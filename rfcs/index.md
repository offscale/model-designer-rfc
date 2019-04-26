%%%
title = "Model designer"
abbrev = "ODESIGN"
area = "Internet"
workgroup = "Offscale.io"
keyword = ["platform-independent"]
#date = 2019-12-07T00:00:00Z

[seriesInfo]
name = "RFC"
value = "ODESIGN0.0.1"
status = "informational"

[[author]]
surname="Marks"
fullname="Samuel Marks"
organization = "Sydney Scientific"
  [author.address]
  email = "samuel@offscale.io"
%%%

{mainmatter}

# Overview

[Offscale.io](https://offscale.io) is an open-source software-engineering consultancy, creating a number of open-source tools to speedup development (& facilitate multicluster and multicloud deployments).

We use [OpenAPI](https://github.com/OAI/OpenAPI-Specification) extensively.

## Compiler driven development (CDD)

In particular, we are writing compilers to translate:

- Swift to OpenAPI (and vice-versa) for iOS;
- Java to OpenAPI (and vice-versa) for Android;
- TypeScript & HTML to OpenAPI (and vice-versa) for web (with Angular);
- and Rust to OpenAPI (and vice-versa) for our [REST] API.

This will result in a huge speedup in development, as model changes can automatically propagate across—and within—language boundaries.

## Designers
Linking in perfectly with our [CDD plans](#name-compiler-driven-development), are designers for:

### OpenAPI
A design tool that will assist with OpenAPI authoring.

### SQL
A design tool that will assist with database schema design.

### Form-builder
A design tool that will assist with workflow design.

# Terminology

The key words "**MUST**", "**MUST NOT**", "**REQUIRED**", "**SHALL**", "**SHALL NOT**", "**SHOULD**", "**SHOULD NOT**", "**RECOMMENDED**", "**NOT RECOMMENDED**", "**MAY**", and "**OPTIONAL**" in this document are to be interpreted as described in BCP 14 [@!RFC2119] [@!RFC8174] when, and only when, they appear in all capitals, as shown here.

# Overarching goal
Along with [CDD](#name-compiler-driven-development), these interactive designers aims to facilitate end-users—e.g.: managers—with the ability to extend business software.

Imagine what a scalable web-based [Microsoft Access](https://products.office.com/en-au/access) would like like. Or [Google Forms](https://www.google.com.au/forms/about) on steroids.

Now take those ideas, and combine them with [BI](https://en.wikipedia.org/wiki/Business_intelligence) tools. Then take those, combined with multicloud and multiclustering, and now you have the full suite of Machine Learning/AI at the fingertips of nontechnical users.

By statically generating all the code, at any point any part of the system can be optimised by engineers. This includes simple things like changing the index type of a database table column, and more complicated concepts like caching, and composing complex workflows into single endpoints.

Once these systems are reasonably stable—if not before—everything will be released under permissive open-source licensing, such as MIT or Apache 2.0.

# Technology

All code must be written in a combination of HTML, CSS (or SCSS), and TypeScript; with the Angular 7 and Angular Material 7 frameworks.

## Drag-and-drop

All designers MUST be usable in a drag-and-drop interface. Angular Material now has a drag-drop functionality, use this.

## Import

All designers MUST be able to import in the same format it exports.

## Cross-platform

All code MUST be platform independent (or be [natively] buildable on: Linux, Mac, and Windows).

## Cross-browser

MUST support latest version of Firefox and Chrome.

## Responsive

MUST work on iPhone 6 up to 1920x1080 screen sizes; without vertical scrollbars. Consider using [ @angular/flex-layout](https://github.com/angular/flex-layout) for this. Review common approaches of collapsing columns into rows.

## Client-side

All code MUST run completely on the client side. There MUST NOT be any server, database, queue or what have you. You MAY use [Local Storage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) and/or similar built-ins.

Naturally, since we're in JavaScript land, you'll need a web server to serve this from. Using `ng serve` will suffice, but ensure `ng build --prod` succeeds.

### Future work
At some point in the future we will provide a stateful interface, enabling collaboration, storage and communication across all these projects.

## Best practices
Follow Angular best-practices as set by Google, including: avoidance of JQuery, and writing tests.

# OpenAPI designer

## Version

Build for [OpenAPI 3.0.2](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md)

## Export

MUST be able to export in YAML, and JSON (in [OpenAPI 3.0.2](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md) format)

# SQL designer

## Related work

Non-exhaustive list:

### Web

  - [WWW SQL Designer](https://github.com/ondras/wwwsqldesigner) (open-source)
  - [DBdiagram](https://dbdiagram.io/home)
  - [SQLdbm](https://sqldbm.com)
  - [QuickDBD](https://www.quickdatabasediagrams.com)
  - [Visual Paradigm](https://online.visual-paradigm.com/solutions/free-erd-software)
  - [Vertabelo](https://www.vertabelo.com)
  - [ERDplus](https://erdplus.com)

### Desktop

  - [Jeddict](https://jeddict.github.io/) (open-source)
  - [ERD-tool](https://www.softwareideas.net/en/erd-tool)
  - [Visual Paradigm](https://visual-paradigm.com/features/database-design-with-erd-tools)
  - [Idera ER/Studio Data Architect](https://www.idera.com/er-studio-data-architect-software/product-tour)
  - [Erwin data modeler](https://erwin.com/products/erwin-data-modeler/)
  - [IBM Rational Rose](ftp://public.dhe.ibm.com/software/rational/web/datasheets/2003/d187d-data-modeler.pdf) [now [Rational Rhaspody](https://www.ibm.com/au-en/marketplace/rational-rhapsody/details)?]
  - [System Architect](https://www.codebydesign.com)

### Discussion

These tools fit in the [Entity–relationship model](https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model) landscape, in at least the [Physical data model](https://en.wikipedia.org/wiki/Physical_data_model) area.

The OpenAPI and form-builder designers fit elsewhere.

### Conclusion

Many of these have good forward-engineering—to SQL—and reverse-engineering—from SQL—capabilities. Some—like DBdiagram & QuickDBD have their own text-based DSL also.

All have ways of visually creating new tables, CRUDing their fields, and display & making relationships.

## Interface
Be able to create many tables, using boxes like so:

~~~ ascii-art
+----------------------------+
| TABLE NAME                 |
+----------------------------+
| concept       | varchar(3) |
+----------------------------+
| amount        | smallint   |
+----------------------------+
| tbl0_key      | fk(tbl0)   |
+----------------------------+
| very_unique   | uuid4      | +
+----------------------------+
~~~
Figure: Single table

~~~ ascii-art
+----------------------------+
| TABLE NAME                 |
+---------------+------------+
| concept       | varchar(3) |
+----------------------------+
| amount        | smallint   |
+----------------------------+
| tbl0_key      | fk(tbl0)   +----+
+----------------------------+    |
| very_unique   | pk(uuid4)  | +  |
+---------------+------------+    |
                                  |
                                  |
                                  |
                                  |
                                  |
+-----------------------------+   |
| tbl0                        |   |
+--------------+--------------+   |
|  muh_key     | pk(uuid4)    +---+
+-----------------------------+
|              |              | +
+--------------+--------------+

~~~
Figure: Relationship

### Features

The system MUST be able to:

#### Vendor types
Postgres, MySQL, SQLite, MSSQL, &etc. all expose different types. in ISO/IEC 9075-1:2011.

#### Reorder schema types
Although reordering doesn't have any logical difference, it can make a different in system understanding [by humans].

#### Indexes, primary, and foreign keys
SHOULD be able to specify composite keys, index type

## Export

MUST be able to export in SQL, and JSON-schema formats.

## Drag-and-drop

The drag-drop interface MUST use Angular Material drag-drop functionality and design.

# Form builder
MAY take inspiration from [Google Forms](https://www.google.com.au/forms/about) or similar nontechnical user-oriented survey building tools.

## Angular Material components
MUST support ALL [Angular Material Components](https://material.angular.io/components/categories), paying particular attention to [stepper](https://material.angular.io/components/stepper/overview) for a [wizard style interface](https://en.wikipedia.org/wiki/Wizard_(software).

## Export
The following export formats MUST be provided.

### Angular Components in HTML & TypeScript
Output MUST be statically generated, there MUST NOT be any [reflection](https://en.wikipedia.org/wiki/Reflection_(computer_programming).

### JSON
Use a JSON-schema format, probably [Angular6-json-schema-form](https://github.com/hamzahamidi/Angular6-json-schema-form) is best. Models MUST be in an OpenAPI compatible format (JSON-schema, essentially).

Importantly, the YAML format SHOULD NOT be overly coupled with Angular, as the same YAML format MAY be used in the future to generate a similar visual experience in Java and Swift.

You MUST allow for logical operands, with minimum of `OR`, `AND`, `XOR` and `NOT`. This will enable design of a form like:

#### Example form workflow that logical operators allow
```
Q1: Are you from Russia?
A1.1: Yes
A1.2: No

// if A1.1
Q2: What part of Russia are you from?
A2: Moscow

// else if A1.2
> Non Russians are terrible. This incident has been recorded in our master database!
```

{backmatter}
