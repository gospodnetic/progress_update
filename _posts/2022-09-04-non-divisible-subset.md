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

## Complete code (with provided code as well)

```cpp
#include <bits/stdc++.h>

using namespace std;

string ltrim(const string &);
string rtrim(const string &);
vector<string> split(const string &);

/*
 * Complete the 'nonDivisibleSubset' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER k
 *  2. INTEGER_ARRAY s
 */

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

int main()
{
    ofstream fout(getenv("OUTPUT_PATH"));

    string first_multiple_input_temp;
    getline(cin, first_multiple_input_temp);

    vector<string> first_multiple_input = split(rtrim(first_multiple_input_temp));

    int n = stoi(first_multiple_input[0]);

    int k = stoi(first_multiple_input[1]);

    string s_temp_temp;
    getline(cin, s_temp_temp);

    vector<string> s_temp = split(rtrim(s_temp_temp));

    vector<int> s(n);

    for (int i = 0; i < n; i++) {
        int s_item = stoi(s_temp[i]);

        s[i] = s_item;
    }

    int result = nonDivisibleSubset(k, s);

    fout << result << "\n";

    fout.close();

    return 0;
}

string ltrim(const string &str) {
    string s(str);

    s.erase(
        s.begin(),
        find_if(s.begin(), s.end(), not1(ptr_fun<int, int>(isspace)))
    );

    return s;
}

string rtrim(const string &str) {
    string s(str);

    s.erase(
        find_if(s.rbegin(), s.rend(), not1(ptr_fun<int, int>(isspace))).base(),
        s.end()
    );

    return s;
}

vector<string> split(const string &str) {
    vector<string> tokens;

    string::size_type start = 0;
    string::size_type end = 0;

    while ((end = str.find(" ", start)) != string::npos) {
        tokens.push_back(str.substr(start, end - start));

        start = end + 1;
    }

    tokens.push_back(str.substr(start));

    return tokens;
}
```
