# Python tricks used

Using numpy or data structures is more efficient than writing own loops.

1. Find common elements between 2 lists

   1. Using **numpy intersection**

   ```py
   np.intersect1d(recent_books, coding_books)
   ```

   2. Using **set intersection**

   ```py
   set(recent_books).intersection(set(coding_books)) #convert lists to sets
   ```

2. Select elements from array which meet certain condition

   ```py
   gift_array = np.array(gift_costs) #convert list to array
   gift_array = gift_array[gift_array < 25]
   ```

3. Find sum of elements in array

```py
sum = np.sum(gift_array)
```

4. Magic methods: They change default behavior of python operations. They begin and end with '**'. Eg. `**init**`,`**add\*\*`,`**repr**` etc.

```py
class Gaussian():
   def __add__(self, other):
      result = Gaussian()
      result.mean = self.mean + other.mean
      result.stdev = math.sqrt(self.stdev**2 + other.stdev**2)

      return result

gaussian_one = Gaussian(25, 3)
gaussian_two = Gaussian(30, 4)
gaussian_sum = gaussian_one + gaussian_two # Using __add__ magic method

```

# Creating custom packages

[gaussian_project](/gaussian_project) contains custom package. Package code is in /distributions. There are 2 special files, `setup.py` and `/distributions/__init__.py`.

1. Update import statements.

In Gaussiandistribution.py

```py
from .Generaldistribution import Distribution
```

2. Create `distributions/__init__.py`. It tells which modules the package must import.

```py
from .Gaussiandistribution import Gaussian
```

3. Create `setup.py` and paste template

```py
import setuptools

setuptools.setup(
    name="distributions",
    version="0.1",
    description="Gaussian distribution",
    packages=setuptools.find_packages(),
)
```

4. Create venv and install this package

```sh
python -m venv venv
source venv/bin/activate
pip install gaussian_project/.
python gaussian.py
```
