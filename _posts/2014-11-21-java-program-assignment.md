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

public class Checkerboard extends Frame implements ActionListener{

}
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


  * Apples
  * Oranges
  * Potatoes
  * Milk

  1. Mow the lawn
  2. Feed the dog
  3. Dance

### Images look great, too

![desk](https://cloud.githubusercontent.com/assets/1424573/3378137/abac6d7c-fbe6-11e3-8e09-55745b6a8176.png)


### There are also pretty colors

Also the result of [BASSCSS](http://www.basscss.com/), you can <span class="bg-dark-gray white">highlight</span> certain components
of a <span class="red">post</span> <span class="mid-gray">with</span> <span class="green">CSS</span> <span class="orange">classes</span>.

I don't recommend using blue, though. It looks like a <span class="blue">link</span>.

### Stylish blockquotes included

You can use the markdown quote syntax, `>` for simple quotes.

> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse quis porta mauris.

However, you need to inject html if you'd like a citation footer. I will be working on a way to
hopefully sidestep this inconvenience.

<blockquote>
  <p>
    Perfection is achieved, not when there is nothing more to add, but when there is nothing left to take away.
  </p>
  <footer><cite title="Antoine de Saint-Exupéry">Antoine de Saint-Exupéry</cite></footer>
</blockquote>

### There's more being added all the time

Checkout the [Github repository](https://github.com/johnotander/pixyll) to request,
or add, features.

Happy writing.


