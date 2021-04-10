# revolution

An assortment of spinners to use while your Python programs run.

## Installation

In order to install `revolution`, run the following in your command line:

`pip install revolution`

`revolution` doesn't have any dependencies.

## Usage

In order to use `revolution` in your code, importing it is as simple as:

```py
from revolution import Revolution
```

### Parameters for Revolution()

The parameters for instantiating a Revolution object are as follows:

```
Revolution(func=None, desc='', total=None, style='', safe=True, interval=None)
```

#### func

The `func` parameter should be left blank unless you initialize a Revolution object with a range object or a list.

#### desc

The `desc` parameter accepts a string object that will be displayed alongside the visual spinner. 

#### total

The `total` parameter accepts an integer value that will be used as the total number of expected iterations.

#### style

The `style` parameter accepts a string object that will be used to specify the spinner style. If `style` is None or if it doesn't exist, the classic style will be used.

#### safe

The `safe` parameter accepts a bool value that will use a spinner style that is safe for terminals on Windows machines.

#### interval

The `interval` paremeter accepts a float value indicating how often the spinner should refresh.

### Function decorator

`revolution` can be used as a **function decorator**:

```py
from revolution import Revolution

@Revolution
def do_something():
    for _ in range(10):
        pass

do_something()
```

You can also provide it a description while you wait for your task to finish:

```py
from revolution import Revolution

@Revolution(desc='Just passing time...')
def do_something():
    for _ in range(10):
        pass

do_something()
```

### with statement

Another possible way to implement `revolution` is through the use of a **with** statement:

```py
from revolution import Revolution

with Revolution(desc='Running through numbers') as revolution:
    for _ in range(100):
        revolution.update(1) 
```

You can also include a visual counter by including a total:

```py
from revolution import Revolution

with Revolution(desc='Counting up to 100', total=100) as revolution:
    for _ in range(100):
        revolution.update(1)
```

### for loop

If you give a Revolution object a **range object** or a **list**, you can then iterate over it:

```py
from revolution import Revolution

total = 0
for i in Revolution(range(100)):
    total += i

print(total)
```

### General

Finally, you can use `revolution` by manually controlling when to stop it:

```py
from revolution import Revolution

revolution = Revolution(desc='Doing things...')
start_long_task()
revolution.stop()
```

## Styles

There are multiple built-in spinner styles that you can take advantage of. *However*, only the classic spinner will be used on **Windows machines** unless you set `safe=False` when you initialize a Revolution object.

### classic

```
Revolution(style='classic')
```

* Windows-friendly
* If a Revolution object doesn't contain a specified style, this is the style that it will default to

### dots

```
Revolution(style='dots')
```

* Windows-friendly

### equal

```
Revolution(style='equal')
```

* Windows-friendly

### braille

```
Revolution(style='braille')
```

### braille_long

```
Revolution(style='braille_long')
```

### braille_crawl

```
Revolution(style='braille_crawl')
```

### braille_bounce

```
Revolution(style='braille_bounce')
```

### arc

```
Revolution(style='arc')
```

### clear_quadrants

```
Revolution(style='clear_quadrants')
```

