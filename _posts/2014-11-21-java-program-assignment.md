---
layout:     post
title:      Java Checker board Assignment
date:       2014-11-21 01:01:01
summary:    This is me attempting to create a checker-board Java application. This is an assignment that I have to complete. This is just a run down of what I have done/am doing.
categories: java assignments
---

This is going to be a post on creating your very own Checker board.
I am going to program this step by step.
## Here is the program:

![checkerboard](http://i.imgur.com/U2ftOcp.png)<br>
![checkerboard-input](http://i.imgur.com/HmSzBmR.png)<br>
![checkerboard-input2](http://imgur.com/U2ftOcp,HmSzBmR,t4XZvHp#2)<br>

<br>
Hopefully this is simple to understand. Hopefully it is fairly self explanatory.
<br>
### Creating the application
First I am going to need to import some packages and create my Checkerboard class.
<br>
{% highlight java %}
import java.awt.*;
import java.awt.event.*;

public class Checkerboard extends Frame implements ActionListener{}
{% endhighlight %}
<br>
Next, I am going to declare some variables and construct some constructor methods.
<br>
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
<br>
Because this class extends Frame, we will have to create a new class to output these constructor methods.
Within this class, we will run a for loop, creating 16 TextArea() constructs, we will also construct the layout.
<br>
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
<br>
Also going to add an <i>addWindowListener()</i> method to the Checkerboard class allowing the user to quit the application.
<br>
{% highlight java %}
addWindowListener(
	new WindowAdapter(){
		public void windowClosing(WindowEvent e)
			{
				System.exit(0);
			}
		}
	);
{% endhighlight %}
<br>

So overall, this application still doesn't do anything.
What I am going to do next will check to see if the <i>go</i> button or the <i>clear</i> button have been pressed and then converting the text fields answers into <i>integers</i> using the Integer.parseInt(<i>var</i>) method if <i>go</i> is pressed, if <i>clear</i> is pressed it will set every block in the <i>blockDisplay[]</i> Array.
<br>
{% highlight java %}
	public void actionPerformed(ActionEvent e) {
		if (e.getSource() == goButton){
			start = Integer.parseInt(startField.getText());
			stop = Integer.parseInt(stopField.getText());
			step = Integer.parseInt(stepField.getText());
			
			for(int i = start; i<stop; i+=step){
				blockDisplay[i].setBackground(green);
			}
		}else if(e.getSource() == clearButton){
			for(int i = 0; i<16; i++){
			blockDisplay[i].setBackground(white);
			}
			startField.setText("");
			stopField.setText("");
			stepField.setText("");
		}
{% endhighlight %}
<br>
I am adding two color constructors and assigning them to the variables <i>white</i>, <i>red</i>and <i>green</i>, <i>white</i> has been used in the previous code block.
<br>
{% highlight java %}
Color white = new Color(250,250,250);
Color red = new Color(255, 90, 90);
Color green = new Color(140, 215, 40);
{% endhighlight %}
<br>
Also going to make all the boxes red when used. by adding this line of code into the loop the constructs the boxes.
<br>
{% highlight java %}
blockDisplay[i].setBackground(red);
{% endhighlight %}
<br><br>
Okay, now, I have decided to tweak one or two things. here they are. added (i+1) into the output of each box to make them start from box 1 instead of box 0.
<br>
{% highlight java %}
blockDisplay[i].setText((i+1) + "");
{% endhighlight %}
<br>
Also changed the layout a little, so that the labels will be displayed a long side there corresponding text field. also layout the text in a nice South, Center, North way.
<br>
{% highlight java %}
fieldsAndLabels.add(startField);
	fieldsAndLabels.add(startLabel);
		
fieldsAndLabels.add(stopField);
	fieldsAndLabels.add(stopLabel);
		
fieldsAndLabels.add(stepField);
	fieldsAndLabels.add(stepLabel);
		
add(blockPanel, BorderLayout.NORTH);
add(fieldsAndLabels, BorderLayout.CENTER);
add(buttonPanel, BorderLayout.SOUTH);
{% endhighlight %}
<br>
Last part in the ActionListener class, I added another for loop allowing me to be able to execute the input from the user.
{% highlight java %}
for(int i = start; i<stop; i+=step){
	blockDisplay[i].setBackground(green);
}
{% endhighlight %}
<br>
Lastly, I added a main class that sets the boundaries for the frame, sets the title, and allows it to be visible.
<br>
{% highlight java %}
public static void main(String[] args){
	Checkerboard f = new Checkerboard();
	f.setBounds(50, 100, 300, 400);
	f.setTitle("Checkerboard Array");
	f.setVisible(true);
	}
{% endhighlight %}
<br>

## And we are done! 

Just take a look at that finished code!

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
		
	Color white = new Color(250,250,250);
	Color red = new Color(255, 90, 90);
	Color green = new Color(140, 215, 40);
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
			blockDisplay[i].setText((i+1) + "");
			blockDisplay[i].setBackground(red);
		}
		
		
		
		
		buttonPanel.add(goButton);
		goButton.addActionListener(this);
		buttonPanel.add(clearButton);
		clearButton.addActionListener(this);
		
		fieldsAndLabels.add(startField);
			fieldsAndLabels.add(startLabel);
		
		fieldsAndLabels.add(stopField);
			fieldsAndLabels.add(stopLabel);
		
		fieldsAndLabels.add(stepField);
			fieldsAndLabels.add(stepLabel);
		
		
		
		
		add(blockPanel, BorderLayout.NORTH);
		add(fieldsAndLabels, BorderLayout.CENTER);
		add(buttonPanel, BorderLayout.SOUTH);
		
		addWindowListener(
			new WindowAdapter(){
				public void windowClosing(WindowEvent e)
					{
						System.exit(0);
					}
				}
			);
		
		
	}
	public void actionPerformed(ActionEvent e) {
		if (e.getSource() == goButton){
			start = Integer.parseInt(startField.getText());
			stop = Integer.parseInt(stopField.getText());
			step = Integer.parseInt(stepField.getText());
			
			for(int i = start; i<stop; i+=step){
				blockDisplay[i].setBackground(green);
			}
		}else if(e.getSource() == clearButton){
			for(int i = 0; i<16; i++){
			blockDisplay[i].setBackground(white);
			}
			startField.setText("");
			stopField.setText("");
			stepField.setText("");
		}
		
	}
	
	public static void main(String[] args){
		Checkerboard f = new Checkerboard();
		f.setBounds(50, 100, 300, 400);
		f.setTitle("Checkerboard Array");
		f.setVisible(true);
	}

}
{% endhighlight %}






























