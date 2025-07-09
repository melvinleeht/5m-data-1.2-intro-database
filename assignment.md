# Assignment

## Brief

Create an ERD for each of the following case study question.

## Instructions

Paste the answer as DBML in the answer code section below each question.

### Question 1

Construct an ERD for a social media company whose database includes information about users, their followers, and the posts that they make. Users can follow multiple users and create multiple posts.

Each entity has the following attributes:

- User: id, username, email, created_at
- Post: id, title, body, user_id, status, created_at
- Follows: following_user_id, followed_user_id, created_at

Answer:

```
// Use DBML to define your database structure
// Docs: https://dbml.dbdiagram.io/docs

Table User {
  id integer [primary key, increment]
  username varchar
  email varchar
  created_at datetime
}

Table Post {
  id integer [primary key, increment]
  title varchar
  body varchar [note:"Post content"]
  user_id integer
  status varchar
  created_at datetime
}

Table Follows {
  following_user_id integer [primary key, increment]
  followed_user_id integer [primary key, increment]
  created_at datetime
}


Ref: User.id < Post.user_id //  one-to-many
Ref: User.id < Follows.following_user_id //  one-to-many
Ref: User.id < Follows.followed_user_id// one-to-many (user is followed by many)
```

### Question 2

Construct an ERD for a company that sells books online. The company has a website where customers can browse available books and add them to their shopping carts. Each cart can contain multiple books.

There are 4 entities, think of what attributes each entity should have.

- Customer
- Book
- Cart
- CartItem

Answer:

```
// Use DBML to define your database structure
// Docs: https://dbml.dbdiagram.io/docs
Table Customer {
  id integer [primary key, increment]
  name varchar
  address varchar
  email varchar
  phone varchar
  created_at datetime
}

Table Book {
  id integer [primary key, increment]
  title varchar
  author varchar
}

Table Cart {
  id integer [primary key, increment]
  user_id integer [unique] // Each user can only have one cart
  created_at datetime
}

Table CartItem {
  cart_id integer
  book_id integer
  quantity integer
}


Ref: Customer.id - Cart.user_id // one-to-one (each customer has one cart)
Ref: Book.id < CartItem.book_id // many-to-many (one cart can have many cart items)
Ref: Cart.id < CartItem.cart_id  // one-to-many (one book can appear in many cart items)

```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
