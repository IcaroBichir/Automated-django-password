----------

Scrip made in expect to change the Django password. In this case, I did this to execute inside a Ansible role.

Follow this steps:

1 - Include the package in your role dependencies, to install when execute the playbook.

>> expect

2 - Include the YML file on your main.yml.

>> include: django-user.yml

3 - Execute your playbook with this new files. xD



----------

{% highlight bash %}
#!/usr/bin/expect

set user [lindex $argv 0]
set key [lindex $argv 1]

spawn python manage.py changepassword ${user}
expect "*Password:*"
send "${key}\r"
expect "*(again)*"
send "${key}\r"
{% endhighlight %}

----------
