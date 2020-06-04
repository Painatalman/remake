

<img src="/remake-logo.gif" alt="Remake">
<br>
Make interactive web apps with only HTML
<p>
<a href="#get-started">Get started</a>·<a href="#learn-remake">Learn how to use</a>·<a href="https://requestcreative.com" target=_blank rel=_noopener>
  Try it live
</a>
</p>

## Table of contents

- [What sets Remake apart](#what-sets-remake-apart)
- [Get started](#get-started)
- [Learn Remake](#learn-remake)
  - [Learn by doing](#practical-tutorials)
  - [How Remake Works](#how-remake-works)
- [How to Contribute](#how-to-contribute)
  - [Contributors](#contributors)
- [Contacts and links](#stay-in-the-loop)

## What sets Remake apart

* **editable content** with just HTML
* **built-in CRUD** features
* **easy, intuitive and powerful syntax** for data handling
* **quick set up**, ideal for prototyping and rapid development
* native **hosting service**

To learn more about its features, check [Remake's official documentation](https://docs.remaketheweb.com/). 

## Get started
Step-by-step instructions on how to **set up a new project** with Remake. 

### 0 - Install prerequisites
To use Remake, you need to install:

1. **Node.js LTS 12.16.2+**(with npm 6). Both are available in the [official node.js package](https://nodejs.org/en/)
2. **Remake CLI**, installable via terminal, with npm:
```
npm install remake -g
```

### 1 - Create project
Use Remake CLI's **create** command to create a new Remake-powered project: 
```
remake create <project-dir>
```
Replace `<project-dir>` with the new project's name.

### 2 - Run project
Any newly-created Remake project provides a **custom script** (*dev*) to run the project through a **development server**.

To run the development server, you can **access the project folder** through the command line and run: 
```
npm run dev
```

You're now all set to implement your project.
Or maybe you'd like to [**learn more about Remake**](#learn-remake).

### 3 - (optional) Deploy Project

To deploy your app, go to its root folder and run:
```
remake deploy
```

## Learn Remake 

- (**Learn by doing**)[#practical-tutorials] (**Recommended for beginners**)- . Step-by-step examples to get started with Remake
- (**Learn how Remake works**)[#how-remake-works], to understand more advanced concepts and build larger projects 

## Practical tutorials
Beginner-friendly tutorials to get you started with learning Remake:

* [Build a todo list in 12 lines of HTML](https://docs.remaketheweb.com/a-simple-example-app/)
* [Build a Trello clone in 30 minutes](https://tutorials.remaketheweb.com/)

## How Remake works
> What if every HTML webpage knew how to save, edit, and add new items by itself?

Remake allows creating complete *web* apps **in record time and with minimum overhead**. Thus, anyone proficiennt in HTML, CSS, and [Handlebars](https://handlebarsjs.com/) can use it, with no back-end knowledge whatsoever. To achieve this, Remake comes built-in with:

- [**CRUD operations**](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete)
- **automatic data saving** after editing content
- **flat file database** system that doesn't require any configuration
- **user account management** 
- **simple API for data handling** that facilitates accessing and saving nested objects

### How Remake Works - Data Handling

> HTML is formatted like a tree 🌳: it has a root (the parent element) and children linked to it (child elements).

<!-- todo: make a diagram -->
Remake **tags HTML elements to data** by looking into their position on the page. To tag data to elements, Remake checks for **custom data attributes** for input and output.

### How Remake Works - Input data attributes

Input data attributes are used to edit data. They're always prefixed with `data-i-`. 
There are **two attributes with specific purposes**:

- `data-i-editable` enables **editing and saving** data
- `data-i-new` sets a template for newly-created elements of a specific type

#### Examples - Input data attributes
<!-- todo: add examples -->

### How Remake Works - Output data attributes

Output data attributes tag an element to specific data. They're always prefixed with `data-o-`.
Elements tagged to output data **require a `data-o-type`** attribute, whose value can be either "object" or "list", depending on the data's nature.

Here's a simple example:

```html
<div data-o-type="object"></div>
```
In this example, the `div` has been tagged as an `Object`. Thus, Remake will convert it into:

```javascript
{}
```

But this is just an example with a basic object. Let's go through a few more examples.

#### Example 1 - Key/value pairs

```html
<div data-o-type="object" data-o-key-name="David"></div>
```

This will be converted into an object with a key/value pair inside of it:

```javascript
{name: "David"}
```
Here's an explanation of what happened:

- the first attribute (`data-o-type`) tells us which data type to expect. It can be set to *only* `object` or `list`
- the second attribute (`data-o-key-name`) tells us that this `object` has a key of `name`, whose value matches the attribute's value ("David", in this case).

#### Example 2 - Nested data

```html
<div data-o-type="object">
  <div data-o-type="object" data-o-key="person" data-o-key-name="David">
    </div>
</div>
```

This example is a bit more advanced, as it relies on **nested** elements to create nested data:

```javascript
{person: {name: "David"}}
```

In this example, we use the `data-o-key` attribute — with nothing after it — to create an object inside of an object. The value of `data-o-key` tells us which key the nested object will be.

Hence, the resulting **data matches its element's structure**.

#### Example 3 - Lists/Arrays of objects

Let's look at the only other data type that Remake supports: `Arrays`. In Remake, we use the term `list`.

How do we create a list in Remake?

```html
<div data-o-type="list"></div>
```

This is a pretty simple example and will compile into just a simple, empty array:

```
[]
```

How would we go about adding objects to this array? We'd just nest them of course!

```html
<div data-o-type="list">
  <div data-o-type="object" data-o-key-name="David">
  <div data-o-type="object" data-o-key-name="John">
  <div data-o-type="object" data-o-key-name="Mary">
</div>
```

When Remake looks at this, all it sees is:

```javascript
[
  {name: "David"},
  {name: "John"},
  {name: "Mary"}
]
```

## How to contribute

You can help us improve Remake by:

- reporting or fixing bugs
- requesting features
- updating documentation
- refactoring code

<!-- TODO: add link to issue list -->
So feel free **to file an issue**, and we'll provide you feedback as soon as possible!

### Contributors

We have to thank these fellows for all their help in (Re)making this project:

- **[Andrew de Jong](https://gitlab.com/android4682)**

## Stay in the loop

Sign up for [our newsletter](https://form.remaketheweb.com/) to get updates as this framework develops. 

Additionally, feel free to: 

* [visit Remake's official website](https://remaketheweb.com/)
* [follow panphora (Remake's creator) on Twitter](https://twitter.com/panphora)
* [View Remake's public roadmap on Trello](https://trello.com/b/BXvugSjT/remake)







