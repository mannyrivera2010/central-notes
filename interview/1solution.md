
Solution:
```
string_1 = '1258641a28755549631bkmmmikdika'

def count_value(input_string):
    d = {}
    for i in input_string:
        if i in d:
            d[i] = d[i] + 1
        else:
            d[i] = 1
    for k in sorted(d.keys()):
        print('The value {} has {} occurrences'.format(k, d[k]))

count_value(string_1)
```
