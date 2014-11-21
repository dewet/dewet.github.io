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


Next, I am going to declare some variables and construct some constructor methods.

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

Because this class extends Frame, we will have to create a new class to output these constructor methods.
Within this class, we will run a for loop, creating 16 TextArea() constructs, we will also construct the layout.

{% highlight java %}

public Checkerboard(){
		start = 0;
		stop = 0;
		step = 0;
		
		this.setLayout(new BorderLayout());
		
		blockPanel.setLayout(new GridLayout(4, 4, 2, 3));
		buttonPanel.setLayout(new FlowLayout());
		fieldsAndLabels.setLayout(new FlowLayout());
		
		for(int i = 0; i<16; i++){
			blockDisplay[i] = new TextArea(null, 3, 5, 3);;
			blockPanel.add(blockDisplay[i]);
			blockDisplay[i].setEditable(false);
			blockDisplay[i].setText(i + "");
		}
		
		
		buttonPanel.add(goButton);
		goButton.addActionListener(this);
		buttonPanel.add(clearButton);
		clearButton.addActionListener(this);
		
		fieldsAndLabels.add(startField);
		fieldsAndLabels.add(stopField);
		fieldsAndLabels.add(stepField);
		
		fieldsAndLabels.add(startLabel);
		fieldsAndLabels.add(stopLabel);
		fieldsAndLabels.add(stepLabel);
	}
	
{% endhighlight %}

Also going to add an addWindowListener() method to the Checkerboard class allowing the user to quit the application.

{% highlight java %}
		addWindowListener(
				new WindowAdapter()
						{
					public void windowClosing(WindowEvent e)
					{
						System.exit(0);
					}
				}
			);
{% endhighlight %}

So overall, this application still doesnt do anything.
What I am going to do next will check to see if the <i>go</i> button or the <i>clear</i> button have been pressed and then converting the text fields answers to <i>integers</i>.


































