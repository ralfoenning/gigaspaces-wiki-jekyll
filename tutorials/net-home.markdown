---
layout: post
title:  Full .NET Tutorial
categories: TUTORIALS
parent: dotnet-quick-start-guide.html
weight: 400
---


{%summary%}This tutorial will introduce you to the basic features of GigaSpace's XAP platform.{%endsummary%}

# Overview

This Tutorial provides a high-level overview of the GigaSpaces XAP platform. Hands on examples are provided to demonstrate the core concepts and API's. The primary people who can benefit from this tutorial, are architects and developers who wish to build scaled-out applications with GigaSpaces XAP.


# Class Model
Throughout this tutorial we will create and use a simple internet payment service application to demonstrate the basic XAP features. The basic concept of our application;

- Merchants enter into a contract to handle financial transactions using the application.
- The Merchant will receive a percentage for each transaction.
- Users will make payments with the online system.

Here is the simplified Class Model:

{%indent %}
[<img src="/attachment_files/qsg/class_diagram.png" width="200" height="140">](/attachment_files/qsg/class_diagram.png)
{%endindent%}
 

{%comment%}
| witdh=300px, height=300px!
{%endcomment%}

{%comment%}
You can download all examples presented here from [GitHub](https://github.com/Gigaspaces/xap-tutorial). Feel free to clown, fork and contribute to the tutorial code.

# Let's get started

{%panel%}
- Download and unzip the latest XAP release from the [downloads page](http://www.gigaspaces.com/xap-download)
- Unzip the distribution into a working directory; GS_HOME
- Set the JAVA_HOME environment variable to point to the JDK root directory
- Start your favorite Java IDE
- Create a new project
- Include all files from the GS_HOME/lib/required in the classpath
{%endpanel%}

{%endcomment%}


# Tutorial Trail


{%comment%} ==============================================================Part I  {%endcomment%}

{% panel borderStyle=solid|borderColor=#3c78b5|bgColor=white %}
{%section%}
{%column width=20% %}

{%align center%}
[Part I](./net-tutorial-part1.html)

<img src="/attachment_files/qsg/data.png" width="100" height="100">

{%endalign%}
{%endcolumn%}

{%column width=75% %}
{%align center%}**Interacting with the Space**{%endalign%}
This part of the tutorial will introduce you to the space as a data store.

You will learn how to:

- create a space
- write objects into the space
- querying the space
- indexing objects in space

{%align right%}{%learn%}./net-tutorial-part1.html{%endlearn%}{%endalign%}
{%endcolumn%}
{%endsection%}
{%endpanel%}



{%comment%} ==========================Part II ====================================
Part II
{%endcomment%}

{%panel borderStyle=solid|borderColor=#3c78b5|bgColor=white %}
{%section%}
{%column width=20% %}
{%align center %}
[Part II](./net-tutorial-part2.html)

<img src="/attachment_files/qsg/grid.gif" width="100" height="100">
{%endalign%}
{%endcolumn%}

{%column width=75% %}
{%align center%}**Deploying a Space**{%endalign%}
In this part of the tutorial we will show you how you can deploy an In Memory Data Grid (IMDG) that provides scalability and failover.

You will learn how to:

- start a data grid
- deploy a data grid
- interact with the data grid
- how to use the administration UI

 {%align right%}{%learn%}./net-tutorial-part2.html{%endlearn%}{%endalign%}
{%endcolumn%}
{%endsection%}
{%endpanel%}

{%comment%}============================ Part III ==================={%endcomment%}
{%panel borderStyle=solid|borderColor=#3c78b5|bgColor=white %}
{%section%}
{%column width=20% %}
{%align center %}
[Part III](./net-tutorial-part3.html)

<img src="/attachment_files/qsg/processing.png" width="100" height="100">
{%endalign%}
{%endcolumn%}

{%column width=70% %}
{%align center%}**Processing Services**{%endalign%}
In this part of the tutorial we will introduce you to the different processing services you can run on top of the space.

You will learn how to use:

- Executor service
- Remoting service


{%align right%}{%learn%}./net-tutorial-part3.html{%endlearn%}{%endalign%}

{%endcolumn%}
{%endsection%}
{%endpanel%}


{%comment%}============================ Part IV ==================={%endcomment%}

{%panel borderStyle=solid|borderColor=#3c78b5|bgColor=white %}
{%section%}
{%column width=20% %}
{%align center %}
[Part IV](./net-tutorial-part4.html)

<img src="/attachment_files/qsg/Events-Message.png" width="100" height="100">
{%endalign%}
{%endcolumn%}

{%column width=70% %}
{%align center%}**Events and Messaging**{%endalign%}
In this part of the tutorial we will introduce you to events and messaging on top of the space.

You will learn how to use:

- Notify container
- Polling container

{%align right%}{%learn%}./net-tutorial-part4.html{%endlearn%}{%endalign%}

{%endcolumn%}
{%endsection%}
{%endpanel%}


{%comment%}============================ Part VI ==================={%endcomment%}

{%panel borderStyle=solid|borderColor=#3c78b5|bgColor=white %}
{%section%}
{%column width=20% %}
{%align center %}
[Part VI](./net-tutorial-part6.html)

<img src="/attachment_files/qsg/transaction.png" width="100" height="100">
{%endalign%}
{%endcolumn%}

{%column width=70% %}
{%align center%}**Space Transactions**{%endalign%}
In this part of the tutorial we will introduce you to the transaction processing capabilities of XAP.

You will learn about:

- Transaction managers
- Transaction processing
- Concurrency
- Locking

{%align right%}{%learn%}./net-tutorial-part6.html{%endlearn%}{%endalign%}

{%endcolumn%}
{%endsection%}
{%endpanel%}