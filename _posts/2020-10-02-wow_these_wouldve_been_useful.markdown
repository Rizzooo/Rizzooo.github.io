---
layout: post
title:      "Wow. These Would've Been Useful!"
date:       2020-10-02 12:09:24 -0400
permalink:  wow_these_wouldve_been_useful
---


For those who struggled to understand or didn’t utilize the methods available for use through our has_many and belongs_to associations (like I did for some reason), here’s a run-down of some of the most useful methods when associating two objects. 

In this example the local variables ‘game’ and ‘user’ are used to replace ‘.collection’ and ‘.association’ respectively.

```
game = Game.find_by(:title = “Title”)

user = User.find_by(:username => “User”)
```

# Important Methods added by has_many: 
```
has_many :games
```

**.collection**

This method returns a collection of games that are associated with the instance variable assigned to an instance of the User class.

`user.games`


**.collection.build**

This method allows us to instantiate an object (a new game) from passed in parameters, and creates the association by assigning the appropriate foreign_key to the object. However, the associated object (the new game) is NOT yet saved.

`user.games.build(:title => “Title”, :genre => “Genre”)`


**.collection.create**

This method allows us to instantiate an object (a new game) from passed in parameters, and creates the association by assigning the appropriate foreign_key to the object. The associated object (the new game) in this case IS saved.

`user.games.create(:title => “Title”, :genre => “Genre”)`


**.collection<< object**

This method adds the object (game1) to the collection by setting its foreign key to the appropriate value (the primary key of the user).

`user.games << game`


**.collection.delete**

This method allows us to remove objects (games) from the collection (user) by setting the foreign key of the object to ‘null’. Objects are destroyed or deleted depending upon the object’s associations:
* If they’re associated with `dependent: :destroy`, the object is destroyed.
* If they’re associated with `dependent: :delete_all`, the object is deleted.

`user.games.delete(game)`


**.collection.destroy**

This method allows us to remove objects (games) from the collection (user) by running ‘destroy’ on each object passed in. Objects are always destroyed regardless of the :dependent association.

`@user.games.destroy(game)`


**.collection.find**
This method allows us to find objects (games) belonging to the collection (user). Syntax is the same as with ActiveRecord::Base.

`@user.games.find(1)`



# Important Methods added by belongs_to: 
```
belongs_to :user
```

**.association**

This method returns the associated object (user).

`game.user`


**.association=**

This method allows us to assign an associated object (user) to our game object by extracting primary key from associated object and setting foreign key of this object to that value.

`game.user=(user)`


**.build_association**

This method allows us to instantiate an object (a new user) from passed in attributes, and creates the association by assigning the appropriate foreign_key to the object. Object will not be saved.

`game.build_user(:username => “Username”, :password => “Password”)`


**create_association**

This method allows us to instantiate an object (a new user) from passed in attributes, and creates the association by assigning the appropriate foreign_key to the object. Once validations in the associated model are passed, the object will be saved.

`game.create_user(:username => “Username”, :password => “Password”)`


This conclude my run-down of some very useful methods added to our repertoire with our has_many/belongs_to associations. It's important to keep in mind that there are quite a few more methods we have access to with these associations that can be helpful as well, however those above could save a ton of work building out functionality and testing associations!






