# [HackerRank] Non-Divisible Subset (C++)
![image](https://user-images.githubusercontent.com/15703361/188331574-ce331a51-f056-4745-9465-7f45a4a01fa2.png)

## Solution
```cpp
int nonDivisibleSubset(int k, vector<int> s)
{
    const bool is_even = k%2 == 0;
    
    vector<int> remainder_frequency(k, 0);
    for (auto it = s.begin(); it != s.end(); it++)
    {
        remainder_frequency[(*it) % k]++;
    }
    
    int max_set_size = 0;
    for (int i = 1; i <= k/2; i++)
    {
        if (is_even && i == k/2)
            break;
            
        max_set_size += max(remainder_frequency[i], remainder_frequency[k - i]);
    }
    if (remainder_frequency[0] > 0)
        max_set_size++;
    if (is_even && remainder_frequency[k/2] > 0)
        max_set_size++;
    
    return max_set_size;
}

```
