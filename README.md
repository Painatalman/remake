<img src="/remake-logo.gif" alt="Remake">
Build interactive websites with only HTML
<p>
<a href="#get-started">Get started</a>
  ·
  <a href="#learn-remake">Learn how to use</a>
  ·
  <a href="https://requestcreative.com" target=_blank rel=_noopener>
  See a demo
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
> What if every HTML webpage knew how to save, edit, and add new items by itself?

Remake allows creating feature-rich websites **in record time and with minimum overhead**, with no back-end knowledge whatsoever:

* **Editable content** with just HTML, thanks to *built-in* [CRUD operations](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete)
* **Easy, intuitive and powerful syntax** for data handling

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
To run your project with a server, go to its folder and run **dev** (a custom script already included in package.json): 

```
cd <project_folder>*
npm run dev
```

*<project_folder> is the path to project's folder
### 3 - Start implementing

You're now all set to implement your project.
You can edit your project's code in the **app folder**, where you'll find:
 - #TODO
 - #TODO
 - #TODO
 
Or maybe you'd like to [**learn more about Remake**](#learn-remake).

### 4 - (optional) Deploy Project

> **NOTE** You need to [set up an account]() first 

To deploy your app, go to its root folder and run remake CLI's deploy command:

```
cd <project_folder>*
remake deploy
```
Congrats, you can now share your project with the world through its custom subdomain! 

*<project_folder> is the path to project's folder
## Learn Remake 

To learn Remake, all you need is basic knowledge in HTML, CSS, and [Handlebars](https://handlebarsjs.com/).
You can then follow one of our **practical tutorials** to learn the basics of Remake while you build a project:

* [Build a todo list in 12 lines of HTML](https://docs.remaketheweb.com/a-simple-example-app/)
* [Build a Trello clone in 30 minutes](https://tutorials.remaketheweb.com/)

And fully understand the concepts behind Remake, feel free to check out (**how Remake works**)[#how-remake-works].  

## How Remake works

> HTML is formatted like a tree 🌳: it has a root (the parent element) and children linked to it (child elements).

<!-- todo: make a diagram -->
Remake **tags HTML elements to data** by looking into their position on the page. To tag data to elements, Remake checks for **custom data attributes** for input and output.

### How to input data

Input data attributes are used to edit data. They're always prefixed with `data-i-`. 
There are **two attributes with specific purposes**:

- `data-i-editable` enables **editing and saving** data
- `data-i-new` sets a template for newly-created elements of a specific type

### Examples - Input data attributes
<!-- todo: add examples -->

### How to export data

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

You can join our [list of contributors] by:

- [Reporting bugs](https://github.com/panphora/remake/issues/new?assignees=&labels=&template=bug_report.md&title=)
- [Requesting features](https://github.com/panphora/remake/issues/new?assignees=&labels=&template=feature_request.md&title=)
- [Fixing an issue](https://github.com/panphora/remake/issues) -- don't forget to assign them to you first!

## Stay in the loop

Sign up for [our newsletter](https://form.remaketheweb.com/) to get updates as this framework develops. 

Additionally, feel free to: 

* [Remake's official website](https://remaketheweb.com/)
* [Panphora's Twitter](https://twitter.com/panphora)
* [Remake's public roadmap on Trello](https://trello.com/b/BXvugSjT/remake)







