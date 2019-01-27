# HandlingConcurrentCalls
At Booking.com, our customer service team is an important contributor to customer satisfaction. During busy times,
however, there might be more calls to customer service than the number of customer service executives can manage.
Fortunately, we record data on that. We've collected information about all phone calls to our call centres for the past
year.


Given that our current number of customer care executives is , determine how many more people we would need to hire,
to make sure that our customers would not have to wait during peak hours (i.e. that we don't have more phone calls than
we have customer service executives).
```
e.g:
Input:
1481122000 - 1481122020
1481122000 - 1481122040
1481122030 - 1481122035

Output:
1
```
Explanation:
The first call overlaps with the second call. The third call also overlaps with the second call. However, the first
and the third calls are not overlapping with each other. This means that we have atleast 2 concurrent calls. Given that
there was only one customer service representative to start we would need to employ one more customer service
representative, to make sure that all customer calls are handled as soon as they arrive.


Solution:
1. Create a new array and mark entry time as positive and exit time as negative. The array will look like this
```
list = {1481122000, -1481122020, 1481122000, -1481122040, 1481122030, -1481122035};
```

2. Sort the array by passing in customized comparator. The comparator will sort the array by its values and not taking
negative sign into consideration. The sorted array will look like this:
```
list = {1481122000, 1481122000, -1481122020, 1481122030, -1481122035, -1481122040};
```

3. One the array is sorted. Loop over the array adding to the counter when value is positive and subtracting when
value is negative.

4. The function will return the maximum concurrent calls alive at any moment.
