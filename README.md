1. Install Homebrew  -- http://brew.sh/
2. Install pip -- `sudo easy_install pip`
3. Install virtualenv -- `pip install virtualenv`
4. Checkout the repo -- `git clone https://github.com/bm1362/selfservice-updated.git`]
5. cd into the repo -- `cd selfservice-updated`
6. Create a virtualenv
> virtualenv venv
> New python executable in venv/bin/python
> Installing setuptools, pip...done.

7. Source the new virtualenv
     > source venv/bin/activate
     
8. Install python dependencies into the new virtualenv
     > pip install -r requirements.txt
     > ... bunch of output
     > Successfully installed Flask-0.9 Flask-Admin-1.0.2 Flask-Login-0.1.3 Flask-SQLAlchemy-0.16 Flask-Script-0.3.3 Flask-WTF-0.8 Jinja2-2.6 MySQL-python-1.2.3 SOAPpy-0.12.5 SQLAlchemy-0.7.7 WTForms-1.0.2 Werkzeug-0.8.3 argparse-1.2.1 fpconst-0.7.2 pyasn1-0.1.4 pycrypto-2.6.1 pysnmp-4.2.2 python-ldap-2.4.9 requests-1.0.3 wstools-0.4

9. Create a config directory under app/ and add config.cfg and ldap.cfg
> mkdir app/config
> touch app/config/config.cfg
> touch app/config/ldap.cfg

10. Setup config files
   > You should copy these from an existing installation, they contain passwords etc for ldap (see sample config below if you need to write from scratch)

11. Start local instance
   >  python manage.py runserver
   > Running on http://127.0.0.1:5000/

References:

* Homebrew: http://brew.sh/
* Virtualenv: http://docs.python-guide.org/en/latest/dev/virtualenvs/
* Flask: http://flask.pocoo.org/docs/0.10/quickstart/ (We use 0.9)
* Deploying Flash to Apache: http://flask.pocoo.org/docs/0.10/deploying/mod_wsgi/

Sample config:

    ✔ ~/workspace/selfservice-updated [master|…1454]
    22:26 $ cat app/config/*
    config.cfg:
       SECRET_KEY= "test"
    ldap.cfg:
       [Server]
       server=192.168.1.1
       port=500

       [Bind]
       user_cn = /bmays/
       user_pw = test

       [Search]
       timeout=10
       base=/base/cn
       sizelimit=100