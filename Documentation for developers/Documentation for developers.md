# Documentation for developers

## Introduction

Documentation for the developer is one of the most important parts of the project; it will help speed up the onboarding of the project or the flow in which the developer will work and can increase the level of understanding of the code.

Using the sections described below you can understand what your documentation may include.

Sections of Documentation:
- **Installation and launch of the project** \
  its configuration and interaction methods
- **Description of the technical requirements of the project** \
  what rules developers must follow, and what problems these rules solve
- **List of libraries and dependencies used** \
  description of the purpose of each library
- **Description of the project structure** \
  location of folders and files, description of the rules by which the developer must edit this structure
- **Description of specific flows or custom modules** \
  methods of working with these flows (or modules), their technical structure and execution
- **Recommendations for improving documentation**

## Installation and launch of the project

There should always be a description of the installation and launch of the project. The detail in the description of this chapter determines how often a new developer will turn to experienced developers due to problems with installation, updating, or launching a project.

As a rule, this section of the documentation should describe how and from where the developer should install the project. \
For example, "run in console `git clone git@github.com:...`"

This and subsequent points may vary depending on the project and technology. I suggest looking at an example of such documentation below and thinking about what questions the reader might have and what needs clarification

> First, clone the Git repository using the console with the following command `git clone git@github.com:...` \
> Next, go to the root folder of the cloned repository using the same console or IDE and run `npm install` to install required dependensies \
> Launch the project using `npm start` \
> Open `http://localhost:3000` with your browser to see the result

At first glance it seems that everything is simple and clear, but I would like to clarify a few points

1. Which method should I use to clone a repository? **SSH, HHTPS, Some CLI**? \
   For example, if security is a priority for the project, you should specify that developer need to use SSH
   > First, clone the Git repository using the console with the following command `git clone git@github.com:...` \
   > **Please use only the SSH method to clone the repository and interact with it securely**
2. Does it matter what I use, **npm** or **yarn**? Does **npm** or **yarn** version matter? If I don't have these programs, where is the best place to download them? \
   Accordingly, it should be clarified that it is necessary to use or can use a program of the developer’s choice. It may also be worth leaving a link to download the program and clarify the required version
   > Next, go to the root folder of the cloned repository using the same console or IDE and run `npm install` to install required dependensies \
   > **Use npm exclusively. (yarn will not work) If you don't have it, you should download node.js from this link. `https://nodejs.org/en/download` \
   > But it's better to install nvm. This program is used on a project to use a specific version of node.js and npm. \
   > You can install it and run `nvm use` in the root of the project to use necessary version of node.js and npm**

Perhaps the example is boring and redundant, but I hope you get the point. To the previous points, I will add that when writing such documentation, you should ask yourself “What questions may the reader have and how to answer them.” \
Just as the developer who assembled this project or has been developing it for a long time, you might encounter difficulties in installing and launching it, do not be lazy to describe these difficulties in this document. \
For example, these could be errors related to the architecture of the ARM or x86 device. \
Describe in the documentation under what circumstances you encountered the problem, how it manifested itself, and how you resolved it. \

You can also add to this section of the documentation what a developer should do to push/deploy changes

## Description of the technical requirements of the project

In this section of the documentation, you can describe what requirements the client put forward for the project, or the technical methodologies that the developers follow for some reason.

To write such a list, you must identify what methodologies/principles you are using or intend to use and determine the rationale for using them. \
By justifying the use of a particular rule, you give the reader more understanding of the problems you encounter on the project and how you solve them.

Below is an example of such a list:
> - We use the **Mobile First** principle as our project is designed for phone, tablet and desktop. \
>   This principle helps phone users quickly get a content of the application and start interacting with it using less computing power.
> - We use the **BEM** methodology to write application styles. \
>   This helps us navigate styles more easily and avoid bugs with accidental reuse of styles.
> - We also use the **SOLID** principle to write the functionality of objects and entities. \
>   This helps us avoid bugs and have clearer methods of interacting with application logic

There are not many examples in the list above, but as a reader we can draw some conclusions. For example, the fact that the application has several versions for different devices and that the Mobile First principle is used. If the reader is a developer, he will already have an idea of the code before he starts looking at it. The developer will also understand exactly how to edit and add application styles

## List of libraries and dependencies used

In this section of the documentation you can describe the list of technologies/libraries/dependencies that you use for the project \
Also, if the technology is not obvious or popular, it is worth indicating the purpose of its use

Below is an example of such a list:
> - **react** v18
> - **react-router-dom** v6
> - **mobx** v6 - using for manage application data and manipulate it
> - **sass** v1
> - **typescript** v5
> - **yup** v1 - using for form validations
> - **dayjs** v1 - using to manipulate with date's easier

Note! Don't list all the dependencies, their versions, and don't come up with a description for each one. \
Indicate the main and specific technologies and their major versions (Major versions are most remembered by developers and contain differences in use) \
Your main task is to describe it as simply as possible. The developer will be able to open the code and learn about the technologies in more detail, and sometimes it is important for the project manager or client to know what you are using on the project, and it will be easier for them to understand if there is nothing superfluous

## Description of the project structure
This section of the documentation should contain a basic map of the project and help a new developer navigate files

Below you can see an example of such a map based on the **react** application:
> `/public` - folder with public files and media files \
> `/src` - root folder of app code
> > `/index.tsx` - root file of **react** application \
> > `/App.tsx` - root file of **react** components \
> > `/elements` - folder of **react** pure components *(Logic of components depends only from props)*
> > > `/[ElementName]` - example of component folder
> > > > `/index.ts` - element root file which exports component and all public methods of it \
> > > > `/[ElementName].tsx` - file which includes component code and logic \
> > > > `/[ElementName].module.scss` - file which includes component styles \
> > > > `/[ElementName].types.ts` - file which includes component **typescript** types and interfaces used in component file
> > 
> > `/components` - folder of **react** components *(Logic of components can contain some api requires or store state manipulation)*
> > > `/[ComponentName]` - example of component folder
> > > > `/index.ts` - element root file which exports component and all public methods of it \
> > > > `/[ComponentName].tsx` - file which includes component code and logic \
> > > > `/[ComponentName].module.scss` - file which includes component styles \
> > > > `/[ComponentName].types.ts` - file which includes component **typescript** types and interfaces used in component file

This map shows the basic structure of a react application, but it may contain more useful directories.
For example, you can specify in which folder or file the functions for the API request are stored \
This map also shows by what principle developers name files in `/elements` and `/components` folders

As with dependencies, do not describe all project files. Describe the basic structure and possibly complex directories (the purpose of which is not obvious)

## Description of specific flows or custom modules

> In progress

## Recommendations for improving documentation

In addition to the above sections, I will add a few tips to improve the documentation:
- Over time, any documentation may become outdated and lose its value. To avoid this, developers should update it. If you can't update documentation frequently, the best time to update it is when you're refactoring your code, finishing some flow, adding a new feature, or changing dependencies or project requirements. You can also set a period after which the documentation needs to be checked and updated (For example, every month or a longer period)
- When writing or updating documentation, try to think like a reader who knows nothing about this project, this will help you focus on the complex unknowns of your project. The ideal option would be to let a developer who is not familiar with your project view the documentation.
