# Code Documentation

In my experience docstrings and code style are the **best** way to assist reviewers of code -- both your future self and colleagues. Also, this is the documentation that saves yours and others life when it comes to future contribution. As such, this page will reflect on a variety of perhaps surprising ways that code gets documentated.

Most code documentation is *for developers*, but docstrings in particular are *for users*.

However, my biggest caution is that code documentation can often be ignored and frequently goes out of date. Try to be mindful of this and also don't fully rely on docstrings to be fully correct. Yet, if you find something amiss in a docstrings, projects usually warmly welcome even "small" (i.e. typo) contributions to fix docstrings!

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

These are especially helpful for collaboration with developers *and* are the main way to communicate to users. IDEs can richly show information if both docstrings and the IDE is set up correctly. Docstrings can be extremely powerful ways to document API, and docs tooling makes it very easy to add this to your website.

```python
def 

```

## Commenting code

Documentation of functionality via comments should be reserved for instances where the aforementioned code documentation is *insufficient* to understand what some lines are code are doing. Generally this explains as much *why* the implementation exists as it does *what* the implementation is.

Other uses of comments include linking to references, such as external documentation, PRs, or explanations of bug/fixes. 

`# TODO` can be used if you need to bookmark anything and is universal enough to be highlighted in some IDEs.

## Typing

I am not here to endorse Typing as the "correct" way to write Python (indeed, I'm hesistant with some perspectives towards typing). BUT, I am here to show you how (minimally) typing your code greatly helps. Typing can also show up in IDEs, which helps users and developers work with your code.

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

## Tests?!?!

Tests are another form of documentation. Tests help us crystallize for both ourselves and for collaborators the purpose of our code. At least for unit tests, they can also form a sort of documentation. Just some encouragement to take the time to write tests, they are as important as making functions that (you think) work.

```python
def test_threshold_otsu_with_minimum():


```

## Code Style

Following a consistent code style can greatly help readability and understanding of a codebase. Sometimes, code style can become a mess in projects, and it also becomes harder to contribute to that project because there is uncertainty on even how to start writing code. If a project has a fairly regular codestyle, don't be afraid to contribute because these projects are (usually) very helpful at providing suggestions to adopt code to meet any standards that might exist. This particularly is better is the enemy of the good.

## Other Tips

1. Functions / Methods should be visible on "one screen", so about 25 lines. Makes much easier to review! And you'll thank yourself! This generally helps with that "do one thing" that people who clearly understand things that way will say.
2. Use `_object_name` to imply that the object is private and should not be relied on by users. This also can have a lower expectation for documentation, BUT tricky or frequently used private objects should still be documented :)
