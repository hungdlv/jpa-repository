JPA Repository
==============

Repository programming model with JPA 2 and [Specification](http://en.wikipedia.org/wiki/Specification_pattern) pattern provides a simple and easy way to build the data access layer.

Usage
-----------

**Create an example entity User**

<pre><code>
    @Entity
    public class User extends EntityObject<Long> {
    	private String name;
    	private Integer age;
    
    	public User() {}
    
    	public User(final String name, final Integer age) {
    		this.name = name;
    		this.age = age;
    	}

        //getter/setter here
    
    }
</code></pre>

**Create an instance of <code>Repository</code>**
<pre><code>
EntityManager em = ...;
Repository repo = new JPARepository(em);
</code></pre>
**Find all instances of User**

<code>
List<User> users = repo.findAll(User.class)
</code>
	
**Find an User by Id**

<code>
User user = repo.findById(User.class, 1L);
</code>

**Find all Users has name "ABC"**

<pre><code>
//Create a specification
Specification<User> hasName = Specifications.equal("name", "Duy Do"); 
List<User> users = repo.findBySpecification(User.class, hasName).asList();
</code></pre>
