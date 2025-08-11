# Documentation of Code

In my experience docstrings and code style are the **best** way to assist reviewers of code -- both your future self and colleagues. Also, this is the documentation that saves yours and others life when it comes to future contribution. As such, this page will reflect on a variety of perhaps surprising ways that code gets documentated. 

Most code documentation is *for developers*, but docstrings in particular are *for users*.

Documenting code has many perspectives, here are a few perspectives that I have appreciated over time.

Key Points (somewhat ordered from most to least important):

## Object Names



1. Function / Class / Variable names should have descriptive names.
   1. Single variable names are notoriously hard to understand bad
   2. Use actions for functions / methods
   3. Longer names can be useful as a form of self documentation, especially when objects are re-used across modules. 
      1. `width` is much less clear than `img_array_width` 
2. Docstrings should be used to the 

## Docstrings

## Commenting code

Documentation via comments should be reserved for instances where the aforementioned code documentation is *insufficient* to understand what some lines are code are doing. Usually, 

```python
def 

```

## Code Style

## Tests?!?!

Tests are another form of documentation. Tests help us crystallize what we 

## Other Tips

1. Functions / Methods should be visible on "one screen", so about 25 lines. Makes much easier to review! And you'll thank yourself! This generally helps with that "do one thing" that people who clearly understand things that way will say.