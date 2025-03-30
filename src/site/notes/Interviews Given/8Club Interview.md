---
{"dg-publish":true,"permalink":"/interviews-given/8-club-interview/"}
---



## Interview 1

### General Questions

1. How do you usually prefer to learn about new technologies?
2. Will you be able to work from the office during your last semester?
3. How did you use Helm and CircleCI in your work at Fynarfin?
4. [[Interview/Interview Prep#1. Introduce yourself and your tech stack.\|Introduce yourself.]]


### Backend Development

1. How many backend frameworks do you have experience with?
2. Have you ever worked with FastAPI?
3. How exactly were you using Django in your work with Zulip?
4. [[Interview/Backend/Backend Role#3. What is idempotent and safe in context of API?\|What is idempotency?]]
5. [[Interview/Backend/Backend Role#2. Difference between put, post, and patch methods?\|What is the difference between PUT and PATCH APIs?]]

### SQL

1. Have you ever encountered an N+1 optimization problem?
2. Write an SQL query to get details from the `payments` table, which has a foreign key referencing the `orders` table, which in turn has a foreign key referencing the `customers` table. You need to perform a join operation.

### What went right:

I was able to answer all the questions easily (Thanks to my backend roles).

## Interview 2

### Python Basics

1. What are magic functions?
2. What are dunder functions?
3. What is list comprehension?
4. What are `*args` and `**kwargs`?
5. How do you declare a class in Python?
6. How do you write a constructor in Python?

### Python Coding and Problem Solving

1. What will be the output of the given code?
```python
def print_output(*args, **kwargs):
    print(args)
    print(kwargs)
    
    
print_output(1, 2, name="hello", age=21)


# Output:
# (1, 2)
# {'name': 'hello', 'age': 21}
```

2. Print the list of ids without the dictionary just a list of numbers:
```python
list1 = [
    {
        "id": 1
    },
    {
        "id": 2
    }
]

print(list1)

# Answer:
# list2 = [i["id"] for i in list1]
# print(list2)
```

3. Write code snippet for creating a class with name property and then create an instance of class with name as "dog".
```python
class Animals:
    def __init__(self, animal_name):
        self.name = animal_name
    def __str__(self):
        return f"Animal: {self.name}"

dog = Animals("dog")

print(dog)  # Outputs: Animal: dog

```
### System Design

1. Design an authentication system for 8club with the following features:
    - Generate OTP
    - Verify OTP
    - Implement OTP throttling
    - Generate JWT tokens

### What went wrong:

I was unfamiliar with some Python-specific terminology, such as magic functions and dunder functions, even though I knew how to use them. I also struggled to predict the output of Python code correctly on the first try. Additionally, I found the system design task challenging, as I kept missing important classes and needed frequent nudges from the interviewer to move in the right direction.