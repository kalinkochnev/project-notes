# Self
## Classmethods
Need to instantiate with `cls()`. Working example:
```python
from typing import Self

class Shape:
    @classmethod
    def from_config(cls, config: dict[str, float]) -> Self:
        return cls(config["scale"])
```