# OrderedList < T > : IList < T >
A thread safe C# generic ordered list

Uses the Binary Search algorithm to add and find values within the list.

The list can either have distinct values or permit duplicates.

## Constructors
# public OrderedList(Func<T, T, int> comparer = null, bool permitDuplicates = true, bool replace = true)

comparer - If null and T is IComparable, will use T.Comparer() as the comparer

permitDuplicates - The list can contain duplicate items.

replace - If permitDuplicates is false, and replace true, new items with the same compared value of 0, will be replaced.

# public OrderedList(IEnumerable<T> range, Func<T, T, int> comparer, bool permitDuplicates = true, bool replace = true, bool rangeIsAlreadySorted = false)

range - An item enumerable to start the ordered list with

comparer - If null and T is IComparable, will use T.Comparer() as the comparer

permitDuplicates - The list can contain duplicate items.

replace - If permitDuplicates is false, and replace true, new items with the same compared value of 0, will be replaced.

rangeIsAlreadySorted - if true, start the internal list with the range, else add each one individually


## Properties
# public Func<T, T, int> Comparer { get; set; }
The comparer that OrderedList uses to sort the list.

# public bool IsReadOnly
false.

# public bool IsSynchronized
false.

## Methods
# public virtual int Add(T item)
Add an item to the ordered list, sorting it into place appropriately based on the rules set with the constructor.

# public virtual void Add(params T[] items)
Add an array to the ordered list, sorting it into place appropriately based on the rules set with the constructor.

# public virtual void Add(IEnumerable<T> items)
Add an enumerable to the ordered list, sorting it into place appropriately based on the rules set with the constructor.

# public virtual void AppendSorted(IEnumerable<T> items)
Add already sorted items to the end of the ordered list.

# public virtual void Clear()
Clear the ordered list.

# public OrderedList<T> Clone()
Make a copy of this ordered list and pass it back full of the current items.

# public bool Contains(T item)

# public bool Contains(Func<T, int> comparer)

# public void CopyTo(T[] array, int arrayIndex)

# public virtual int Count
The count of items in the ordered list.

# public void ForEach(Action<T> action)
Loop over each item in the ordered list.

# public void ForEach(Action<T, int> action)
Loop over each item in the ordered list. 

Included is the index of the item. Safe, if someone wants to use RemoveAt in the loop.

# public IEnumerator<T> GetEnumerator()

# public virtual int IndexOf(T item)
Find Index of item or its opposite where to insert the item if not found.

# public virtual int IndexOf(Func<T, int> comparer)
Using your own comparer, find Index of item or its opposite where to insert the item if not found.

# public virtual void Insert(int index, T item)
Insert item into ordered list.

Remarks: Does up to two compares to verify that it is being inserted properly.
Exception: InvalidInsertException - Index for item puts item out of order

# public virtual T Item(Func<T, int> comparer)
Find Item if found or default(T) if not.

# public virtual T Item(object key)
Find Item if found or default(T) if not.

Remarks: Generic Type must be of type IComparable to use this method.

# public virtual void LoadSorted(IEnumerable<T> items)
Load a (new) list of already sorted items. Clears the old list first.

# public virtual void Remove(params T[] items)
Remove an array of items.

# public virtual void Remove(IEnumerable<T> items)
Remove an enumerable of items.

# public virtual int Remove(T item)
This will remove the correct item if this is a non-repeating list or the comparer can determine the correct item in a repeating list.

# public virtual int Remove(object key)
Remove item and return its index if it was found.

Remarks: Generic Type must be of type IComparable to use this method.

# public virtual int Remove(object key, out T item)
Remove item and return its index if it was found.

Remarks: Generic Type must be of type IComparable to use this method.

# public virtual int Remove(Func<T, int> comparer)

# public virtual int Remove(Func<T, int> comparer, out T item)

# public virtual void RemoveAt(int index)

# public virtual void RemoveAt(int index, out T item)

# public virtual void Reverse()
Reverses the list.

WARNING: Comparer may be invalid if adding new items or calling IndexOf(item).

# public virtual void Sort()
Re-sort the list.

# public virtual void Sort(Action<T, int> itemAdded)
Re-sort the list with own comparer.

# public virtual T this[int index]

## Static Methods
# public static OrderedList<O> NewOrderedList<O>
New OrderedList of type T, no duplicates and doesn't replace if found on add.

## Extra
There are a bunch of list.BinarySearch type extension methods included with this package.