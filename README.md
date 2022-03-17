# tradewell

Repository containing dark arts.

# Pinescript Basics

## Boilerplate
files have the version annotation at the top:

`//@version=4`

then have a call to strategy or study.

Studies have to call a function to output (`plot` etc)
Strategies have to call a `strategy.*` function 

## Study vs Strategy

Studies:
- can plot
- contain calculations
- can't be used in back-testing
- do not contain `strategy.*` calls.
- can create and use `alertcondition`

Strategies:
- same as studies
- can be used for backtesting
- need to contain calls for buy/sell orders
- You can create an `alertcondition` but can't use it.

## Spacing + Indenting

Multi-line statements are made by having the subsequent lines having any number of spaces that are not a multiple of 4.

```python
a = 1
  + 1
```

Functions require indentation of 4 spaces similar to python

```python
my_function() => 
    a = 1 + 1
    a

```

## Comments 
Pine supports single-line comments only.
Comments are denoted by `//`. They can be placed most anywhere apart from on multi-line statements.

# Identifiers
Identifiers the name referencing a function or variable.

```python
a = 1
b = 2
c = b
```

Can contain uppercase or lowercase, numbers and underscore. Cannot start with number. 

Can optionally declare the type

```python
int my_int = 1
```

# Variable Types
Pine has the following identifier types:
`int, float, bool, string, line, label, color`

Identifiers can be assigned these:
- Integer: `a = 1`
- Float: `a = 3.2` or `a = 3.2e10`
- Strings: `a = "hello"` or `a = 'hello'` or `a = 'I\'m a string'`
- Bool `a = true`
- Colors `a = #ff0000` or `a = color.red`
- Lines and Labels
- Plots and hline (horizontal line)
- `na` which is null/none. If assigning `na` explicitly, an identifier needs a type (`color my_color = na`) 
- Tuples: `[a,b] = [1,2]`

## Default arguments in functions
Functions will often have defaults that can be overridden.

`plot(close, trackprice=false)`

### Editor Features
Command click will give you info on function params. Can find colors etc there.
The "Data Window" will show you information on variables in the script.

### plot and fill
Can plot and fill between w/ fill function.
Plot output can be assigned so that it can be used in other functions like fill.

```python
open_id = plot(open, color=color.red, title="open")
close_id = plot(close, color=color.red, title="close")
fill(open_id, close_id, color=color.green, title="fill")
```

### hline
Puts a horizontal line on the chart

```python
h1 = hline(1000)
h2 = hline(1000)
fill(h1, h2, color=color.red, trasp=50)
```

### lines and labels (pine v4+)
`line.new()` see pine editor for detail.

