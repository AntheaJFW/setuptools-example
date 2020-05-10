# Creating distributable CLI app

Create and activate virtual environment with python3
```bash
python3 -m venv venv
source venv/bin/activate
```

For this example, we're using the following CLI example from PyInquirer example files, [Order Pizza](https://github.com/CITGuru/PyInquirer/blob/master/examples/pizza.py), which will require pyinquirer:
```bash
pip install pyinquirer
```

Installing Setup tools:
```bash
pip install --upgrade setuptools
```

## Creating module to import:
Create a file order like so:
```bash
order_pizza/
    order_pizza/
        __init__.py
        order_pizza.py
    setup.py
```
Where order_pizza.py will have the function OrderPizza to be used to run the cli app, and `__init__.py` will only contain the following:

```bash
from .order_pizza import OrderPizza
```
hence when order_pizza is imported, OrderPizza is in the module namespace.

We can test this by starting python in the second level ie 
```bash
order_pizza/
->   order_pizza/
        __init__.py
        order_pizza.py
    setup.py
```
Starting python repl:
```bash
cd order_pizza
python
```

And trying to import and run the module:
```python
from order_pizza import OrderPizza
OrderPizza()
```

In `setup.py`, we can specify the modules that this module will depend on, by specifying these in `install_requires`: 
```python
from setuptools import setup

setup(name='OrderPizza',
      version='0.1',
      description='OrderPizza',
      url='',
      author='',
      author_email='',
      license='MIT',
      packages=['order_pizza'],
      zip_safe=False,
      install_requires=[
          'pyInquirer',
      ])
```

Check that it works using:
```bash
python setup.py develop
```

Sucess would output a message similar to the following will prompt:
```bash
Finished processing dependencies for OrderPizza==0.1
```

Then you may install the module using
```bash
pip install .
```

Test that it works by changing your terminal directory to elsewhere and running python, ie:
```bash
cd ~
python
```
Then import your new module!:
```python
from order_pizza import OrderPizza
OrderPizza()
```

