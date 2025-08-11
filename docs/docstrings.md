# Documentation of Code

In my experience docstrings and code style are the **best** way to assist reviewers of code -- both your future self and colleagues. Also, this is the documentation that saves yours and others life when it comes to future contribution. As such, this page will reflect on a variety of perhaps surprising ways that code gets documentated.

Most code documentation is *for developers*, but docstrings in particular are *for users*.

Documenting code has many perspectives, here are a few perspectives that I have appreciated over time.

```{tip}
Sections have an opinionated order from most to least important.
```

## Suggested Reading



## Object Names

This is where documentation starts and is why its deserving of its own section. If objects are named poorly it becomes a real challenge to follow code.

Object names should bias towards descriptive rather than short. Single variables names are notoriously hard to understand (except in some cases like norms in list comprehension). Use "active" naming or verbs for functions / methods.

Longer names can be an especially useful form of self documentation, especially when objects are re-used across a codebase. 

1. `img_array_width` not `width`
2. `calculate_max_of_array()` not `do_math()` (see ![Typing] though)

## Docstrings

These are especially helpful for collaboration with developers *and* are the main way to communicate to users. IDEs can richly show information if both docstrings and the IDE is set up correctly. Docstrings can be extremely powerful ways to document API, and docs tooling makes it very easy to 

```python
def 

```

## Commenting code

Documentation of functionality via comments should be reserved for instances where the aforementioned code documentation is *insufficient* to understand what some lines are code are doing. Generally this explains as much *why* the implementation exists as it does *what* the implementation is.

Other uses of comments include linking to references, such as external documentation, PRs, or explanations of 

## Typing

I'm not here to endorse Typing as the "correct" way to write Python. BUT, I am here to show you how (minimally) typing your code greatly helps. Typing can also show up in IDEs, which helps users and developers work with your code.

```python
def threshold_otsu_minimum(img, min_value = None):
    """Get threshold value of an image

    Return the threshold value of an image. If the value determined by
    Otsu's algorithm is smaller than a minimum_value, then return the minimum value. 
    This strategy prevents thresholding below a specified value,
    which is useful when an image may be all background and have no signal to threshold.
    """
    threshold = filters.threshold_otsu(img)
    if min_value is not None and min_value > threshold:
        threshold = min_value
    return threshold


def threshold_otsu_minimum(
    img: np.ndarray,
    min_value: int | float | None = None
) -> int | float:
    """Get Otsu's threshold or a minimum of an image

    Parameters
    ----------
    img : np.ndarray
        Image-like array to threshold
    min_value : Optional
        Minimum return value for the threshold

    Returns
    -------
    threshold : int | float
        Threshold value
    ... 
```

## Code Style

Following a consistent code style can greatly help readability and understanding 

## Tests?!?!

Tests are another form of documentation. Tests help us crystallize what we 

## Other Tips

1. Functions / Methods should be visible on "one screen", so about 25 lines. Makes much easier to review! And you'll thank yourself! This generally helps with that "do one thing" that people who clearly understand things that way will say.