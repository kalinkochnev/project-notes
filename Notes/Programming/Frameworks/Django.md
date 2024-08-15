# Computed fields
https://stackoverflow.com/questions/30586994/django-model-save-computed-value-in-a-model-field
```python
class TestModel(models.Model):
    x = models.CharField(max_length=16)
    z = models.CharField(max_length=16)
    computed = models.CharField(max_length=32, editable=False)

    def save(self, *args, **kwargs):
        self.computed = self.x + self.y
        super(TestModel, self).save(*args, **kwargs
```