# Unit 7 Problem Set #3
## Schema Design and Building RESTful APIs

### Directions
1. Fork and clone this lab.
2. Answer the following questions directly in this README. Be sure that your answers are well-formatted.
3. For the final question (build a to-do list), create all of your necessary app files in this directory. (I have included GitHub's standard Node.js `.gitignore` template so that you don't end up pushing `node_modules` to GitHub.

##

0. **What are the four types of HTTP requests that correspond to _creating_, _reading_, _updating_, and _deleting_ resources? Why is it important to use these  different types of requests?**
<br>
```javascript
_creating_ - `POST`  
_reading_ - `GET`     
_updating_ - `PUT`    
_deleting_ - `DELETE`     
It is important to use different types of requests in order to tell the server what actions have to be performed based on information that is received from a user. This will allow the user to be provided the proper responses based on their requests.
```

1. **You've recently learned about an API for a cat sitting company. The API is fully RESTful for a resource called `cats`. You also happen to know that their database is running Postgresql on the backend. What are the five types of requests the API will respond to? Based on the description, list the HTTP method, the path, and what SQL the request will fire.**

| http method  |  path |  sql | description |
|---|---|---|---|
| POST | '/cats' | INSERT INTO cats (name, breed) VALUES ($1, $2);| Creating a cat |
| GET | '/cats' | SELECT * FROM cats; | Retrieving all the cats |
| GET | '/cats/:id' | SELECT * FROM cats WHERE id = $1;, [id]| Retrieving a specific cat |
| PUT | '/cats/:id' | UPDATE cats SET(name, breed) = $2, $3 WHERE id = $1;, [id, name, breed]| Updating a specific cat |
| DELETE | '/cats/:id' | DELETE * FROM cats WHERE id = $1;, [id] | Deleting a cat |

<br>

2. **You're working on a blogging application and doing some debugging. You see in the logs that the following SQL has fired:**

   ```sql
   SELECT * FROM articles WHERE id = 9;
   ```

   **Given that the application is RESTful, what HTTP method and request would you expect to have been made to fire that SQL?**
<br>
```javascript
A `GET` HTTP method would be expected and the request for the route where an article with an `id = 9` is made.
```

3. **You've been hired to do some work for Discogs, an application to help users track a vinyl record collection. A `Collection` has many `Albums`, and an `Album` has many collections via a join table called `Ownership`. You've been asked to build a feature that allows to remove an album from their collection. What HTTP Method/URL/controller action would you use to implement this feature?**
<br>

```javascript
To implement this feature I would use the `DELETE` HTTP method.  
The URL would be `'/album/:id/collection/:id'` as you would have to have the id of the album in order to look for the album id in the collection to successfully removed an album from a collection.  
```
4. **Choose your favorite web application. What's an example of a one-to-many and many-to-many relationship that might exist within the app?**
<br>
**Tumblr**
- one-to-many
  - one users post can have many reblogs but those reblogs only belong to that post
- many-to-many
  - a user can follow many blogs and many users of those blogs can follow the user.  

5. **Build a full CRUD, RESTful API using Express for a Todo List. A TodoList should have many items and belong to a user. Each endpoint should respond with the appropriate JSON response. Our API should support:**
   * **An index route to see a list of todos.**
   * **A show route to see details about an individual todo item.**
   * **The ability to update a todo (i.e. mark complete)**
   * **Delete a todo item**
   * **Create a Todo list item**

   **Deploy Your Project to Heroku and include a link here:**
