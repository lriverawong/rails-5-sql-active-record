# Devcamp Deep Dive on SQL

> This is the project demo code for the Devcamp [Deep Dive on SQL](https://rails.devcamp.com/trails/dissecting-rails-5) from the Dissecting Rails 5 course.

## To do to run rails app
```
rails db:create
rails db:migrate
rails db:setup
```
## Some rails console commands ran
```
Book.where(title: "The Force")
Book.where(title: "The Force").class
# shows you that where returns a collection
Book.find_by_title("The Force").class
# show you that this returns the book object
```
Show you that rails dynamically creates method for database table attributs
```
Author.find_by_country("Tatooine")
```
Check if object exist based on association
```
leia = Author.find_by_name("Leia")
leia.books.any? # return false
luke = Author.find_by_name("Luke")
luke.books.any? # return true
```
Sum of all sales for "Vader" author
```
vader = Author.find_by_name("Vader")
vader.books.sum(:sales)
```
Average of all sales - (need to_f which converts it to float as it returns a big decimal by default)
```
Book.average(:sales).to_f
```
Find maximum of sales
```
Book.maximum(:sales)
```
Return collection sorted by parameter in certain order.
```
Book.order(':sales DESC')
```
Return author of book with most sales
```
Book.order('sales DESC').first.author.name
```
Reload rails console
```
reload!
```
Using has_many :x, through: :y relationships
Can do this because books contains author_id and genre_id
Can find all genres that Vader has written in
```
vader = Author.find_by_name("Vader").genres
```
