# aptwe

aptwe is a framework to create recursive descent parsers. It intends to define
parsers inside the Python syntax similarily to writing EBNF. For example:

~~~
nested_lists_ = Parser('NestedLists')
head_ = nested_lists_
tail_ = ~(str_(',') >> nested_lists_)[getitem(1)]
list_ = (str_('[') >> head_ >> tail_ >> str_(']'))[lambda x: [x[1]] + x[2]]
nested_lists_[...] = int_ | list_

nested_lists_.loads('[1,[2,3]]') # Returns [1,[2,3]]
~~~
