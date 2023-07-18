0x00. AirBnB clone - The console
Background Context
Welcome to the AirBnB clone project!
Before starting, please read the AirBnB concept page.
First step: Write a command interpreter to manage your AirBnB objects.
This is the first step towards building your first full web application: the AirBnB clone. This first step is very important because you will use what you build during this project with all other following projects: HTML/CSS templating, database storage, API, front-end integration…
Each task is linked and will help you to:
•	put in place a parent class (called BaseModel) to take care of the initialization, serialization and deserialization of your future instances
•	create a simple flow of serialization/deserialization: Instance <-> Dictionary <-> JSON string <-> file
•	create all classes used for AirBnB (User, State, City, Place…) that inherit from BaseModel
•	create the first abstracted storage engine of the project: File storage.
•	create all unittests to validate all our classes and storage engine
What’s a command interpreter?
Do you remember the Shell? It’s exactly the same but limited to a specific use-case. In our case, we want to be able to manage the objects of our project:
•	Create a new object (ex: a new User or a new Place)
•	Retrieve an object from a file, a database etc…
•	Do operations on objects (count, compute stats, etc…)
•	Update attributes of an object
•	Destroy an object
Tasks
0. README, AUTHORS
mandatory
•	Write a README.md:
o	description of the project
o	description of the command interpreter:
	how to start it
	how to use it
	examples
•	You should have an AUTHORS file at the root of your repository, listing all individuals having contributed content to the repository. For format, reference Docker’s AUTHORS page
•	You should use branches and pull requests on GitHub - it will help you as team to organize your work
1. Be pycodestyle compliant!
mandatory
Write beautiful code that passes the pycodestyle checks.
2. Unittests
mandatory
All your files, classes, functions must be tested with unit tests
3. BaseModel
mandatory
Write a class BaseModel that defines all common attributes/methods for other classes:
4. Create BaseModel from dictionary
mandatory
Previously we created a method to generate a dictionary representation of an instance (method to_dict()).
Now it’s time to re-create an instance with this dictionary representation.
5. Store first object
mandatory
Now we can recreate a BaseModel from another one by using a dictionary representation:
6. Console 0.0.1
mandatory
Write a program called console.py that contains the entry point of the command interpreter:
•	You must use the module cmd
•	Your class definition must be: class HBNBCommand(cmd.Cmd):
•	Your command interpreter should implement:
o	quit and EOF to exit the program
o	help (this action is provided by default by cmd but you should keep it updated and documented as you work through tasks)
o	a custom prompt: (hbnb)
o	an empty line + ENTER shouldn’t execute anything
•	Your code should not be executed when imported
7. Console 0.1
mandatory
Update your command interpreter (console.py) to have these commands:
•	create: Creates a new instance of BaseModel, saves it (to the JSON file) and prints the id. Ex: $ create BaseModel
o	If the class name is missing, print ** class name missing ** (ex: $ create)
o	If the class name doesn’t exist, print ** class doesn't exist ** (ex: $ create MyModel)
•	show: Prints the string representation of an instance based on the class name and id. Ex: $ show BaseModel 1234-1234-1234.
o	If the class name is missing, print ** class name missing ** (ex: $ show)
o	If the class name doesn’t exist, print ** class doesn't exist ** (ex: $ show MyModel)
o	If the id is missing, print ** instance id missing ** (ex: $ show BaseModel)
o	If the instance of the class name doesn’t exist for the id, print ** no instance found ** (ex: $ show BaseModel 121212)
•	destroy: Deletes an instance based on the class name and id (save the change into the JSON file). Ex: $ destroy BaseModel 1234-1234-1234.
o	If the class name is missing, print ** class name missing ** (ex: $ destroy)
o	If the class name doesn’t exist, print ** class doesn't exist ** (ex:$ destroy MyModel)
o	If the id is missing, print ** instance id missing ** (ex: $ destroy BaseModel)
o	If the instance of the class name doesn’t exist for the id, print ** no instance found ** (ex: $ destroy BaseModel 121212)
•	all: Prints all string representation of all instances based or not on the class name. Ex: $ all BaseModel or $ all.
o	The printed result must be a list of strings (like the example below)
o	If the class name doesn’t exist, print ** class doesn't exist ** (ex: $ all MyModel)
•	update: Updates an instance based on the class name and id by adding or updating attribute (save the change into the JSON file). Ex: $ update BaseModel 1234-1234-1234 email "aibnb@mail.com".
o	Usage: update <class name> <id> <attribute name> "<attribute value>"
o	Only one attribute can be updated at the time
o	You can assume the attribute name is valid (exists for this model)
o	The attribute value must be casted to the attribute type
o	If the class name is missing, print ** class name missing ** (ex: $ update)
o	If the class name doesn’t exist, print ** class doesn't exist ** (ex: $ update MyModel)
o	If the id is missing, print ** instance id missing ** (ex: $ update BaseModel)
o	If the instance of the class name doesn’t exist for the id, print ** no instance found ** (ex: $ update BaseModel 121212)
o	If the attribute name is missing, print ** attribute name missing ** (ex: $ update BaseModel existing-id)
o	If the value for the attribute name doesn’t exist, print ** value missing ** (ex: $ update BaseModel existing-id first_name)
o	All other arguments should not be used (Ex: $ update BaseModel 1234-1234-1234 email "aibnb@mail.com" first_name "Betty" = $ update BaseModel 1234-1234-1234 email "aibnb@mail.com")
o	id, created_at and updated_at cant’ be updated. You can assume they won’t be passed in the update command
o	Only “simple” arguments can be updated: string, integer and float. You can assume nobody will try to update list of ids or datetime
Let’s add some rules:
•	You can assume arguments are always in the right order
•	Each arguments are separated by a space
•	A string argument with a space must be between double quote
•	The error management starts from the first argument to the last one
8. First User
mandatory
Write a class User that inherits from BaseModel:
•	models/user.py
•	Public class attributes:
o	email: string - empty string
o	password: string - empty string
o	first_name: string - empty string
o	last_name: string - empty string
Update FileStorage to manage correctly serialization and deserialization of User.
Update your command interpreter (console.py) to allow show, create, destroy, update and all used with User.
9. More classes!
mandatory
Write all those classes that inherit from BaseModel:
•	State (models/state.py):
o	Public class attributes:
	name: string - empty string
•	City (models/city.py):
o	Public class attributes:
	state_id: string - empty string: it will be the State.id
	name: string - empty string
•	Amenity (models/amenity.py):
o	Public class attributes:
	name: string - empty string
•	Place (models/place.py):
o	Public class attributes:
	city_id: string - empty string: it will be the City.id
	user_id: string - empty string: it will be the User.id
	name: string - empty string
	description: string - empty string
	number_rooms: integer - 0
	number_bathrooms: integer - 0
	max_guest: integer - 0
	price_by_night: integer - 0
	latitude: float - 0.0
	longitude: float - 0.0
	amenity_ids: list of string - empty list: it will be the list of Amenity.id later
•	Review (models/review.py):
o	Public class attributes:
	place_id: string - empty string: it will be the Place.id
	user_id: string - empty string: it will be the User.id
	text: string - empty string
10. Console 1.0
mandatory
Update FileStorage to manage correctly serialization and deserialization of all our new classes: Place, State, City, Amenity and Review
Update your command interpreter (console.py) to allow those actions: show, create, destroy, update and all with all classes created previously.
Enjoy your first console!
11. All instances by class name
#advanced
Score: 100.0% (Checks completed: 100.0%)
Update your command interpreter (console.py) to retrieve all instances of a class by using: <class name>.all().
12. Count instances
#advanced
Score: 100.0% (Checks completed: 100.0%)
Update your command interpreter (console.py) to retrieve the number of instances of a class: <class name>.count().
13. Show
#advanced
Score: 100.0% (Checks completed: 100.0%)
Update your command interpreter (console.py) to retrieve an instance based on its ID: <class name>.show(<id>).
14. Destroy
#advanced
Score: 100.0% (Checks completed: 100.0%)
Update your command interpreter (console.py) to destroy an instance based on his ID: <class name>.destroy(<id>).
15. Update
#advanced
Score: 100.0% (Checks completed: 100.0%)
Update your command interpreter (console.py) to update an instance based on his ID: <class name>.update(<id>, <attribute name>, <attribute value>).
16. Update from dictionary
#advanced
Score: 100.0% (Checks completed: 100.0%)
Update your command interpreter (console.py) to update an instance based on his ID with a dictionary: <class name>.update(<id>, <dictionary representation>).
17. Unittests for the Console!
#advanced
Score: 0.0% (Checks completed: 0.0%)
Write all unittests for console.py, all features!

