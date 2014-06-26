---
layout: post
title:  "Fizzbuzz and the Interview"
date:   2014-06-25
comments: true
categories: interview fizzbuzz
---
Technical interviews are hard to do, or at least, they're hard for me. It's hard to judge a candidate's skills in a 30 minute or 1 hour timeframe. And from this period of time, you're expected to make a decision on the skill levels of a candidate. Some candidates don't interview well even if they have the skill sets you require. On the other side of the coin, there are candidates who interview well but don't deliver on their tasks later on. In order to get the best and brightest candidates for a project, several companies have come up with various methods to screen candidates. Companies have used to have  out-of-the-box style questions (*How many golfballs fit in a 747?*), others have long hours of back-to-back interviews, others endlessly quizz on obscure language constructs (*How would you swap the values of 2 variables without using a third temporary one?*). There are many techniques to use, but to me a technical interview will always start with [FizzBuzz](http://blog.codinghorror.com/why-cant-programmers-program/). I tend to use the standard FizzBuzz problem: 

> Write a method that prints the numbers from 1 to 100, but for the numbers divisible by 3 print out "Fizz", for those divisible by 5 print out "Buzz", and for those divisible by 3 and 5 print out "FizzBuzz"

Some people are against making people code on the spot during an interview. There are various arguments that get used against it;  including nervousness of candidates, lack of tools used in a normal development shop (autocomplete, other people, the Internet), and the fact that it doesn't show real-world problem solving skills. I agree with some of these arguments, but still find that a FizzBuzz type problem is a good first step in determining the skills of a candidate. 

I currently work in a Java web application and every few months there are openings for developers of all skill levels. With the many resumes and interviews we sometimes hold (sometimes 2 a day every day of the week) we need a quick way to screen the skill levels of the candidates. The way that I conduct the interviews is as follows:

1. Welcome the candidate, and brief introductions of interviewers
2. Ask the candidate to talk a little about their technical background
3. Ask the candidate if they are comfortable coding during the interview
4. If the candidate answers yes, then show them FizzBuzz and let them code it on a laptop (Notepad++ editor) or on a whiteboard
5. If the candidate says no, it doesn't discount the candidate but it doesn't give me much confidence
6. Once the candidate completes the exercise (or if they can't complete it within 15 minutes) move on to other questions based around their experience and our project needs

The candidates are applying for a Java position so the expectation is that they provide a working Java program. During the exercise I look for these factors:

1. Does the candidate ask questions for clarifications? 
	- For example, the problem statement doesn't specify that the 3 conditions are exclusive so a candidate may want to clarify whether for "15" would it print out just "FizzBuzz" or "FizzBuzzFizzBuzz"
2. If the candidate makes a mistake, can the candidate trace their code and correct it? 
	- I've seen candidates make a simple error on their loop, like starting from 0 and going to 99. In these instances I ask candidates to trace their code to see if they're tracing the code they wrote vs the code the expect.
3. Is the candidate coding in the right programming language?
	- For these, I've seen candidates that don't write the language they are applying for. For example, I've seen this example as "Java":
	- {% highlight java %}
for (int i = 0, i = i + 1, i < 100) {
...
}
{% endhighlight%}	 

These findings are very helpful in determining the strenghts of a candidate, and they can make the rest of the interview easier on both the interviewer and interviewee. To counteract the negative views of FizzBuzz however, let's look at some common arguments.

The argument that nervous candidates will not interview well is weak in my opinion. I agree an interview is a highly stressful scenario. You're literally putting yourself on the line for a job/career. However, from my experience in working for the Government, there are many times when developers are put into high stress situations. Meetings with an unhappy client, tight deadlines, inappropriate tools (like a 2 CPU computer for development). All of these situations can cause a stressful work experience. That's the reason I ask candidates whether they are comfortable coding, and whether they would be comfortable coding "right now". If the candidate lies to me and says they are but start breaking down when I call their bluff, I don't want that person working on my team. I would never be able to trust a teammate who lies to me during our first meeting.

Some people argue that whiteboard coding or having candidates implement FizzBuzz in a text editor is unfair because the same tools they would use on a day-to-day basis are not available. I would agree with this if FizzBuzz was a complicated problem with the need for various APIs and other component interaction, but let's be honest, a straightforward solution for this would look as follows:

{% highlight java linenos %}
// Omitting class declaration
public void fizzbuzz() {
    for (int i = 1; i <= 100; i++) {
        if (i % 15 == 0) {
            System.out.println("FizzBuzz");
        } else if (i % 5 == 0) {
            System.out.println("Buzz");
        } else if (i % 3 == 0) {
            System.out.println("Fizz");
        } else {
            System.out.println(i);
        }
    }
}
{% endhighlight %}

All the constructs needed for this solution are: `for`, `if`, `else`, `public`, `void`, and the modulus operator `%`. All of these are something that any Java developer should know. If the candidate doesn't know about modulus, then they can ask for help and it can be answered by the interviewer. I check with the candidate every 5 minutes or so to ask them if they have questions, if they don't I let them continue. Another alternative is for the candidate to write a helper function (and I can help them with modulus):

{% highlight java linenos %}
// Omitting class declaration
public void fizzbuzz() {
    for (int i = 1; i <= 100; i++) {
        if (numberIsDivisibleBy(i, 15)) {
            System.out.println("FizzBuzz");
        } else if (numberIsDivisibleBy(i, 5)) {
            System.out.println("Buzz");
        } else if (numberIsDivisibleBy(i, 3)) {
            System.out.println("Fizz");
        } else {
            System.out.println(i);
        }
    }
}
private boolean isDivisibleBy(int number, int divisor) {
	// TODO: don't remember the "remainder" operator
	return ???;
}
{% endhighlight %}

Using the excuse that a candidate is unable to complete this task because autocomplete, the Internet, and other resources are not available is unacceptable. 

As for the other common argument that FizzBuzz doesn't present a real-world problem, how can a candidate who cannot interpret and implement the requirements for a fairly simple problem be expected to complete a business functionality? Or maybe, the candidate can implement it but if it will take them hours to implement FizzBuzz, how long will it take to implement more complicated scenarios? A good developer should be able to complete a FizzBuzz solution in under 15 minutes at worst, but I've seen most good developers complete it in under 10, and some even take as little as 3 minutes. 

FizzBuzz is not intended to determine whether a candidate is hired or not, it is simply the first test that is administered to see if a candidate is worth interviewing further. Just like in [Jeff Atwood's post](http://blog.codinghorror.com/why-cant-programmers-program/), I've seen similar results in my experience interviewing. I wouldn't say that 99% of our candidates can't code this properly, but of the past 6 candidates to have been interviewed by me, only 1 was able to give me a complete solution within that timeframe (it actually took him about 4 minutes to complete, all other candidates did not finish in the 15 minute limit). So for now, FizzBuzz will remain my first line of defense in my technical interviews.