# ShaneBow Content Management System

## Overview
The [*ShaneBow Content Management System* (CMS)](https://shanebow.com/page/show/advanced-cms) grew out of a need to be able to demonstrate code and web site templates online.

It is written for a coder in that it uses [*Markdown*](/page/show/markdown) for the main content of a page but also allows for scripts to be included at the bottom of the page.

It also supports the creation of [*manifests*](/page/show/cms-manifest) which provide the data for applications. 

These pieces work together to make this CMSy flexible and powerful:

*   [Pages](https://github.com/ShaneBow-CMS/pages) A *page* can be a blog post, a lesson plan. a chapter of a book, site policies, or anything else you can think of to publish on the web
*   [Templates](https://shanebow.com/page/show/cms-templates) are the available layouts for the pages. 
*   [Categories](https://github.com/ShaneBow-CMS/cats) allow pages to be grouped into a tree hierarchy
*   [Manifests](https://github.com/ShaneBow-CMS/manifests) provide data to applications - They are like a data-set stored with a title, description, and other meta.
*   [Tags](https://github.com/ShaneBow-CMS/tags) are a way of specifying that a page touches on some topic. Tags are different from categories in that a page can have multiple tags, but only one category.
*   [Media](https://github.com/ShaneBow-CMS/media), usually pictures or video, that can be inserted into pages. The media manager facilitates tracking copyright and provides a way todata give each item a title and description. Note that media is not limited to pictures, but can include any MIME type for which an interface has been written

To get a quick feel for how these features help the developer, consider an educational site. Let's say we write an app where
 users drag vocabulary words and drop them on a picture. We would write the app in a single page then put each picture with
 it's vocabulary into a manifest.

The app could present a list of the manifests (i.e. pictures to label) for the user to choose from.

We could also make a template shared by all the courses, and then make a page for each individual course.
 The lessons, quizzes, and activities would reside in individual manifests.

### Why not put the lessons into pages rather than manifests?
You could — these is some overlap in the functionality of pages and manifests. One key difference is that manifests are
 stored separately from the page hierachy, and are *not* searchable by the end user: This may or may not be the desired
 behavior for individual lessons.

This document is primarily directed at the end user, however, there are [setup notes in the sidebar](#setup).

## CMS Setup
The CMS has the following dependencies, which must be installed prior to the CMS

*   Categories subsystem
*   Media subsystem
*   Tags subsystem
*   Users subsystem

File/Location|Description
-------------|-----------
constants.php<br>application/config|Must include ~~cms/pages/config/constants.div
form_validation.php<br>application/config|Must include ~~cms/pages/config/form_validation.php.div
Page.php<br>application/controllers|Main Page controller
Macro.php<br>application/controllers|Controller for Page Editor macros
Mpages.php<br>application/models|Main model for page data
Mmacros.php<br>application/models|Model for Page Editor Macros
tbl-pages.sql<br>application/models/tbls|Definition for page DB
tbl-pages.sql<br>application/models/tbls|Definition for page macros DB
layouts.csv<br>application/models/tbls|CSV file with `tmpl`,`name` columns where `tmpl` is the template file name without the `tmpl-` prefix nor `.php` extension and `name` is a user friendly name the
Csv.php<br>application/libraries|CSV library required for template list
Markdown.php<br>application/libraries|Markdown library required page content
tmpl-*.php|application/views|User created template files
page-editor.php<br>/application/views/admin|Page Editor user interface
page-table.php<br>/application/views/admin|Page List user interface
page-macros.php<br>/application/views/admin|Page Editor Macros user interface
