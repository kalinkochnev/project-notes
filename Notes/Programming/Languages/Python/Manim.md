u# Linux install
https://docs.manim.community/en/stable/installation/linux.html
1. Create [[Notes/Programming/Languages/Python/General#Create virtual environment]]
```
sudo apt update
sudo apt install build-essential python3-dev libcairo2-dev libpango1.0-dev ffmpeg
```


# Command line arguments
`-ql` render in low quality
`-p` play once finished rendering
`-s` outputs image preview of the ending state of the scene (can be combined w/ quality settings) `-s -ql`

# Sections
https://docs.manim.community/en/stable/tutorials/output_and_config.html#sections



- Can `add()` and `remove()` objects from Scene
- Order of args to `add()` determine the order that objects are displayed
```python
from manim import *

class CreatingMobjects(Scene):
    def construct(self):
        circle = Circle()
        self.add(circle)
        self.wait(1)
        self.remove(circle)
        self.wait(1)
```

- Mobjects are placed at origin by default
- Can position with `move_to()` (absolute units), `next_to()` (relative units), `align_to()` (uses bounding box border)
```python
from manim import *

class MobjectPlacement(Scene):
    def construct(self):
        circle = Circle()
        square = Square()
        triangle = Triangle()

        # place the circle two units left from the origin
        circle.move_to(LEFT * 2)
        # place the square to the left of the circle
        square.next_to(circle, LEFT)
        # align the left border of the triangle to the left border of the circle
        triangle.align_to(circle, LEFT)

        self.add(circle, square, triangle)
        self.wait(1)
```
![[Pasted image 20230411195437.png]]

- Styles can be applied with `set_fill()` and `set_stroke()` (both have keyword arg opacity parameter)

# Animations
- Are procedure to interpolate between 2 `Mobjects`
- Any method that changes a `Mobject` property can be converted to an animation with `animate()`
- `play(run_time=N)` adjusts runtime of animation
```python
from manim import *

class AnimateExample(Scene):
    def construct(self):
        square = Square().set_fill(RED, opacity=1.0)
        self.add(square)

        # animate the change of color
        self.play(square.animate.set_fill(WHITE))
        self.wait(1)

        # animate the change of position and the rotation at the same time
        self.play(square.animate.shift(UP).rotate(PI / 3))
        self.wait(1)
```

## Custom animations
https://docs.manim.community/en/stable/tutorials/building_blocks.html#creating-a-custom-animation

### Example
```python
from manim import *

class Count(Animation):
    def __init__(self, number: DecimalNumber, start: float, end: float, **kwargs) -> None:
        # Pass number as the mobject of the animation
        super().__init__(number,  **kwargs)
        # Set start and end
        self.start = start
        self.end = end

    def interpolate_mobject(self, alpha: float) -> None:
        # Set value of DecimalNumber according to alpha
        value = self.start + (alpha * (self.end - self.start))
        self.mobject.set_value(value)


class CountingScene(Scene):
    def construct(self):
        # Create Decimal Number and add it to scene
        number = DecimalNumber().set_color(WHITE).scale(5)
        # Add an updater to keep the DecimalNumber centered as its value changes
        number.add_updater(lambda number: number.move_to(ORIGIN))

        self.add(number)

        self.wait()

        # Play the Count Animation to count from 0 to 100 in 4 seconds
        self.play(Count(number, 0, 100), run_time=4, rate_func=linear)

        self.wait()
```

# Mobjects
## Coordinates within `Mobject`
![[Pasted image 20230411200158.png]]


# Scenes
- Mobjects must be added to `Scene` to be played
- All code for the video must be in a `construct()`


# Text and Math
- Can add latex with `Tex(r"\Latex"` or `MathTex(r"")`
https://docs.manim.community/en/stable/guides/using_text.html