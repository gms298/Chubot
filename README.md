# Chubot

Chubot is a chat bot in the Slack platform, for REST-API programmers. Chubot is programmed in **node JS**, runs on the **slack** platform and uses **POSTGRES-SQL** databases. 

## Index

1. [Video Presentation](#video)
2. [Introduction](#problem)
3. [Primary Features & Screenshots](#primary)
4. [Limitations and future work](#limit)
5. [Deployment](#deploy)

## <a name="video"></a>Video Presentation

[Here](https://youtu.be/snKSAnZ-YiE) is a link to the video presentation, demonstrating the entire project.

## <a name="problem"></a>Introduction
Often developers use REST API requests in their projects when interacting within a platform. For example, many use Github - REST API requests to interact with Github for their version control or source code management needs. Coding REST-API requests into large projects/automated processes requires referring lengthy pages of online documentation to find the proper code-syntax or to find definitions of headers/parameters used in the REST API requests. More importantly, this process is often redundant when developers write lots of similar API requests in their projects. Hence, this process is time consuming for developers and provides an opportunity for automation. 

Automating this process using a bot saves a lot of time and helps reduce developer frustration. This also frees the developer from opening many browser windows to refer documentation materials online, thereby clearing a lot of clutter on the developer’s desktop.

Chubot is a chat bot that assists it's users (software developers) by having conversations with them. Chubot has the following important functions:

  1. It automates the process of searching a platform's support documentation for a code-syntax (or) skeleton code of a REST-API operation/function.
  2. It finds definitions and explanations of REST API headers/parameters (Eg: JSON headers used in GET/POST methods). 
  3. It also sets required header values in the replies (node.js function code for a REST API operation), if specified by the user.
  
A developer can simply ask chubot for a specific REST-API request code and chubot will reply with a link to a Github gist containing the requested code in the form of a node.js function. Hence, chubot may be classified as a support bot.

## <a name="primary"></a>Primary Features & Screenshots

Chubot supports Github and Wordpress platforms as of version 1.0 and can be explanded into other REST-API compatible platforms in furture versions.

### Features

Chubot has three primary features:

  1. Saving a user's username, token and the API URL for a platform (currently Github & Wordpress).
  2. Generating a node.js function for a REST API request which is then posted as a Github gist.
  3. Providing definitions for headers/parameters used in REST API requests.

### Screenshots

#### Feature #1

![1](https://cloud.githubusercontent.com/assets/22831490/20863626/c63d6ee8-b99e-11e6-9101-b01f4e5ae2dd.GIF)

This screenshot shows chubot saving a user's Github and WordPress token. Later, chubot replaces the token values in the generated node.js functions (Feature #2) with this value. Similarly, the user can store their username and URL for every platform supported by chubot.

#### Feature #2

**PART 1: NO PARAMETERS IN REQUEST**

![2](https://cloud.githubusercontent.com/assets/22831490/20863627/c63db290-b99e-11e6-93a8-d93c95bd86bc.GIF)

This screenshot shows a user asking Chubot for the code to a function which can list all comments in WordPress. Chubot generates the function and posts it as a Github gist and then returns the URL of the gist to the user with a small preview of the function.

#### Gist containing the generated code

![5](https://cloud.githubusercontent.com/assets/22831490/20863684/d9611c02-b9a0-11e6-81dd-4de1dd632cf4.GIF)

**PART 2: MULTIPLE PARAMETERS IN REQUEST**

![3](https://cloud.githubusercontent.com/assets/22831490/20863628/c63e473c-b99e-11e6-919f-0c0d02fb1919.GIF)

This screenshot shows a user asking Chubot for the code to a function which can list issues in a Github repo. It should be noted that the user has passed values for two parameters in the GET request. This informs chubot to set the passed values to the appropriate headers/parameters when generatng the code for the node.js function. As earlier, chubot responds with the gist URL along with a small preview.


#### Gist containing the generated code

![6](https://cloud.githubusercontent.com/assets/22831490/20863685/d964f07a-b9a0-11e6-8c54-9d677ad5fc21.GIF)

It can be seen that Chubot has replaced the default value for `state` and `sort` parameters with the values that were passed in the user's request message.

#### Feature #3

![4](https://cloud.githubusercontent.com/assets/22831490/20863629/c63ea786-b99e-11e6-9e76-09160347fa19.GIF)

This screenshot shows a user asking Chubot to define the parameter `has_issues` and Chubot responding with the Name, Type and Definition of `has_issues`.

### <a name="limit"></a>Limitations and future work

One limitation is that Chubot doesn't verify the validity of the token provided by the user. It simply accepts the token values specified by the user and replaces it with the default values in it's code generation process.

Currently Chubot (v1.0) supports REST API requests in Github and WordPress only. Future work can be focused on including support for other REST API compatible platforms. This can be done **without modifying** chubot's implementation (code) and **just adding** required documentation records in the database.

Lastly, there is one more area that could be addressed in the future and that is the storage of skeleton code (used in the function code generation process) in the database. Currently the skeleton code for each function is directly inserted into the database (for each REST API request) and they are not dynamically generated although the parameters alone are dynamically modified. In the future, Chubot can be programmed to include artificial intelligence methods to support this feature. Addition of one or more database tables may be needed for mapping each REST API request to it's parameters and this should be sufficient to allow complete dynamic code generation.

### <a name="deploy"></a>Deployment

Chubot was deployed into Amazon Web Services EC2 instance using an [Ansible Playbook](https://github.com/gms298/Chubot/tree/master/Deployment%20scripts). 

