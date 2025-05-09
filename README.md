# Interview Preparation Guide

## How to test locally

### Pre-req's

1. Install Python3, follow the guide here if you havent got python3 on your machine https://docs.python-guide.org/starting/install3/osx/

2. use pip3 (installed as part of step 1) to install virtuenv

```
pip3 install virtualenv

or

pip3 install virtualenv --user
```

3. Go into the directory where you cloned the repo (developer-portal), Create a virtualenv

```
virtualenv venv
source venv/bin/activate
```

4. Install mkdocs and requirements
```
pip3 install -r requirements.txt
```

5. Start the server
```
mkdocs serve -a 0.0.0.0:8000
```

6. browse the site under http://localhost:8000

7. To Deploy 
```
mkdocs gh-deploy
```