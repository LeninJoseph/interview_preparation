# Interview Preparation Guide
#

## Directory structure

Home
Authentication
    - Introducion
    - SAT
Platform
    - Init
    - Offers
    - Cart
    - Consent
    - Purchase
    - Poll Order status
    - Get Activation Url
    - Subscriptions
        - Get subscription
        - Re - subscribe
        - Un - subscribe

Support
    - Frequently Asked Questions
    - Contact

## How to contribute

1. Close the repository

```
git clone git@github.comcast.com:sales-rpil/shopfront-dev-portal.git
```

2. Familiarize yourself on the structure of content inside markdowns folder

3. Update content that is related to you

4. Test it locally before you commit the changes ( see test in local section )


## Writing content

The developer portal content is written in mark down, Reference https://www.mkdocs.org/user-guide/writing-your-docs/ should provide the details
on how to write content.

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