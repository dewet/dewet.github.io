---
layout:     post
title:      Java Using an Applet to Search an Array
date:       2014-11-21 09:05:01
summary:    Just going through very basic Login system, This was an assignment given to me a few days ago, I decided to blog it up because it is a great way to keep a tab on what I am doing at the moment.
categories: java assignments
---

### Screenshots of the program 
<br>
![login](http://i.imgur.com/d3nQQnb.png)<br>
![login-successful](http://i.imgur.com/HG1n7FO.png)<br>
![login-unsuccessful](http://i.imgur.com/Sxy6kzb.png)<br>

Okay, So now I have been presented with this code:


{% highlight java %}
	
	//Author: Ben de Wet
	
	public class Login extends Applet implements ActionListener{

	//Declaring variables
	String id, password;
	boolean success;

	//Create components for applet
	Label headerLabel = new Label("Please type your ID and Password");

	Label idLabel = new Label("ID:");
		TextField idField = new TextField(8);

	Label passwordLabel = new Label("Password:");
		TextField passwordField = new TextField(8);


	Button loginButton = new Button("Login");

	public void init(){
	
	//Set color, layout, and add components
	setBackground(Color.orange);

	setLayout(new FlowLayout(FlowLayout.LEFT,50,30));

	add(headerLabel);

	add(idLabel);
		add(idField);
		idField.requestFocus();

	add(passwordLabel);
		add(passwordField);
		passwordField.setEchoChar('*');

	add(loginButton);
		loginButton.addActionListener(this);
	}

	public void actionPerformed(ActionEvent e){
	success = false;

	//Sequential search

	}
} //end
{% endhighlight %}

It is a basic login page. Although it doesn't do anything.

So I have been asked to do two things.

<b>Part A</b> Create a Host Document.
<b>Part B</b> Create an Applet that Searches an Array to perform the task of logging in. (We will not be dealing with any sessions at the moment.)

### Part A, Using HTML to Host my Java Applet

