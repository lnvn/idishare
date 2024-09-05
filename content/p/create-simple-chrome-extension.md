+++
title = 'Create Simple Chrome Extension'
summary = 'Describe how to build a simple chrome extension to block access to facebook, youtube, instagram, ...'
date = 2024-08-04T19:48:25+07:00
draft = false
+++

- [I. Overview](#i-overview)
- [II. Getting Started](#ii-getting-started)
  - [1. What is chrome extension ?](#1-what-is-chrome-extension-)
  - [2. Create Extension](#2-create-extension)
    - [Folder structure:](#folder-structure)
    - [manifest.json](#manifestjson)
    - [style.css](#stylecss)
  - [3. Apply Extension](#3-apply-extension)
  - [4. Reference](#4-reference)

## I. Overview
In this article, I will share how to create a simple chrome extension to block access to some social media website. We do that to add one more security layer :) to prevent us from wasting time on screen too much
## II. Getting Started
### 1. What is chrome extension ?
Extensions are small software programs that customize the browsing experience. They enable users to tailor Chrome functionality and behavior to individual needs or preferences. They are built on web technologies such as HTML, JavaScript, and CSS.

### 2. Create Extension
#### Folder structure:
```
web-blocker
├── css
│   └── style.css
├── images
│   └── icon.png
├── manifest.json
└── README.md
```

We will focus on two main file are "manifest.json" and"style.css", you may need to create or download an image (E.g icon.png) if you wanna custom your extension icon.

#### manifest.json

Chrome’s manifest.json file is a JSON-formatted file that serves as the core configuration file for a Chrome extension. It provides essential metadata and functionality information to Chrome, enabling the extension to interact with the browser and perform various tasks.

```
{
    "manifest_version": 3,
    "name": "Block Site",
    "description": "Use to block access to facebook, youtube, ... Save your time!!!",
    "version": "1.0",
    "content_scripts": [
        {
          "matches": [
            "https://www.facebook.com/*",
            "https://www.youtube.com/*",
            "https://www.netflix.com/*",
            "https://www.24h.com.vn/*",
            "https://www.instagram.com/*"
          ],
          "css": [
            "css/style.css"
          ]
        }
      ],
    "icons": {
        "128": "images/icon.png"
    }
  }
```

- **manifest_version**: Specifies that this is a manifest version 3 (latest)
- **name**: The name of the extension
- **description**: A brief description of what the extension does
- **version**: The version of the extension
- **content_scripts**: This section specifies scripts and CSS to be injected into web pages that match the URLs in the "matches" array
- **matches**: An array of URL patterns for the sites you want to block. When a user visits any of these sites, the specified CSS will be applied.
- **css**: An array of CSS files to be injected
- **icons**: Specifies the icon for the extension, with a 128x128 pixel image

#### style.css

contain the styles that will block or alter the appearance of the matched websites.
```
* {
    box-sizing: border-box;
    color: #fff;
    font-family: monospace;
    font-size: 5vw;
    font-weight: bold;
    text-align: center;
  }
  
  html {
    background: radial-gradient(68.34% 50% at 50% 50%, #2D9AFF 0%, #41DEE8 0%, #A22DFF 100%);
    height: 100vh;
    padding: 50px 30px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  html::before {
    content: '!! Stop !!';
  }
  
  body {
    display: none !important;
  }
```

### 3. Apply Extension
- **Step 1**: Go to `chrome://extensions/` in your Chrome browser.
- **Step 2**: Enable "Developer mode" in the top right corner.
- **Step 3**: Click "Load unpacked" and select the directory containing your manifest file and other assets.

The extension should now appear in your list, and the specified sites should be blocked according to the CSS when visited.

### 4. Reference
- https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world

TBD: add enable/disable button, design extension popup