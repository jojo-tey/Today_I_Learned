# Design pattern

- [Factory pattern](#Factory-pattern)
  - Fachtory method
  - Abstract factory
- [Builder pattern](#Builder-pattern)
- [Prototype pattern](#Prototype-pattern)
- [Singleton pattern](#Singleton-pattern)
- [Adapter pattern](#Adapter-pattern)
- [Decorator pattern](#Decorator-pattern)
- [Bridge pattern](#Bridge-pattern)
- [Facade Pattern](#Facade-pattern)
- [Flyweight pattern](#Flyweight-pattern)
- [Proxy pattern](#Proxy-pattern)
- [Observer pattern](#Observer-pattern)
- [State pattern](#State-pattern)
- [Strategy pattern](#Strategy-pattern)
- [Microservices pattern](#Microservices-pattern)
  - Retry pattern
  - Circuit Breaker pattern
  - Cache-Aside pattern
  - Throttiling pattern


<br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)


---

## Factory pattern

### Fachtory method

> The factory method centralizes object creation and tracking your objects becomes much easier


1. It inherits forms and creates objects of various fields.

```
py

from django import forms

class PersonForm(forms.Form):
    name = forms.CharField(max_length=100)
    birth_date = forms.DateField(required=False)
```

2. For connecting you to different databases (MySQL, SQLite)

3. For creating the geometrical object that you request (circle, triangle)

4. Parsing various input XML and JSON files and centralizes the client's connection

```
py

import json
import xml.etree.ElementTree as etree


class JSONDataExtractor:

    def __init__(self, filepath):
        self.data = dict()
        with open(filepath, mode='r', encoding='utf-8') as f:
            self.data = json.load(f)

    @property
    def parsed_data(self):
        return self.data


class XMLDataExtractor:

    def __init__(self, filepath):
        self.tree =  etree.parse(filepath)

    @property
    def parsed_data(self):
        return self.tree


def dataextraction_factory(filepath):
    if filepath.endswith('json'):
        extractor = JSONDataExtractor
    elif filepath.endswith('xml'):
        extractor = XMLDataExtractor
    else:
        raise ValueError('Cannot extract data from {}'.format(filepath))
    return extractor(filepath)


def extract_data_from(filepath):
    factory_obj = None
    try:
        factory_obj = dataextraction_factory(filepath)
    except ValueError as e:
        print(e)
    return factory_obj


def main():
    sqlite_factory = extract_data_from('data/person.sq3')
    print()

    json_factory = extract_data_from('data/movies.json')
    json_data = json_factory.parsed_data
    print(f'Found: {len(json_data)} movies')
    for movie in json_data:
        print(f"Title: {movie['title']}")
        year = movie['year']
        if year:
            print(f"Year: {year}")
        director = movie['director']
        if director:
            print(f"Director: {director}")
        genre = movie['genre']
        if genre:
            print(f"Genre: {genre}")
        print()

    xml_factory = extract_data_from('data/person.xml')
    xml_data = xml_factory.parsed_data
    liars = xml_data.findall(f".//person[lastName='Liar']")
    print(f'found: {len(liars)} persons')
    for liar in liars:
        firstname = liar.find('firstName').text
        print(f'first name: {firstname}')
        lastname = liar.find('lastName').text
        print(f'last name: {lastname}')
        [print(f"phone number ({p.attrib['type']}):", p.text) 
              for p in liar.find('phoneNumbers')]
        print()
    print()


if __name__ == '__main__':
    main()
```


### Abstract factory

> A generalized version of the factory method pattern. Create grouped objects. It has advantages such as easy object creation, improved memory usability, and improved performance.


#### Example

- The 'FrogWorld' class is an abstract factory.
- The 'WizardWorld' class is an abstract factory.
- The 'GameEnvironment' class is the main entry point of our game. It accepts the factory as an input and uses it to create the world of the game.

```
# Frog game

class Frog:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return self.name

    def interact_with(self, obstacle):
        act = obstacle.action()
        msg = f'{self} the Frog encounters {obstacle} and {act}!'
        print(msg)

class Bug:
    def __str__(self):
        return 'a bug'

    def action(self):
        return 'eats it'

class FrogWorld:
    def __init__(self, name):
        print(self)
        self.player_name = name

    def __str__(self):
        return '\n\n\t------ Frog World -------'

    def make_character(self):
        return Frog(self.player_name)

    def make_obstacle(self):
        return Bug()


# Wizard game

class Wizard:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return self.name

    def interact_with(self, obstacle):
        act = obstacle.action()
        msg = f'{self} the Wizard battles against {obstacle} and {act}!'
        print(msg)

class Ork:
    def __str__(self):
        return 'an evil ork'

    def action(self):
        return 'kills it'

class WizardWorld:
    def __init__(self, name):
        print(self)
        self.player_name = name

    def __str__(self):
        return '\n\n\t------ Wizard World -------'

    def make_character(self):
        return Wizard(self.player_name)

    def make_obstacle(self):
        return Ork()

# Game environment
class GameEnvironment:
    def __init__(self, factory):
        self.hero = factory.make_character()
        self.obstacle = factory.make_obstacle()

    def play(self):
        self.hero.interact_with(self.obstacle)

def validate_age(name):
    try:
        age = input(f'Welcome {name}. How old are you? ')
        age = int(age)
    except ValueError as err:
        print(f"Age {age} is invalid, please try again...")
        return (False, age)
    return (True, age)

def main():
    name = input("Hello. What's your name? ")
    valid_input = False
    while not valid_input:
        valid_input, age = validate_age(name)
    game = FrogWorld if age < 18 else WizardWorld
    environment = GameEnvironment(game(name))
    environment.play()


if __name__ == '__main__':
    main()
```


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)


## Builder pattern

> If you need to create an object through various steps, use the Builder Pattern.

- Difference between factory pattern and builder pattern
  - In the factory pattern, object creation is a single step, but in the builder pattern, object creation is in multiple steps.
  - The factory pattern creates the object immediately, but the builder pattern explicitly asks the director to return the final object when it needs it

- There are two important factors
  - builder: Creates a complex object (which has to go through various steps)
  - director: The component that controls the building process using a builder instance. (It seems like a role to customize elements that can be customized.)


#### Example

1. It is applicable to situations where various burgers must be prepared in a fast food restaurant and various packages are required

  - In this case, the director is the cashier who gives instructions about what needs to be prepared to the crew, and the builder is the person from the crew that takes care of the specific order.

2. The django-widgy editor contains a page builder that can be used for creating HTML pages with different layouts.

3. Pizza restaurant
  - Code structure
  - two builders: MargaritaBuilder, CreamyBaconBuilder
  - Each builder creates a'Pizza' instance
  - prepare_dough() is just a wrapper to the prepare_dough() method of the Pizza class.
  - The director in this example is the waiter, which accepts a builder as a parameter and executes all the pizza-preparation steps in the right order.

```
py

from enum import Enum
import time

PizzaProgress = Enum('PizzaProgress', 'queued preparation baking ready')
PizzaDough = Enum('PizzaDough', 'thin thick')
PizzaSauce = Enum('PizzaSauce', 'tomato creme_fraiche')
PizzaTopping = Enum('PizzaTopping', 
                    'mozzarella double_mozzarella bacon ham mushrooms red_onion oregano')
STEP_DELAY = 3 # in seconds for the sake of the example


class Pizza:
    def __init__(self, name):
        self.name = name
        self.dough = None
        self.sauce = None
        self.topping = []

    def __str__(self):
        return self.name

    def prepare_dough(self, dough):
        self.dough = dough
        print(f'preparing the {self.dough.name} dough of your {self}...')
        time.sleep(STEP_DELAY)
        print(f'done with the {self.dough.name} dough')

        
class MargaritaBuilder:
    def __init__(self):
        self.pizza = Pizza('margarita')
        self.progress = PizzaProgress.queued
        self.baking_time = 5 # in seconds for the sake of the example

    def prepare_dough(self):
        self.progress = PizzaProgress.preparation
        self.pizza.prepare_dough(PizzaDough.thin)

    def add_sauce(self):
        print('adding the tomato sauce to your margarita...')
        self.pizza.sauce = PizzaSauce.tomato
        time.sleep(STEP_DELAY)
        print('done with the tomato sauce')

    def add_topping(self):
        topping_desc = 'double mozzarella, oregano'
        topping_items = (PizzaTopping.double_mozzarella, PizzaTopping.oregano)
        print(f'adding the topping ({topping_desc}) to your margarita')
        self.pizza.topping.append([t for t in topping_items])
        time.sleep(STEP_DELAY)
        print(f'done with the topping ({topping_desc})')

    def bake(self):
        self.progress = PizzaProgress.baking
        print(f'baking your margarita for {self.baking_time} seconds')
        time.sleep(self.baking_time)
        self.progress = PizzaProgress.ready
        print('your margarita is ready')

        
class CreamyBaconBuilder:
    def __init__(self):
        self.pizza = Pizza('creamy bacon')
        self.progress = PizzaProgress.queued
        self.baking_time = 7 # in seconds for the sake of the example

    def prepare_dough(self):
        self.progress = PizzaProgress.preparation
        self.pizza.prepare_dough(PizzaDough.thick)

    def add_sauce(self):
        print('adding the crème fraîche sauce to your creamy bacon')
        self.pizza.sauce = PizzaSauce.creme_fraiche
        time.sleep(STEP_DELAY)
        print('done with the crème fraîche sauce')

    def add_topping(self):
        topping_desc = 'mozzarella, bacon, ham, mushrooms, red onion, oregano'
        topping_items =  (PizzaTopping.mozzarella,
                          PizzaTopping.bacon,
                          PizzaTopping.ham,
                          PizzaTopping.mushrooms,
                          PizzaTopping.red_onion, 
                          PizzaTopping.oregano)
        print(f'adding the topping ({topping_desc}) to your creamy bacon')
        self.pizza.topping.append([t for t in topping_items])
        time.sleep(STEP_DELAY)
        print(f'done with the topping ({topping_desc})')

    def bake(self):
        self.progress = PizzaProgress.baking
        print(f'baking your creamy bacon for {self.baking_time} seconds')
        time.sleep(self.baking_time)
        self.progress = PizzaProgress.ready
        print('your creamy bacon is ready')

        
class Waiter:
    def __init__(self):
        self.builder = None

    def construct_pizza(self, builder):
        self.builder = builder
        steps = (builder.prepare_dough, 
                 builder.add_sauce, 
                 builder.add_topping, 
                 builder.bake)
        [step() for step in steps]

    @property
    def pizza(self):
        return self.builder.pizza

        
def validate_style(builders):
    try:
        input_msg = 'What pizza would you like, [m]argarita or [c]reamy bacon? '
        pizza_style = input(input_msg)
        builder = builders[pizza_style]()
        valid_input = True
    except KeyError:
        error_msg = 'Sorry, only margarita (key m) and creamy bacon (key c) are available'
        print(error_msg)
        return (False, None)
    return (True, builder)

    
def main():
    builders = dict(m=MargaritaBuilder, c=CreamyBaconBuilder)
    valid_input = False
    while not valid_input:
        valid_input, builder = validate_style(builders)
    print()
    waiter = Waiter()
    waiter.construct_pizza(builder)
    pizza = waiter.pizza
    print()
    print(f'Enjoy your {pizza}!')

    
if __name__ == '__main__':
    main()
```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)



## Prototype pattern

> A pattern of creating a new object by copying an existing object rather than creating a new object as a class

  - In Python, this can be done using the copy.deepcopy() function.
  - Good to use when you need complex object creation logic.

#### Example

1. Used to create multiple websites with the same format but by changing only the name, domain, and creation date.

```
import copy

class Website: 
    def __init__(self, name, domain, description, author, **kwargs): 
        '''Examples of optional attributes (kwargs): 
           category, creation_date, technologies, keywords.
        ''' 
        self.name = name 
        self.domain = domain 
        self.description = description
        self.author = author
        
        for key in kwargs:
            setattr(self, key, kwargs[key])
 
    def __str__(self): 
        summary = [f'Website "{self.name}"\n',] 
        
        infos = vars(self).items()
        ordered_infos = sorted(infos)
        for attr, val in ordered_infos:
            if attr == 'name':
                continue
            summary.append(f'{attr}: {val}\n')
            
        return ''.join(summary) 

        
class Prototype: 
    def __init__(self): 
        self.objects = dict() 
 
    def register(self, identifier, obj): 
        self.objects[identifier] = obj 
 
    def unregister(self, identifier): 
        del self.objects[identifier] 
 
    def clone(self, identifier, **attrs): 
        found = self.objects.get(identifier) 
        if not found: 
            raise ValueError(f'Incorrect object identifier: {identifier}') 
        obj = copy.deepcopy(found) 
        for key in attrs:
            setattr(obj, key, attrs[key])

        return obj
        
def main(): 
    keywords = ('python', 'data', 'apis', 'automation')
    site1 = Website('ContentGardening', 
            domain='contentgardening.com', 
            description='Automation and data-driven apps', 
            author='Kamon Ayeva',
            category='Blog',
            keywords=keywords)
 
    prototype = Prototype() 
    identifier = 'ka-cg-1' 
    prototype.register(identifier, site1)
    
    site2 = prototype.clone(identifier, 
            name='ContentGardeningPlayground',
            domain='play.contentgardening.com', 
            description='Experimentation for techniques featured on the blog', 
            category='Membership site',
            creation_date='2018-08-01') 
 
    for site in (site1, site2): 
        print(site)
    print(f'ID site1 : {id(site1)} != ID site2 : {id(site2)}')
    
if __name__ == '__main__': 
    main()
```


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)


## Singleton Pattern

> Pattern restricting class to have only 1 instance

1. Python 3 nowadays, the recommended technique we will choose is the metaclass technique.
2. Controlling concurrent access to a shared resource. For example, the class managing the connection to a database.
3. The class at the core of the logging system or utility
4. URL fetcher
  - define the SingletonType class, with its special `__call__()` method
```
py

import urllib.parse
import urllib.request


class SingletonType(type):
    _instances = {}
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super(SingletonType, cls).__call__(*args, **kwargs)
        return cls._instances[cls]


class URLFetcher(metaclass=SingletonType):

    def __init__(self):
        self.urls = []
    
    def fetch(self, url):
        req = urllib.request.Request(url)
        with urllib.request.urlopen(req) as response:
            if response.code == 200:
                the_page = response.read()
                print(the_page)
        
                urls = self.urls
                urls.append(url)
                self.urls = urls
            
    def dump_url_registry(self):
        return ', '.join(self.urls)


def main():

    MY_URLS = ['http://www.voidspace.org.uk', 
               'http://google.com', 
               'http://python.org',
               'https://www.python.org/error',
               ]

    print(URLFetcher() is URLFetcher())

    fetcher = URLFetcher()
    for url in MY_URLS:
        try:
            fetcher.fetch(url)
        except Exception as e:
            print(e)
            
    print('-------')
    done_urls = fetcher.dump_url_registry()
    print(f'Done URLs: {done_urls}')
    
if __name__ == '__main__':
    main()
```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)

## Adapter Pattern

> A pattern to connect interfaces when the interface provided by the class to be reused and the interface used by the client are different

- helps us make two incompatible interfaces compatible


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)


## Decorator Pattern

> The decorator pattern is generally used for extending the functionality of an object

  - Data validation
  - Caching
  - Logging
  - Monitoring
  - Debugging
  - Business rules
  - Encryption

#### Example

1. Registering a function as an event subscriber

2. Protecting a method with a specific permission

3. Implementing the adapter pattern

4. Controlling HTTP compression and caching

5. Caching and memoization

```
py

import functools 
 
def memoize(fn): 
    cache = dict() 
 
    @functools.wraps(fn) 
    def memoizer(*args): 
        if args not in cache: 
            cache[args] = fn(*args) 
        return cache[args] 
 
    return memoizer
    
@memoize 
def number_sum(n): 
    '''Returns the sum of the first n numbers''' 
    assert(n >= 0), 'n must be >= 0' 
    if n == 0:
        return 0
    else:
        return n + number_sum(n-1)
 
@memoize 
def fibonacci(n): 
    '''Returns the suite of Fibonacci numbers''' 
    assert(n >= 0), 'n must be >= 0'
    if n in (0, 1):
        return n
    else:
        return fibonacci(n-1) + fibonacci(n-2)    
        
def main():
    from timeit import Timer

    to_execute = [
        (number_sum, 
         Timer('number_sum(300)', 'from __main__ import number_sum')),
        (fibonacci, 
         Timer('fibonacci(100)', 'from __main__ import fibonacci'))    
    ]
    
    for item in to_execute:
        fn = item[0]
        print(f'Function "{fn.__name__}": {fn.__doc__}')
        t = item[1]
        print(f'Time: {t.timeit()}')
        print()

if __name__ == '__main__': 
    main()
```


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)

## Bridge pattern

> When it is necessary to implement various speacilzed classes, the implementation part is separated through abstraction.


- An abstraction that applies to all the classes
- A separate interface for the different objects involved

#### Example

- Resource Content abstraction, called ResourceContent. (maintain a reference to the object which represents the Implementor)
- Define the interface for implementation classes that help fetch content, that is, the ResourceContentFetcher class. This concept is called the Implementor.
- For using bridge pattern, you can extract content from different sources and integrate the results in the same data manipulation system or user interface.

```
py

import abc
import urllib.parse
import urllib.request


class ResourceContent:
    """
    Define the abstraction's interface.
    Maintain a reference to an object which represents the Implementor.
    """

    def __init__(self, imp):
        self._imp = imp

    def show_content(self, path):
        self._imp.fetch(path)


class ResourceContentFetcher(metaclass=abc.ABCMeta):
    """
    Define the interface (Implementor) for implementation classes that help fetch content.
    """
    
    @abc.abstractmethod
    def fetch(path):
        pass
        

class URLFetcher(ResourceContentFetcher):
    """
    Implement the Implementor interface and define its concrete
    implementation.
    """
    
    def fetch(self, path):
        # path is an URL
        req = urllib.request.Request(path)
        with urllib.request.urlopen(req) as response:
            if response.code == 200:
                the_page = response.read()
                print(the_page)
                        
                
class LocalFileFetcher(ResourceContentFetcher):
    """
    Implement the Implementor interface and define its concrete
    implementation.
    """

    def fetch(self, path):
        # path is the filepath to a text file
        with open(path) as f:
            print(f.read())
        
       
def main():
    url_fetcher = URLFetcher()
    iface = ResourceContent(url_fetcher)
    iface.show_content('http://python.org')

    print('===================')
    
    localfs_fetcher = LocalFileFetcher()
    iface = ResourceContent(localfs_fetcher)
    iface.show_content('file.txt')

    
if __name__ == "__main__":
    main()
```

## Facade Pattern


> Complex classes and instructions can be executed through a single function.

- The facade design pattern helps us to hide the internal complexity of our systems and expose only what is necessary to the client through a simplified interface.
- By introducing facade, the client code can use a system by simply calling a single method/function.

#### Example

- It does not expose the complexity to the client because it encapsulates the whole procedure when the CPU boots.
- We need to subclass ABCMeta using the metaclass keyword.
- We use the @abstractmethod decorator for stating which methods should be implemented (mandatory) by all subclasses of server.

```
py

from enum import Enum 
from abc import ABCMeta, abstractmethod 
 
State = Enum('State', 'new running sleeping restart zombie') 
 
class User: 
    pass 
 
class Process: 
    pass 
 
class File: 
    pass 
 
class Server(metaclass=ABCMeta): 
    @abstractmethod 
    def __init__(self): 
        pass 
 
    def __str__(self): 
        return self.name 
 
    @abstractmethod 
    def boot(self): 
        pass 
 
    @abstractmethod  
    def kill(self, restart=True): 
        pass 
 
class FileServer(Server): 
    def __init__(self): 
        '''actions required for initializing the file server''' 
        self.name = 'FileServer' 
        self.state = State.new 
 
    def boot(self): 
        print(f'booting the {self}') 
        '''actions required for booting the file server''' 
        self.state = State.running 
 
    def kill(self, restart=True): 
        print(f'Killing {self}') 
        '''actions required for killing the file server''' 
        self.state = State.restart if restart else State.zombie 
 
    def create_file(self, user, name, permissions): 
        '''check validity of permissions, user rights, etc.''' 
        print(f"trying to create the file '{name}' for user '{user}' with permissions {permissions}") 
 
class ProcessServer(Server): 
    def __init__(self): 
        '''actions required for initializing the process server''' 
        self.name = 'ProcessServer' 
        self.state = State.new 
 
    def boot(self): 
        print(f'booting the {self}') 
        '''actions required for booting the process server''' 
        self.state = State.running 
 
    def kill(self, restart=True): 
        print(f'Killing {self}') 
        '''actions required for killing the process server''' 
        self.state = State.restart if restart else State.zombie 
 
    def create_process(self, user, name): 
        '''check user rights, generate PID, etc.''' 
        print(f"trying to create the process '{name}' for user '{user}'") 
 
class WindowServer: 
    pass 
 
class NetworkServer: 
    pass 
 
class OperatingSystem: 
    '''The Facade''' 
    def __init__(self): 
        self.fs = FileServer() 
        self.ps = ProcessServer() 
 
    def start(self): 
        [i.boot() for i in (self.fs, self.ps)] 
 
    def create_file(self, user, name, permissions): 
        return self.fs.create_file(user, name, permissions) 
 
    def create_process(self, user, name): 
        return self.ps.create_process(user, name) 
 
def main(): 
    os = OperatingSystem() 
    os.start()  
    os.create_file('foo', 'hello', '-rw-r-r') 
    os.create_process('bar', 'ls /tmp') 
 
if __name__ == '__main__': 
    main()
```


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)


## Flyweight pattern

> It is a pattern that saves memory by managing common properties of multiple objects. In other words, it is a pattern used when you need to create a large number of objects, and a pattern that should be used when memory is consumed too much to store that many objects.

- To minimize memory usage and improve performance by introducing data sharing between similar objects
- Flyweight is an OOP-specific optimization design pattern that focuses on sharing object data.


#### Example

- In the game, all users are in the same team, there is a common action (jump, duck, etc.) and can be used at this time.
- Caching
- The Exaile music player uses flyweight to reuse objects (in this case, music tracks) that are identified by the same URL.
- Choosing car model

<br>

* Notice that pool is a class attribute (a variable shared by all instances).
* Using the __new__() special method, which is called before __init__(), we are converting the Car class to a metaclass that supports self-references. This means that cls references the Car class.

```
py

import random 
from enum import Enum 
 
CarType = Enum('CarType', 'subcompact compact suv') 
 
class Car: 
    pool = dict() 
 
    def __new__(cls, car_type): 
        obj = cls.pool.get(car_type, None) 
        if not obj: 
            obj = object.__new__(cls) 
            cls.pool[car_type] = obj 
            obj.car_type = car_type 
        return obj 
 
    def render(self, color, x, y):
        type = self.car_type
        msg = f'render a car of type {type} and color {color} at ({x}, {y})'
        print(msg)
 
def main(): 
    rnd = random.Random() 
    #age_min, age_max = 1, 30    # in years 
    colors = 'white black silver gray red blue brown beige yellow green'.split()
    min_point, max_point = 0, 100 
    car_counter = 0 
 
    for _ in range(10): 
        c1 = Car(CarType.subcompact) 
        c1.render(random.choice(colors), 
                  rnd.randint(min_point, max_point), 
                  rnd.randint(min_point, max_point)) 
        car_counter += 1 
 
    for _ in range(3): 
        c2 = Car(CarType.compact) 
        c2.render(random.choice(colors), 
                  rnd.randint(min_point, max_point), 
                  rnd.randint(min_point, max_point)) 
        car_counter += 1 
 
    for _ in range(5): 
        c3 = Car(CarType.suv) 
        c3.render(random.choice(colors), 
                  rnd.randint(min_point, max_point), 
                  rnd.randint(min_point, max_point)) 
        car_counter += 1 
 
    print(f'cars rendered: {car_counter}') 
    print(f'cars actually created: {len(Car.pool)}') 
 
    c4 = Car(CarType.subcompact) 
    c5 = Car(CarType.subcompact) 
    c6 = Car(CarType.suv) 
    print(f'{id(c4)} == {id(c5)}? {id(c4) == id(c5)}') 
    print(f'{id(c5)} == {id(c6)}? {id(c5) == id(c6)}') 

    
if __name__ == '__main__': 
    main()
```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)

## Proxy pattern

> Control access to sensitive information

#### Example

- Introducing lazy initialization using a virtual proxy to create the objects only at the moment they are actually required can give us significant performance improvements(make it execute at the end).
- When checking whether a user has a specific authority

```
py

class SensitiveInfo: 
    def __init__(self): 
        self.users = ['nick', 'tom', 'ben', 'mike'] 
 
    def read(self): 
        nb = len(self.users)
        print(f"There are {nb} users: {' '.join(self.users)}") 
 
    def add(self, user): 
        self.users.append(user) 
        print(f'Added user {user}') 
 
class Info:  
    '''protection proxy to SensitiveInfo''' 
 
    def __init__(self): 
        self.protected = SensitiveInfo() 
        self.secret = '0xdeadbeef' 
 
    def read(self): 
        self.protected.read() 
 
    def add(self, user): 
        sec = input('what is the secret? ') 
        self.protected.add(user) if sec == self.secret else print("That's wrong!") 
 
def main(): 
    info = Info() 
 
    while True: 
        print('1. read list |==| 2. add user |==| 3. quit') 
        key = input('choose option: ') 
        if key == '1': 
            info.read() 
        elif key == '2': 
            name = input('choose username: ') 
            info.add(name) 
        elif key == '3': 
            exit() 
        else: 
            print(f'unknown option: {key}') 
 
if __name__ == '__main__': 
    main()
```
<br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)


## Observer pattern

> The key point in this case is that multiple listeners (observers) can be attached to a single event (publisher).

#### Example

- RabbitMQ library, Several messaging protocols are supported, such as HTTP and AMQP. RabbitMQ can be used in a Python application to implement a publish-subscribe pattern

- news feed(RSS)

- Event-driven systems
<br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)


## State pattern

> patterns with two states and transitions. In an event-driven system, the transition from one state to another triggers an event/message.


#### Example

- Reject our selection because the product we requested is out of stock
- Reject our selection because the amount of money we inserted was not sufficient
- Deliver the product and give no change because we inserted the exact amount
- Deliver the product and return the change


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)


## Strategy pattern

> A pattern that makes various algorithms and selects the most suitable algorithm according to the input.


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)



## Microservices pattern

1. Retry pattern
  - Pattern to retry when an error occurs

2. Circuit Breaker pattern
  - When failures reach a specific threshold, the circuit is blocked to prevent propagation of failure

3. Cache-Aside pattern
  - Cache frequently used information

4. Throttling pattern
  - throttling is based on limiting the number of requests a user can send to a given web service in a given amount of time, in order to protect the resources of the service from being overused by some users.

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Design-pattern)

</br>


_designpattern.end_






</br>