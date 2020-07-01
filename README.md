# Accessibility testing for SDG sites using Pa11y

## How to use

### Prerequisites

You need these installed before proceeding: 

⚠️ NOTE: You will probably need an off-network computer to be able install these

* Git - [install](https://git-scm.com/)
* Node JS - [install](https://nodejs.org/)

### 1. Setup

To setup accessibility testing, clone this repository and install all dependencies:

```bash
npm install -g yarn
git clone https://github.com/onsdigital/sdg-accessibilitytesting.git
cd sdg-accessibilitytesting
yarn
```

### 2. Configure

The next step is to tell the script which site and pages you'd like to test and what Pa11y configurations you'd like to have.

For this you'll have to edit 2 files: `pages.json` and `configurations.json`:

#### pages.json

`pages.json` is where you add your site's URL and the path of the pages you'd like to test. It should look like this:

```json
{
    "baseUrl": "http://localhost/sdg-indicators",
    "pages": [
        {
            "name": "Home",
            "path": "/"
        },
        {
            "name": "Reporting status",
            "path": "/reporting-status"
        },
        {
            "name": "Publications",
            "path": "/publications"
        },
        {
            "name": "FAQ",
            "path": "/faq"
        }
    ]
}
```

#### configurations.json

This is the file where you'll add any configurations. These are a list of [Pa11y Actions found here](https://github.com/pa11y/pa11y#actions). For example, change to a mobile screen or set to high contrast mode before testing:

```json
{
    "desktop": {},
    
    "highContrast": {
        "actions": [
            "click element .navbar ul.navbar-nav li.contrast-high a"
        ],
        "chromeLaunchConfig": {
            "args": ["--no-sandbox"]
        } 
    },
    
    "mobile": {
        "viewport": {
            "width": 320,
            "height": 480
        }
    }
}
```

### 3. Run tests

To run all the tests, run `yarn start` at the root directory of the project. It might take a few seconds for the reports to be generated.

### 4. See reports

To see the reports, open `.output/index.html` in your browser. You should see the list of all the pages you've run tests against:

![List of pages on the homepage](https://imgur.com/MoOTcRM.png)

Clicking on a link takes to the full test report for that page:

![Page report](https://imgur.com/YXqiJPQ.png)
