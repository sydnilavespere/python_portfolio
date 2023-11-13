# python_portfolio
This is the portfolio including my final project for Python

# Python Fundamentals: 

#Any python interpreter can be used as a calculator: 
3 + 5 * 4
```




    23




```python
# Lets save a value to a variable 
weight_kg = 60
```


```python
print(weight_kg)
```

    60



```python
# Weight0= valud
# 0weight = invalid
# weight and Weight are different 
```


```python
# Types of data
# There are three common types of data 
# Integer numbers 
# floating point numbers 
# Strings 
```


```python
weight_kg = 60.3
```


```python
# String comprised of Letters 
patient_name = "John Smith"
```


```python
# String comprised of numbers 
patient_id = '001'
```


```python
# Use variables in python 

weight_lb = 2.2 * weight_kg

print(weight_lb)
```

    132.66



```python
# Lets add a prefix to our patient id 

patient_id = 'inflam_' + patient_id

print(patient_id)
```

    inflam_001



```python
# Lets combine print statements 

print(patient_id, 'weight in kilograms:' , weight_kg)
```

    inflam_001 weight in kilograms: 60.3



```python
# we can call a function inside another function

print(type(60.30))

print(type(patient_id))
```

    <class 'float'>
    <class 'str'>



```python
# we can also do calculations inside the print function 

print('weight in lbs:' , 2.2 * weight_kg)
```

    weight in lbs: 132.66



```python
print(weight_kg)
```

    60.3



```python
weight_kg = 65.0
print('weight in kilograms us now:' , weight_kg)
```

    weight in kilograms us now: 65.0






# Analyzing Patient Data (1,2,3): 


```python
import numpy
```


```python
numpy.loadtxt(fname = 'inflammation-01.csv' , delimiter = ',')
```




    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])




```python
data = numpy.loadtxt(fname = 'inflammation-01.csv' , delimiter = ',')


```


```python
print(data)
```

    [[0. 0. 1. ... 3. 0. 0.]
     [0. 1. 2. ... 1. 0. 1.]
     [0. 1. 1. ... 2. 1. 1.]
     ...
     [0. 1. 1. ... 1. 1. 1.]
     [0. 0. 0. ... 0. 2. 0.]
     [0. 0. 1. ... 1. 1. 0.]]



```python
print(type(data))
```

    <class 'numpy.ndarray'>



```python
print(data.shape)
```

    (60, 40)



```python
print('firt value in data:' , data[0,0])
```

    firt value in data: 0.0



```python
print('middle value in data:' , data[29,19])
```

    middle value in data: 16.0



```python
print(data[0:4, 0:10])
```

    [[0. 0. 1. 3. 1. 2. 4. 7. 8. 3.]
     [0. 1. 2. 1. 2. 1. 3. 2. 2. 6.]
     [0. 1. 1. 3. 3. 2. 6. 2. 5. 9.]
     [0. 0. 2. 0. 4. 2. 2. 1. 6. 7.]]



```python
print(data[5:10, 0:10])
```

    [[0. 0. 1. 2. 2. 4. 2. 1. 6. 4.]
     [0. 0. 2. 2. 4. 2. 2. 5. 5. 8.]
     [0. 0. 1. 2. 3. 1. 2. 3. 5. 3.]
     [0. 0. 0. 3. 1. 5. 6. 5. 5. 8.]
     [0. 1. 1. 2. 1. 3. 5. 3. 5. 8.]]



```python
small = data[:3, 36:]
```


```python
print('small is:')
```

    small is:



```python
print(small)
```

    [[2. 3. 0. 0.]
     [1. 1. 0. 1.]
     [2. 2. 1. 1.]]



```python
# Lets us a numpy function 
print(numpy.mean(data))
```

    6.14875



```python
maxval, minval, stdval = numpy.amax(data), numpy.amin(data), numpy.std(data)
```


```python
print(maxval)
print(minval)
print(stdval)
```

    20.0
    0.0
    4.613833197118566



```python
maxval = numpy.amax(data)
minval = numpy.amin(data)
stdval = numpy.std(data)

```


```python
print('maximum inflammation:' ,maxval)
print('minimum inflammation:' , minval)
print('standard deviation:' , stdval)
```

    maximum inflammation: 20.0
    minimum inflammation: 0.0
    standard deviation: 4.613833197118566



```python
# Sometimes we want to look at variation in statistical values, such as maximum inflammationper patient, 
# or average from day one.

patient_0 = data[0,:] # 0 on the first axis (rows), everything on the second (columns)

print('maximum inflammation for patient 0:' , numpy.amax(patient_0))

```

    maximum inflammation for patient 0: 18.0



```python
print('maximum inflammation for patient 2:' , numpy.amax(data[2, :]))
```

    maximum inflammation for patient 2: 19.0



```python
print(data)
```

    [[0. 0. 1. ... 3. 0. 0.]
     [0. 1. 2. ... 1. 0. 1.]
     [0. 1. 1. ... 2. 1. 1.]
     ...
     [0. 1. 1. ... 1. 1. 1.]
     [0. 0. 0. ... 0. 2. 0.]
     [0. 0. 1. ... 1. 1. 0.]]



```python
print(numpy.mean(data, axis = 0).shape)
```

    (40,)



```python
print(numpy.mean(data,axis = 1))
```

    [5.45  5.425 6.1   5.9   5.55  6.225 5.975 6.65  6.625 6.525 6.775 5.8
     6.225 5.75  5.225 6.3   6.55  5.7   5.85  6.55  5.775 5.825 6.175 6.1
     5.8   6.425 6.05  6.025 6.175 6.55  6.175 6.35  6.725 6.125 7.075 5.725
     5.925 6.15  6.075 5.75  5.975 5.725 6.3   5.9   6.75  5.925 7.225 6.15
     5.95  6.275 5.7   6.1   6.825 5.975 6.725 5.7   6.25  6.4   7.05  5.9  ]

# Storing values in lists

```python
odds = [1, 3, 5, 7]
print('odds are:', odds)
```

    odds are: [1, 3, 5, 7]



```python
print('first element:', odds[0])
print('last element:', odds[3])
print('"-1" element:', odds [-1])
```

    first element: 1
    last element: 7
    "-1" element: 7



```python
names = ['Curie', 'Darwing', 'Turning'] #Typo in Darwin's name

print('names is orignally:', names)

names[1] = 'Darwin' # correct the name

print('final value of names:', names)
```

    names is orignally: ['Curie', 'Darwing', 'Turning']
    final value of names: ['Curie', 'Darwin', 'Turning']



```python
#name = 'Darwin'
#name [0] = 'd'
```


```python
odds.append(11)
print('odds after adding a value:', odds)
```

    odds after adding a value: [1, 3, 5, 7, 11]



```python
removed_element = odds.pop(0)
print('odds after removing the first element:', odds)
print('removed_element:', removed_element)
```

    odds after removing the first element: [3, 5, 7, 11]
    removed_element: 1



```python
odds.reverse()
print('odds after reversing:', odds)
```

    odds after reversing: [11, 7, 5, 3]



```python
odds = [3, 5, 7]
primes = odds
primes.append(2)
print('primes:', primes)
print('odds:', odds)
```

    primes: [3, 5, 7, 2]
    odds: [3, 5, 7, 2]



```python
odds = [3, 5, 7]
primes = list(odds)
primes.append(2)
print('primes:', primes)
print('odds:', odds)
```

    primes: [3, 5, 7, 2]
    odds: [3, 5, 7]



```python
binomial_name = "Drosophila melanogaster"
group = binomial_name[0:10]
print('group:', group)

species = binomial_name[11:23]
print('species:', species)

chromosomes = ['X', 'Y', '2', '3', '4']
autosomes = chromosomes[2:5]
print('autosomes:', autosomes)

last = chromosomes[-1]
print('last:', last)
```

    group: Drosophila
    species: melanogaster
    autosomes: ['2', '3', '4']
    last: 4



```python
date = 'Monday 4 January 2023'
day = date[0:6]
print('Using 0 to begin range:', day)
day = date[:6]
print('Omitting beginning index:', day)
```

    Using 0 to begin range: Monday
    Omitting beginning index: Monday



```python
months = ['jan', 'feb', 'mar', 'apr', 'may', 'jun', 'jul', 'aug', 'sep', 'oct', 'nov', 'dec']
sond = months[8:12]
print('With known last position:', sond)

sond = months[8:len(months)]
print('Using len() to get last entry:', sond)
sond = months[8:]
print('Omitting ending index:', sond)
```

    With known last position: ['sep', 'oct', 'nov', 'dec']
    Using len() to get last entry: ['sep', 'oct', 'nov', 'dec']
    Omitting ending index: ['sep', 'oct', 'nov', 'dec']


# Using loops

```python
odds = [1, 3, 5, 7]
```


```python
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```

    1
    3
    5
    7



```python
odds = [1, 3, 5]
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```

    1
    3
    5



    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-3-b48c9fadc7bf> in <module>
          3 print(odds[1])
          4 print(odds[2])
    ----> 5 print(odds[3])
    

    IndexError: list index out of range



```python
odds = [1, 3 , 5, 7, 9, 11, 13, 15, 17, 19]

for num in odds: 
    print(num)
```


```python
length = 0
names = ['Curie', 'Darwin', 'Turing']
for value in names:
    length = length + 1
print('There are', length, 'names in the list.')
```


```python
name = "Rosalind"
for name in ['Curie', 'Darwin', 'Turing']:
    print(name)
print('after the loop, name is', name)
```


```python
print(len([0,1,2,3]))
```


```python
name = ['Curie', 'Darwin', 'Turing']
print(len(name))
```


# Using multiple files

```python
import glob
```


```python
print(glob.glob('inflammation*.csv'))
```

    ['inflammation-10.csv', 'inflammation-09.csv', 'inflammation-11.csv', 'inflammation-06.csv', 'inflammation-05.csv', 'inflammation-08.csv', 'inflammation-01.csv', 'inflammation-07.csv', 'inflammation-04.csv', 'inflammation-03.csv', 'inflammation-02.csv', 'inflammation-12.csv']



```python
import glob
import numpy
import matplotlib.pyplot

filenames = sorted(glob.glob('inflammation*.csv'))
filenames = filenames[0:3]

for filename in filenames:
    print(filename)
    
    data = numpy.loadtxt(fname=filename, delimiter = ',')
    
    fig = matplotlib.pyplot.figure(figsize = (10.0, 3.0))
    
    axes1 = fig.add_subplot(1,3,1)
    axes2 = fig.add_subplot(1,3,2)
    axes3 = fig.add_subplot(1,3,3)
    
    axes1.set_ylabel('average')
    axes1.plot(numpy.mean(data, axis = 0))
    
    
    axes2.set_ylabel('max')
    axes2.plot(numpy.amax(data, axis = 0))
    
    axes3.set_ylabel('min')
    axes3.plot(numpy.amin(data, axis = 0))
    
    fig.tight_layout()
    matplotlib.pyplot.show()
```

# Making choices

```python
num = 37
if num > 100:
    print('greater')
else:
    print('not greater')
print('done')
```

    not greater
    done



```python
num = 53
print('before conditional...')
if num > 100:
    print(num, 'is greater than 100')
print('...after conditional')
```

    before conditional...
    ...after conditional



```python
num = 14

if num > 0:
    print(num, 'is positive')
elif num == 0:
    print(num, 'is zero')
else:
    print(num, 'is negative')
```

    14 is positive



```python
if (1 > 0) and (-1 >= 0): 
    print('both parts are true')
else:
    print('at least one part if false')
```

    at least one part if false



```python
if (1 > 0) or (-1 >= 0): 
    print('at least one part is true')
else:
    print('both of these are false')
```

    at least one part is true



```python

import numpy
```


```python
data = numpy.loadtxt(fname='inflammation-01.csv' , delimiter = ',')
```


```python
max_inflammation_0 = numpy.amax(data, axis = 0)[0]

```


```python
max_inflammation_20 = numpy.amax(data, axis = 0)[20]

if max_inflammation_0 == 0 and max_inflammation_20 == 20:
    print('Saspictious looking maxima!')
```

    Saspictious looking maxima!



```python
max_inflammation_20 = numpy.amax(data, axis = 0)[20]

if max_inflammation_0 == 0 and max_inflammation_20 == 20:
    print('Saspictious looking maxima!')
    
elif numpy.sum(numpy.amin(data, axis =0 ))==0:
    print('Minima add up to zero')
    
else:
    print('Seems OK!')
```

    Saspictious looking maxima!



```python
data = numpy.loadtxt(fname='inflammation-03.csv' , delimiter = ',')

max_inflammation_0 = numpy.amax(data, axis = 0)[0]

max_inflammation_20 = numpy.amax(data, axis = 0)[20]

if max_inflammation_0 == 0 and max_inflammation_20 == 20:
    print('Suspicious looking maxima!')
    
elif numpy.sum(numpy.amin(data, axis =0 ))==0:
    print('Minima add up to zero! -> HEALTHY PARTICIPANT ALERT!')
          
else:
    print('Seems OK!')
```

    Minima add up to zero! -> HEALTHY PARTICIPANT ALERT!


# Functions (1,2,3,4)

```python
farenheit_val = 99
celsius_val = ((farenheit_val -32) * (5/9))

print(celsius_val)
```

    37.22222222222222



```python
farenheit_val = 43
celsius_val = ((farenheit_val -32) * (5/9))

print(celsius_val)
```

    6.111111111111112



```python
def explicit_fahr_to_celsius(temp):
    # Assign the converted value to a variable 
    converted = ((temp - 32) * (5/9))
    # return the values of the new variable
    return converted
```


```python
def fahr_to_celsius(temp):
    # Return converted values more efficently using the return function without creating a new variable 
    # This code does the same thing as the previous function but it is more explicit in explaining how the return command works.
    return((temp -32) * (5/9))
```


```python
fahr_to_celsius(32)
```




    0.0




```python
explicit_fahr_to_celsius(32)
```




    0.0




```python
print('Freezing point of water:', fahr_to_celsius(32), 'C')
print('Boiling point of water:', fahr_to_celsius(212), 'C')
```

    Freezing point of water: 0.0 C
    Boiling point of water: 100.0 C



```python
def celsius_to_kelvin(temp_c):
    return temp_c + 273.15

print('freezing point of water in kelvin:', celsius_to_kelvin(0.))
```

    freezing point of water in kelvin: 273.15



```python
def fahr_to_kelvin(temp_f):
    temp_c = fahr_to_celsius(temp_f)
    temp_k = celsius_to_kelvin(temp_c)
    return temp_k
print('freezing point of water in kelvin:', fahr_to_kelvin(212))
```

    freezing point of water in kelvin: 373.15



```python
print('Again, temperature in kelvin was:', temp_k)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-10-4e4efe6231e3> in <module>
    ----> 1 print('Again, temperature in kelvin was:', temp_k)
    

    NameError: name 'temp_k' is not defined



```python
temp_kelvin = fahr_to_kelvin(212.0)
print('Temperature in Kelvin was:', temp_kelvin)
```


```python
def print_temperatures():
    print('Temperature in Fahrenheit was:', temp_fahr)
    print('Temperature in kelvin was:', temp_kelvin)
    
temp_fahr = 212.0
temp_kelvin = fahr_to_kelvin(temp_fahr)

print_temperatures()
```
```python
import numpy
import glob
import matplotlib
import matplotlib.pyplot
```


```python
def visualize(filename):
    data = numpy.loadtxt(fname= filename, delimiter = ',')
    
    fig = matplotlib.pyplot.figure(figsize=(10.0,3.0))
    
    axes1 = fig.add_subplot(1,3,1)
    axes2 = fig.add_subplot(1,3,2)
    axes3 = fig.add_subplot(1,3,3)
    
    axes1.set_ylabel('average')
    axes1.plot(numpy.mean(data, axis=0))
    
    axes2.set_ylabel('max')
    axes2.plot(numpy.max(data, axis=0))
    
    axes2.set_ylabel('min')
    axes3.plot(numpy.min(data, axis=0))
    
    fig.tight_layout()
    matplotlib.pyplot.show()
```


```python
def detect_problems(filename):
    
    data = numpy.loadtxt(fname= filename, delimiter = ',')
    
    if numpy.amax(data, axis = 0)[0] == 0 and numpy.amax(data, axis =0)[20]:
        print('Suspicious looking maxima!')
    elif numpy.sum(numpy.amin(data, axis = 0)) == 0:
        print('Minima add up to zero!')
    else:
        print('Seems ok!')
    
```


```python

filenames = sorted(glob.glob('inflammation*.csv'))

for filename in filenames[:3]:
    print(filename)
    visualize(filename)
    detect_problems(filename)
```

    inflammation-01.csv



![png](output_3_1.png)


    Suspicious looking maxima!
    inflammation-02.csv



![png](output_3_3.png)


    Suspicious looking maxima!
    inflammation-03.csv



![png](output_3_5.png)


    Suspicious looking maxima!



```python
def offset_mean(data, target_mean_value):
    return(data-numpy.mean(data)) + target_mean_value
```


```python
z = numpy.zeros((2,2))
print(offset_mean(z,3))
```

    [[3. 3.]
     [3. 3.]]



```python
data = numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')

print(offset_mean(data, 0))
```

    [[-6.14875 -6.14875 -5.14875 ... -3.14875 -6.14875 -6.14875]
     [-6.14875 -5.14875 -4.14875 ... -5.14875 -6.14875 -5.14875]
     [-6.14875 -5.14875 -5.14875 ... -4.14875 -5.14875 -5.14875]
     ...
     [-6.14875 -5.14875 -5.14875 ... -5.14875 -5.14875 -5.14875]
     [-6.14875 -6.14875 -6.14875 ... -6.14875 -4.14875 -6.14875]
     [-6.14875 -6.14875 -5.14875 ... -5.14875 -5.14875 -6.14875]]



```python
print('original min, mean and max are:', numpy.amin(data), numpy.mean(data), numpy.amax(data))
offset_data = offset_mean(data,0)
print('min, mean,and max of offset data are:',
      numpy.amin(offset_data),
      numpy.mean(offset_data),
      numpy.amax(offset_data))
```

    original min, mean and max are: 0.0 6.14875 20.0
    min, mean,and max of offset data are: -6.14875 2.842170943040401e-16 13.85125



```python
print('std dev before and after:', numpy.std(data), numpy.std(offset_data))
```

    std dev before and after: 4.613833197118566 4.613833197118566



```python
print('difference in standard deviation before and after:', numpy.std(data) - numpy.std(offset_data))
```

    difference in standard deviation before and after: 0.0



```python
# offset_mean(data, target_mean_value):
#return a new array containing the original data with its mean offset to match the desired value. 

def offset_mean(data, target_mean_value):
    return (data - numpy.mean(data)) + target_mean_value
```


```python
def offset_mean(data, target_mean_value):
    """Return a new array containing the original data with its mean offset to match the desired value"""
    return(data - numpy.mean(data)) + target_mean_value
```


```python
help(offset_mean)
```

    Help on function offset_mean in module __main__:
    
    offset_mean(data, target_mean_value)
        Return a new array containing the original data with its mean offset to match the desired value
   
    def offset_mean(data, target_mean_value):
    """Return a new array containing the original data with its mean offset to match the desired value"""
    
    Examples
   
    
    Offset_mean([1,2,3], 0)
    array([-1., 0., 1.])
    
    return (data - numpy.mean(data)) + target_mean_value



# Defensive programming
```python
numbers = [1.5, 2.3, 0.7, -0.001, 4.4]
total = 0.0
for num in numbers:
    assert num > 0.0, 'Data should only contain positive values'
    total += num
print('total is:', total)
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-2-13c7d5640ddd> in <module>
          2 total = 0.0
          3 for num in numbers:
    ----> 4     assert num > 0.0, 'Data should only contain positive values'
          5     total += num
          6 print('total is:', total)


    AssertionError: Data should only contain positive values



```python
def normalize_rectangle(rect):
    '''Normalizes a rectangle so that it is at the origin and 1.0 units long on its longest axis. input should be of the format (x0, y0, x1, y1), (x0, y0) and (x1, y1) define the lower left and upper right corners of the rectangle respectively'''
    assert len(rect) == 4, 'Rectangles must contain 4 coordintes'
    x0, y0, x1, y1 = rect
    assert x0 < x1, 'Invalid x coordinates'
    assert y0 < y1, 'Invalid Y coordinates'
    
    dx = x1 - x0
    dy = y1 -y0
    if dx > dy:
        scaled = dy / dx
        upper_x, upper_y = 1.0, scaled
    else: 
        scaled = dx / dy
        upper_x, upper_y = scaled, 1.0
        
    assert 0 < upper_x <= 1.0, 'Calculated upper x coordinate invalid'
    assert 0 < upper_y <= 1.0, 'Calculated upper y coordinate invalid'
    
    return (0, 0, upper_x, upper_y)
```


```python
print(normalize_rectangle( (0.0, 1.0, 2.0)))
```


```python
print(normalize_rectangle( (4.0, 2.0, 1.0, 5.0)))
```


```python
print(normalize_rectangle( (0.0, 0.0, 1.0, 5.0)))
```


```python
print(normalize_rectangle( (0.0, 0.0, 5.0, 1.0)))
```




# Transcribing DNA to RNA

#Prompt the user to input the FASTA file name

input_file_name = input("Enter the name of the input fasta file:")
```

    Enter the name of the input fasta file: sumo.txt



```python
# open the input fasta file and read the DNA sequence 

with open(input_file_name, "r") as input_file:
    dna_sequence = ""
    for line in input_file:
        if line.startswith(">"):
            continue
        dna_sequence += line.strip()
```


```python
# Transcribe the DNA to RNA

rna_sequence = ""
for nucleotide in dna_sequence:
    if nucleotide == "T":
        rna_sequence += "U"
    else: 
        rna_sequence += nucleotide
```


```python
# Prompt the user to enter the output file name

output_file_name = input("Enter the name of the output file:")
```

    Enter the name of the output file: sumoRNA.txt



```python
# Save the RNA sequence to a text file

with open(output_file_name, "w") as output_file:
    output_file.write(rna_sequence)
print("the RNA sequence has been saved to (output_file_name)")
```

    the RNA sequence has been saved to (output_file_name)



```python
print(rna_sequence)
```

    AUGUCUGACGAAAAGAAGGGAGGUGAGACCGAGCACAUCAACCUGAAGGUCCUCGGCCAGGACAACGCCGUCGUCCAGUUCAAGAUCAAGAAGCACACACCCUUGAGGAAGCUGAUGAACGCCUACUGCGACCGUGCCGGACUCUCCAUGCAGGUGGUGCGCUUCCGUUUCGACGGACAGCCCAUCAACGAGAACGACACUCCGACCUCGCUGGAGAUGGAGGAGGGCGACACCAUCGAGGUUUACCAGCAGCAGACUGGUGGCGCUCCAUAA



# Translating RNA to Proteins

#Prompt the user to enter the input RNA file name 

input_file_name = input("Enter the name of the input RNA file")
```

    Enter the name of the input RNA file sumoRNA.txt



```python
# open the input RNA file and read the RNA sequence 

with open(input_file_name, "r") as input_file:
    rna_sequence = input_file.read().strip()
```


```python
# define the codon table

codon_table = {
    "UUU": "F", "UUC": "F", "UUA": "L", "UUG": "L",
    "CUU":"L",  "CUC": "L", "CUA": "L", "CUG": "L",
    "AUU":"I",  "AUC": "I", "AUA": "I", "AUG": "M", 
    "GUU":"V",  "GUC": "V", "GUA": "V", "GUG": "V", 
    "UCU":"S",  "UCC": "S", "UCA": "S", "UCG": "S", 
    "CCU":"P",  "CCC": "P", "CCA": "P", "CCG": "P", 
    "ACU":"T",  "ACC": "T", "ACA": "T", "ACG": "T", 
    "GCU":"A",  "GCC": "A", "GCA": "A", "GCG": "A", 
    "UAU":"Y",  "UAC": "Y", "UAA": "*", "UAG": "*", 
    "CAU":"H",  "CAC": "H", "CAA": "Q", "CAG": "O", 
    "AAU":"N",  "AAC": "N", "AAA": "K", "AAG": "K", 
    "GAU":"D",  "GAC": "D", "GAA": "E", "GAG": "E", 
    "UGU":"C",  "UGC": "C", "UGA": "*", "UGG": "W", 
    "CGU":"R",  "CGC": "R", "CGA": "R", "CGG": "R", 
    "AGU":"S",  "AGC": "S", "AGA": "R", "AGG": "R", 
    "GGU":"G",  "GGC": "G", "GGA": "G", "GGG": "G", 
}
```


```python
# Translate RNA to protein 

protein_sequence = " " 
for i in range(0, len(rna_sequence), 3):
    codon = rna_sequence[i: i+3]
    if len (codon) == 3:
        amino_acid = codon_table[codon]
        if amino_acid == "*":
            break 
        protein_sequence += amino_acid
```


```python
# prompt the user to enter the output file name 

output_file_name = input("Enter the name of the output file:")

```

    Enter the name of the output file: proteins.txt



```python
# save the protein sequence to a text file

with open(output_file_name, "w") as output_file:
    output_file.write(protein_sequence)
    print(f"The protein sequence has been saved to {output_file_name}")
```

    The protein sequence has been saved to proteins.txt



```python
print(protein_sequence)
```

     MSDEKKGGETEHINLKVLGODNAVVOFKIKKHTPLRKLMNAYCDRAGLSMOVVRFRFDGOPINENDTPTSLEMEEGDTIEVYOOOTGGAP




