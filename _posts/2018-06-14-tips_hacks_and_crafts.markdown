---
layout: post
title:      "TIPs, Hacks, And Crafts"
date:       2018-06-14 21:10:06 +0000
permalink:  tips_hacks_and_crafts
---


If I've got a few minutes of spare time, I enjoy watching those life hacks videos on Youtube. Sure some are common sense, but there are quite a few that make me pause and think; I've got to remember that one. So when it was time to make my portfolio project, i thought why not make a collection site where users can submit their favorite tips, tricks, hacks, and crafts. I call it 'Tiphac' short for TIPs, Hacks, And Crafts (hey, all the other domains were taken).

The requiremnts for the project were pretty straight forward:

1. Build an MVC Sinatra Application.
2. Use ActiveRecord with Sinatra.
3. Use Multiple Models.
4. Use at least one has_many relationship on a User model and one belongs_to relationship on another model
5. Must have user accounts. The user that created a given piece of content should be the only person who can modify that content
6. Must have the abilty to create, read, update and destroy any instance of the resource that belongs to a user.
7. Ensure that any instance of the resource that belongs to a user can be edited or deleted only by that user.
8. You should also have validations for user input to ensure that bad data isn't added to the database. The fields in your signup form should be required and the user attribute that is used to login a user should be a unique value in the DB before creating the user.

The first three are pretty obvious, for number four, each `user` could have many `hacks`, and a `hack` would belong to a single `user`. This is accouplished in my models as you see in the code below:

```
class User < ActiveRecord::Base
**  has_many  :hacks
**
  has_secure_password

  def slug
    username.gsub(" ","-").downcase
  end

  def self.find_by_slug(slug)
    User.all.find{|user| user.slug == slug}
  end

end
```


```
class Hack < ActiveRecord::Base
**  belongs_to :user
**end
```

For six and seven, while any user should be able to 
