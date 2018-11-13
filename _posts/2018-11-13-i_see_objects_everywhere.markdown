---
layout: post
title:      "I See Objects Everywhere"
date:       2018-11-13 17:57:47 +0000
permalink:  i_see_objects_everywhere
---

## self-referential join tables??

Working with Sinatra has really been a great way to cement the Object-oriented concepts introduced in the earier parts of the curriculum. I can really sense myself *seeing* objects, or "discovering objects" when I consider a new idea or project. In my life before code school I didn't really get that. I would see a "post" as a set of words, not as a "thing" that  contained a host of information about itself, of which  it was also self-aware. Asking objects questions about themselves really is the name of the game.

For my Sinatra portfolio project, I'm totally overdoing it. The app I want to make goes well beyond the project requirements, in an irresistibly interesting way:  self-referential join tables!  I need Users to relate to themselves in two different roles. As a result, I've learned a lot, and have many headaches and bugs still to cure.

Much like a User on other sites often relates to other users by "following" them, or by being "followed," my Users relate to each other either as a "loaner" (loaning someone a tool), or as a "borrower" (borrowing a tool from someone). Solving this problem has been kind of a doozy for me but I think I'm on the right track.

The essential piece is the "Contract" that relates a borrower to a loaner. So that model is relatively straightforward (ignoring Tools for now):
```
class Contract < ActiveRecord::Base
	belongs_to :loaner, foreign_key: "loaner_id", class_name: "User"
	belongs_to :borrower, foreign_key: "borrower_id", class_name: "User"
end
```

So far, so good. A Contract has a borrower and a loaner, and each of those comes from the User class.

About that User class.... A User can loan many tools, borrow many tools, and can do both simultaneously. So anything that classifies a User as exclusively a borrower or loaner is out. We need Users to relate to each other as borrowers or loaners *through* their Contracts. And, essentially, those Contracts are one of two flavors -- either the User is the loaner in the Contract (a loaner_contract), or the borrower (a borrower_contract).
```
class User < ActiveRecord::Base
	
	   # "loaner_contract == in the role of loaner
	   has_many :loaner_contracts, foreign_key: :loaner_id, class_name: "Contract"
	   has_many :borrowers, through: :loaner_contracts, source: :borrower 

	   # "borrower_contract" ==  in the role of borrower
	   has_many :borrower_contracts, foreign_key: :borrower_id, class_name: "Contract"
	   has_many :loaners, through: :borrower_contracts, source: :loaner
	
	end
```

This structure was very unwieldy to me at first, but after spending some time in the db playing around, it really started to sink in. It works! Loaners relate to Borrowers, Users to Users, and there is a Contract object that contains all of the relevant information.

Great! I thought I was homefree so I started fleshing out my views, cruising along and patting my self on the back for a job well done. 

Then I started making the logic for "terminating" a Contract... Basically in the Edit Contract page, we need to "Return the Tool", i.e. terminate the Contract.  And that's where the madness began. For some reason, I cannot change the "active" (boolean) attribute of a Contract and have it persist. The moment i change a Contract to inactive, I expected to become inactive in its guise as the Contract itself, one User's borrower_contract, and another User's loaner_contract.

But no! It doesn't! Even if I find those three instances and change them manually in the same method, the Contract itself immediately reverts back to "active: true" and I cannot for the life of my figure out why. I've Googled til my fingers were numb and read through Stack Overflow posts til my eyes crossed, and I still can't solve the problem.  I'm sure it's right in front of me, and I look forward to getting through it. 
