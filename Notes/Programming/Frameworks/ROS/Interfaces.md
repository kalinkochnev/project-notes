# Interfaces
**Interface description language (IDL)** - describes interfaces for communication

## File types

# `.msg` files
- Text files that describe fields of a ROS message
```
fieldtype1 fieldname1
fieldtype2 fieldname2
fieldtype3 fieldname3
```

# `.srv` files
- Describes a service
- Contains a request and a response which can make use of message types
```
#request constants
int8 FOO=1
int8 BAR=2
#request fields
int8 foobar
another_pkg/AnotherMessage msg
---
#response constants
uint32 SECRET=123456
#response fields
another_pkg/YetAnotherMessage val
CustomMessageDefinedInThisPackage value
uint32 an_integer
```

# `.action` files
- Contains a goal, a result, and feedback.
```
# Define the goal
uint32 dishwasher_id  # Specify which dishwasher we want to use
---
# Define the result
uint32 total_dishes_cleaned
---
# Define a feedback message
float32 percent_complete
```

## Field types
https://docs.ros.org/en/jazzy/Concepts/Basic/About-Interfaces.html#messages
