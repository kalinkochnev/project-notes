# Check that error is thrown
https://stackoverflow.com/a/56569533/10521417
```python
with pytest.raises(ValueError, match="error message"):
	raise ValueError("error message")
```