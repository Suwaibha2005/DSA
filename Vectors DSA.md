# DSA

## Insertion & Deletion using STL(standard template library) Vectors

### Introduction to Vectors

1. **Why Vectors over Static Array** 

| Feature | Static Array | Vector (STL) |
| --- | --- | --- |
| Size | Fixed at compile-time | Dynamic (can grow/shrink) |
| Memory Allocation | Stack | Heap (resizable) |
| Built-in Functions | None | Yes (push_back, insert…) |
| Safety | No bounds checking | .at( ) checks bounds |
| Flexibility | Low | High |

Vector has all the properties of array with flexibility.

1. **Syntax for Declaration.**

```cpp
vector <datatype> Vector_Name (Size_of_vector);
```

```cpp
vector <int> v(4); //Declares a vector of size 4.
```

1. Syntax for Initialization.

```cpp
vector <datatype> Vector_Name (size,value);
```

```cpp
vector <int> v(4,2);
```

OR

```cpp
#include <vector>
using namespace std;

vector<int> v1;               // Empty vector of integers
vector<int> v2(5);            // Vector of size 5, default initialized
vector<int> v3(5, 100);       // Vector of size 5, all elements = 100
vector<int> v4 = {1, 2, 3};   // Initialization using list
```

Initialization using for 

```cpp
#include <vector>
using namespace std;

int n;
cin>>n; //Takes input from the user which is not allowed in arrays

vector<int>v(n)
for(i=0;i<n;i++)
cin>>v[i];

```

### How to insert value in vector

Declaration:

```cpp
vector<int> a;
```

Insertion using push_back( )

```cpp
a.push_back(4);  // Inserts 4
a.push_back(8);  // Inserts 8
a.push_back(5);  // Inserts 5
a.push_back(2);  // Inserts 2
```

Final Vector

```cpp
a = [4, 8, 5, 2]
```

**Dynamic Resizing in Vector**

- Vectors use dynamic memory (allocated in the heap).
- When current memory is full, inserting a new element:
1. Doubles the capacity.    
2. Copies existing elements to the new memory.
3. Inserts the new element at the next available spot.

**Example:**

```cpp
a.push_back(7);
```

```cpp
a = [4, 8, 5, 2, 7, _, _, _] // _ = unused slots
```

## Why Double the Size?

- To reduce the number of memory reallocations, we double the size when full.
- This ensures that resizing doesn’t happen too often.

## Time Complexity

- push_back() usually takes constant time: O(1).
- Sometimes it takes longer when the vector resizes, but that happens rarely.

## How to Remove Values from Vector

1. v.pop_back() - Removes last element (Time: O(1))

```cpp
vector<int> v = {5, 3, 4, 5};
v.pop_back();  // removes 5
```

Now: v={5,3,4}

1. v.erase(position) - Removes element at a specific index

```cpp
vector<int> v = {6, 7, 8, 9, 10};  // indexes: 0 1 2 3  4
v.erase(v.begin() + 2);           // removes 8 at index 2
```

1. v.clear( ) - Removes all values

```cpp
vector<int> v = {5, 3, 4, 5};
v.clear
```

## Size vs Capacity

```cpp
vector<int> v;
v.push_back(1);       // Size = 1, Capacity = 1
v.push_back(2);       // Size = 2, Capacity = 2
v.push_back(10);      // Size = 3, Capacity = 4

```

| Operation | Time Complexity |  |
| --- | --- | --- |
| push_back() | O(1) (amortized) | 
Doubles capacity if needed |
| pop_back() | O(1) | Removes last element |
| erase(pos) | 
O(n) | Shifts elements after removed index |

## Accessing Elements

```cpp
vector<int> v = {1, 2, 3, 4};
```

1. v.front()

```cpp
cout << v.front();  // Output: 1
```

1. v.back()

```cpp
cout << v.back();   // Output: 4
```

1. v.empty()

```cpp
cout << v.empty();  // Output: 0 (false, since it's not empty)
```

1. v.at(index)

```cpp
cout << v.at(2);    // Output: 3
```

## Iterators in a Vector

- v.begin() → Points to the first element.
- v.end() → Points just after the last element.

```cpp
vector<int> v = {4, 6, 8, 10};

// Using iterator
for (auto it = v.begin(); it != v.end(); ++it) {
    cout << *it << " ";
}
```

Output: 4 6 8 10

Using for loop

```cpp
for (int i = 0; i < v.size(); i++) {
    cout << v[i] << " ";
}
```

Output: 4 6 8 10

## Sorting Using Vectors

1. Sorting in Ascending Order

```cpp
sort(v.begin(), v.end());
```

```cpp
vector<int> v = {2, 3, 1, 7, 4};
sort(v.begin(), v.end());
```

1. Sorting in Descending Order

```cpp
sort(v.begin(), v.end(), greater<int>());
```

```cpp
vector<int> v = {2, 3, 1, 7, 4};
sort(v.begin(), v.end(), greater<int>());
```

## Searching Using Vectors

1. Using find()
- Searches for a value and returns an iterator to it, or v.end() if not found.

```cpp
#include <algorithm>
vector<int> v = {10, 20, 30, 40};
auto it = find(v.begin(), v.end(), 30);
if (it != v.end())  
     cout << "Found at index: " << it - v.begin();
else cout << "Not found";
```

1. Using binary_search() (requires sorted vector)

```cpp
#include <algorithm>
vector<int> v = {10, 20, 30, 40};
sort(v.begin(),v.end());
if (binary_search(v.begin(),v.end(),20) 
     cout << "Element found";
else 
     cout << "Not found";
```

1. max_element() and min_element()

Finds the maximum/minimum element in a vector.

```cpp
vector<int> v = {4, 1, 9, 7};
int maxVal = *max_element(v.begin(), v.end());  // Output: 9
int minVal = *min_element(v.begin(), v.end());  // Output: 1
```

1. count() – Count Occurrences of an Element

```cpp
int c = count(v.begin(), v.end(), value);
```

example:

```cpp
vector<int> v = {2, 3, 2, 4, 2};
int c = count(v.begin(), v.end(), 2);  // Output: 3
```