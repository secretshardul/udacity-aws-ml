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
