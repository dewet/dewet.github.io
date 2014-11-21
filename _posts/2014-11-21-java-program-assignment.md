---
layout:     post
title:      Java Checker board Assignment
date:       2014-11-21 01:01:01
summary:    This is me attempting to create a checker-board Java application. This is an assignment that I have to complete. This is just a run down of what I have done/am doing.
categories: java assignments
---

This is going to be a post on creating your very own Checker board.
I am going to program this step by step.

### Creating the application
First I am going to need to import some packages and create my Checkerboard class.

{% highlight java %}
import java.awt.*;
import java.awt.event.*;

public class Checkerboard extends Frame implements ActionListener{}
{% endhighlight %}

Next, I am going to declare some variables.

{% highlight java %}
import java.awt.*;
import java.awt.event.*;

public class Checkerboard extends Frame implements ActionListener{
	int start, stop, step;
	
	Panel blockPanel = new Panel();
		TextArea blockDisplay[] = new TextArea[16];
		
	Panel fieldsAndLabels = new Panel();	
		TextField startField = new TextField(5);
		TextField stopField = new TextField(5);
		TextField stepField = new TextField(5);
		
		Label startLabel = new Label("Start");
		Label stopLabel = new Label("Stop");
		Label stepLabel = new Label("Step");
	
	Panel buttonPanel = new Panel();
		Button goButton = new Button("GO!");
		Button clearButton = new Button("Clear.");
	}
{% endhighlight %}

This is the end of my test hehe