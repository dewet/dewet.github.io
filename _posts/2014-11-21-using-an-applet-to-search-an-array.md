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

<br>

{% highlight java %}
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
}
{% endhighlight %}

<br>

It is a basic login page. Although it doesn't do anything.

<br>

So I have been asked to do two things.

<b>Part A</b> Create a Host Document.
<b>Part B</b> Create an Applet that Searches an Array to perform the task of logging in. (We will not be dealing with any sessions at the moment.)

### Part A, Using HTML to Host my Java Applet

<br>

{% highlight html %}
<html>
<head>
	<title>
		Password Applet
	</title>
</head>
<body>
	<applet code="PasswordApplet.class" width="300" height="300">
		Password Applet
	</applet>
</body>
</html>
{% endhighlight %}

<br>

Now that we have created this host document, we can get started on the Applet.

### Part B, Creating the Applet

<br>

Okay, so firstly, we have been given a bunch of code already. But if I compile this, I get a bunch of errors. I'm going to have to import some packages.

{% highlight java %}
import java.awt.*;
import java.applet.*;
import java.awt.event.*;
{% endhighlight %}

<br>

That's better.

Okay, so what I am going to do first is create some Arrays for the <i>IDs</i> and corresponding <i>Passwords</i>.
You can name these whatever you want.

{% highlight java %}
	String idArray[] = {"id", "spicy", "manboy", "ultrasound", "venix"};
	String passwordArray[] = {"password", "skull", "badger123", "yoyo", "gom"};
{% endhighlight %}

<br>

We can just slip that in under the declared variables in our Login class.

and now all that we need to get this code working is a little bit of thought.

I am going to add these lines of code to make things a little easier on me.

{% highlight java %}
id = idField.getText();
password = passwordField.getText();
{% endhighlight %}

<br>

Now we are going to focus on the <i>actionPerformed()</i> method for now.

{% highlight java %}
public void actionPerformed(ActionEvent e)
	{
		success = false;

		//Sequential search

	}
{% endhighlight %}

<br>

The first thing I am going to do now if compare the <i>ID</i> and <i>Password</i> using this bit of code. By making <i>success</i>=<i>true</i>; if success = true, Login Successful, if success = false, Login Unsuccessful.
<br>
If the <i>Password</i> does not match the <i>ID</i>, the fields will reset.

{& highlight java %}
for(int i = 0; i<idArray.length; i++){
	if ((idArray[i].compareTo(id)==0) && (passwordArray[i].compareTo(password)==0)){
		success=true;
	}
	if(success==true){
		headerLabel.setText("Login Successful");
		repaint();
	}
	else{
		headerLabel.setText("Login Unsuccessful");
			idField.setText("");
    		passwordField.setText("");
    		repaint();
    	  }
}
{% endhighlight %}

and Voila.

## And we are done! 

Just take a look at that finished code!

{% highlight java %}
import java.awt.*;
import java.applet.*;
import java.awt.event.*;

public class Login extends Applet implements ActionListener
{
	//Declaring variables
	String id, password;
	boolean success;

	String idArray[] = {"id", "spicy", "manboy", "ultrasound", "venix"};
	String passwordArray[] = {"password", "skull", "badger123", "yoyo", "gom"};

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
      
		id = idField.getText();
		password = passwordField.getText();
      
	for(int i = 0; i<idArray.length; i++){
		if ((idArray[i].compareTo(id)==0) && (passwordArray[i].compareTo(password)==0)){
			success=true;
		}
		
		if(success==true){
			headerLabel.setText("Login Successful");
			repaint();
		}else{
			headerLabel.setText("Login Unsuccessful");
			idField.setText("");
			passwordField.setText("");
			repaint();
			}
		}
	}
}
{% endhighlight %}
