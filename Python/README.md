# PDM "no module" error

Try add `setuptools`

```sh
pdm add setuptools
```

# Matplotlib Small Scatter Plot Marker Size Results in Circles

Turn off edge coloring by setting `edgecolor="none"`

```python
import matplotlib.pyplot as plt

plt.scatter(x, y, s=1, edgecolor="none")
```

- **Reference** : [Matplotlib github](https://github.com/matplotlib/matplotlib/issues/25410/)

