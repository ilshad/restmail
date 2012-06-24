Simple REST / SMTP gate
=======================

Build
-----

Make sure Erlang/OTP is installed already (`sudo apt-get install erlang-base` for Ubuntu).
Create config file:

  $ make config

Then edit SMTP options in config file "include/restmail.hrl".
Then build application:

  $ make

Run
---

  $ ./restmail {start|stop|attach|console}

Usage
------

Demo using Python shell:

  >>> import httplib2, json
  >>> h = httplib2.Http()

  >>> msg = json.dumps({"recipients": ["test1@example.com", "test2@example.com"],
                        "subject": "Welcome",
			"body": "<h1>The body of this message</h2>"})

  >>> r,c = h.request("http://localhost:9871/mail",
                       method="POST",
		       body=msg,
		       headers={"Content-Type":"application/json"})
