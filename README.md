## Solution of task-functions-decorators
```
def filter_nums(func):
    def inner(items):
        new_list = []
        for item in items:
            if type(item) == int:
                new_list.append(item)
        return func(new_list)

    return inner


def double_nums(func):
    def inner(new_list):
        new_dict = {}
        for item in new_list:
            new_dict[item] = item * item
        return func(new_dict)

    return inner


def transform_nums(func):
    def inner(new_dict):
        result = []
        for key, value in new_dict.items():
            result.append(f"{key}^2 = {value}")
        return func(result)

    return inner


@filter_nums
@double_nums
@transform_nums
def f1(items: list):
    return f"To transform this list into string we need to decorate it first!" \
           f"After transformation: {', '.join(items)}."
```