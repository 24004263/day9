# Build a Django Todo App with User Login and Admin Dashboard
# home.html:
```
<h2>Welcome, {{ request.user.username }}</h2>
<a href="{% url 'logout' %}">Logout</a>

{% if request.user.is_superuser %}
  <h3>All Users</h3>
  <ul>
    {% for user in users %}
      <li>{{ user.username }}</li>
    {% endfor %}
  </ul>

  <h3>All Tasks</h3>
  <ul>
    {% for task in tasks %}
      <li>{{ task.title }} — {{ task.user.username }}</li>
    {% endfor %}
  </ul>
{% else %}
  <h3>Your Tasks</h3>
  <ul>
    {% for task in tasks %}
      <li>{{ task.title }} {% if task.completed %}(Completed){% endif %}</li>
    {% endfor %}
  </ul>
{% endif %}
```
# login.html:
```
<h2>Login</h2>
<form method="post">
  {% csrf_token %}
  <input type="text" name="username" placeholder="Username">
  <input type="password" name="password" placeholder="Password">
  <button type="submit">Login</button>
</form>
<a href="{% url 'register' %}">Register</a>
```
# register.html:
```
<h2>Register</h2>
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Register</button>
</form>
<a href="{% url 'login' %}">Login</a>
```
# output:
![Screenshot 2025-07-08 123446](https://github.com/user-attachments/assets/57822ddc-3c9c-4784-a2c5-1bf9ed283acb)
![Screenshot 2025-07-08 123353](https://github.com/user-attachments/assets/bc207998-8d17-4bc0-87b6-896ba8ff3596)
