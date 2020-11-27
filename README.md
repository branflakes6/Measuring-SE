# Measuring-Software Engineering


### Introduction

The idea of measuring software engineering has existed pretty much since Software Engineering began It is an idea that has evolved into an entire field with hundreds of methods and dozens of companies working on the problem.<sup>[1]</sup> Modern software companies place a lot of importance on being able to measure the quality of work being done by their employees, companies are paying a lot of money for their engineers and want to make sure they are getting the best out of them. Many companies exist to create new ways of measuring software engineering that they can sell to larger companies. The techniques and technologies produced by these companies have a lot of potential in making the process easier and could lead to better engineering standards and practices. However, there are many ethical questions and concerns that need to be answered.  

In this report I will look at many ways to measure engineering, some of the original methods and ways of quantifying software as well as some new ideas. Some tools used to measure the engineers themselves who are working on the code base, how productive they are, what do they contribute to the company. Then lastly, I will discuss the ethics of all of this and give my opinions on whether I think these ideas should be embraced by the industry.


### Algorithmic Approaches

Lines of Code (LOC)

One of the most basic approaches to measuring Software Engineering is source lines of code. There are two different ways of doing this, the first is physical source lines of code which is simply counting the number of lines of code in the code base. <sup>[1]</sup>  The second is logical lines of code which attempts to count the number of executable statements. <sup>[1]</sup>

This method of measuring software has been around since the 1960’s <sup>[1]</sup> and while it has remained a popular metric to assist in measuring software engineering it quickly became apparent that SLOC on its own is an ineffective and misleading measurement. When measuring software by its lines of code you do not account for several important factors, such as the differences and diversity in programming languages and how each one does a task and the simple truth that a long program is not necessarily a complex program. 

Examples: Code can be written in many ways

A simple example is two ways of summing two numbers in Java	
``` 
Public int add (int a, int b) {Return a + b;}
```

Vs

```
Public int add (int a, int b) 
{
	int sum;
	sum = a + b;
 	Return sum;
}
```

If we are to count physical lines of code the first implementation of this function is done in one line that simply just returns a + b, the second implementation returns the exact same answer but does so in six lines and uses an extra variable to add a and b. Both functions do the exact same thing, but the second version has many more lines of code while also being less efficient. If we use logical lines of code and define a logical SLOC as an executable line with a semicolon (ignoring function definitions and curly brackets) we get one logical SLOC for the first function and three for the second. While this is a better measurement as the two functions are now closer in magnitude there is still the obvious flaw that the less efficient function still appears to be the better one by our measurement. Additionally, our measurement of logical lines of code is based on simply counting the number of semicolons, which is a problematic approach as it only works for some languages. There are many languages such as python which do not use semicolons and thus creating a definition that works for all languages is extremely difficult.

This highlights a key issue with counting lines of code, it is very difficult to tell the difference between complex code and long code. A system of measurement that uses only source lines of code can be detrimental to the code base as it can encourage programmers to write worse code. If you are basing your metrics of which developers are working hardest or doing the best work on SLOC then you are creating an environment that encourages your engineers to find the longest possible way to write their code. This can lead to deliberately inefficient methods that require a large amount of code. 

Another example is the difference between a simple Object Orientated Java class and a complex but compact algorithm. When writing Object Orientated programs you can end up with a long piece of software with a lot of basic getter and setter methods that simply just changes one or two values of the object. Writing such a class could take only an hour or two but have hundreds of lines of code, conversely a complicated algorithm that could be crucial to the software system may only be 20-30 lines long but could take several days to develop as it requires the engineer to spend a lot of time figuring out the logic of what they are trying to create rather than just mindlessly writing code.

```
*"Measuring programming progress by lines of code is like measuring aircraft building progress by weight" - Bill Gates* 
```

Source lines of code as a metric is only useful when combined with other measurements, if you impose strict coding practices on your engineers and ensure that everyone is writing the highest quality and most line efficient code they can then it can provide some insight into the complexity of your code base. For example, Windows NT 3.1 has about 5 million source lines of code while windows XP had about 45 million <sup>[3]</sup>, this provides some meaningful information on the scale of these projects and the number of engineers required to create and maintain them.


ABC Method

The ABC software metric was developed as an answer to issues with SLOC, it attempts to solve the problem with a more algorithmic approach that is much less simplistic.<sup>[4]</sup>

ABC values are calculated by counting the number of assignments(A), branches (B) and conditionals (C) and then creating a triplet of these values.<sup>[4]</sup>

The following equation is used to calucalte ABC values


```
<ABCvector> = √(a2 + b2 + c2)
```

ABC evaluation has different rules depending on the programming language used, this is aimed at creating consistent scores across a range of languages. The goal of ABC is to measure the size of the software in a meaningful by evaluating all parts of the system rather than just lines of code. ABC accounts for things such as conditional operators, assignment operators and important keywords. This means it can tell the difference between the complexity of single lines of code. <sup>[4]</sup>

An example of using ABC to measure software:

```
System.out.println(x);
```

Vs

```
If ( x >= 0 && y != 1) { System.out.println(x + y);} 
```
In a basic SLOC system these would both have a value of one as there is one line of code and one semi colon. In ABC however the first snippet has a single class method call that prints x so its value for A = 0, B = 1 and C = 0.  

The second snippet has a condition, two conditional operators, a class method call and an assignment so its values will be A = 1, B = 1, C = 3. 

This demonstrates the clear difference in complexity between these lines and allows for a much greater evaluation of the code base. 

While ABC is a better metric for measuring software than simple SLOC it still has many of the same drawbacks. Like SLOC if not used correctly it can encourage bad programming as it still rewards you for writing longer less efficient code, however the rewards are not as great with ABC so there is less incentive. Like SLOC, ABC is most valuable when used in combination with other methods and systems. If engineers are following good programming practice and their code is being monitored to ensure they are not trying to game the system, it can be a useful metric for determining its complexity.



### New Technologies and Companies

Many modern solutions to measuring software engineering have abandoned the idea of using complex algorithms or techniques to measure the quality of the code itself. As discussed, it is simply too difficult a task due to the nature of software, differences in language and the type of work being done make most comparisons useless. The modern solution to this problem is to instead measure the engineers working on the software themselves. This means we are no longer looking just at the code been written but the efficiency of the engineers themselves, how hard they are working and what factors could be preventing them from doing better work. This combined with good code practices and mostly manual reviews of software been written is a much easier way to measure software engineering. 


### Humanyze 

Humanyze was founded in 2010 and aims to measure software engineering by analysing engineers themselves rather than the code they write. 

They achieve this using a badge that monitors employees at work. The Humanyze badge uses location data and speech recognition to gather data about employees. It can determine where employees are spending most of their time through out, they day, which departments are interacting with each other and the nature of these interactions. The Humanyze badge does not record conversations between employees but instead uses technology to analysis things such as the tone of voice of the people talking to try and determine the mood and nature of the conversation. This allows it to tell if employees are getting along well or are hostile to each other.

The badge can track exactly what you have spent your time doing throughout the day, where you have been and who you interact with most. All this data is then analysed by Artificial Intelligence to tell employers if their employee dynamic is “healthy” <sup>[5]</sup>. They produce metrics about how happy employees are, how engaged they are and how productive they are. 

Humanyze claim their badges protect employee privacy in several different ways.<sup>[6]</sup> Firstly, and most importantly they do not record any content from email, messages or voice calls.<sup>[6]</sup>  Data is analysed based on things like tone of voice rather than the actual content of the call, emails and messaging are used mostly to determine which departments employees interact with the most and which ones are the largest source of problem.<sup>[6]</sup> Humanyze also does not provide any identifiable information to employers. The data is not presented on a person by person basis instead employers are given an overview of the entire company with aggregate information about the performance of the whole office.<sup>[6]</sup> Humanyze does however have a personal dashboard where you can see your own information and while employers can’t access this, they could request employees give them this data themselves.<sup>[6]</sup> Humanyze also does not track employees when they are in the bathroom and does all location tracking via beacons and not GPS. <sup>[6]</sup>

Humanyze aims to use this data to build a more productive and better functioning work force. They believe by understanding how employees are interacting they can find ways to increase productivity and eliminate major stress factors. In an interview with Business Insider.<sup>[7]</sup> CEO Ben Waber gave an example of how they determined that employees spent less time calling each other if they had a little bit of extra face to face time throughout the day. By designing a lunch schedule with overlap between employees who interact a lot you can eliminate a lot of time spent on the phone and increase productivity. 


### StatusToday

StatusToday is a tool based on the idea that employers and managers don’t understand their employees. StatusToday aims to fix this problem by using AI to analyse data about employees to better understand them and what they might need or how they are performing. StatusToday is also able to define and map relationships between employees to build a database of who is talking to who in the office and which employees hold the most social power.<sup>[8]</sup>

StatusToday uses an AI named Isaak to analyse a range of data it gathers about employees. One of its goals is to identify which employees are being overworked and why, Isaak can identify if certain managers are delegating too much work and give feedback to employees on why they may be feeling overworked.<sup>[8]</sup> Isaak can also determine if an employee is working outside of office hours and risking burnout. Isaak aims to reduced burnout as much as possible by providing information on the sources of burnout.<sup>[8]</sup>

Isaak also monitors office relationships to try and determine who is influential within the office. It creates a database of all employees that unlike Humanyze is not anonymised, this database ranks employees by the size of their circle, how critical they are, how connected they are and how much influence they hold in the office. This gives a very detailed overview of how exactly individual employees effect the social dynamic of the office and who is most critical to maintaining it. This can be used to determine candidates for managerial positions or to figure out which employees would be missed the least if let go.

Like Humanyze StatusToday does not collect and record information from emails or phone calls, instead it simply analyses metadata to determine the context of the interaction. <sup>[8]</sup>


### Atlassian 

Atlassian are a software engineering company that has developed numerous tools designed to aid with and measure software engineering such as Jira and Trello. 

Trello workflow management software that gives employees a way of tracking their work and deadlines. Trello provides its users with dozens of tools that allow them to create a work board of the various things they are working on. Users can break there projects down into individual components and set deadlines and expected completion times. Trello aids in the measurement of software engineering by giving companies and employees the ability to monitor exactly how long a task took to do. The engineer can set a deadline for themselves based on how long they think it will take and then mark the task complete when its finished. By taking all this data across an entire company and aggregating it you can begin to get an idea of how long certain tasks should take to do. This allows employers to compare the speed and efficiency of all their employees.

Jira is an issue tracking software designed for tracking bugs in software projects. Jira allows engineers to create a list of bugs they are working on fixing, which ones still need to be done and which ones they are in the process of fixing. Much like Trello the data collected from Jira can be used to figure out an estimate of how long certain types of bugs should take to be fixed. It can also be used to identify which engineers are creating the most bugs as you can see which part of the code base contains the greatest number of bugs.


### Ethics

The ethics of measuring software engineering is a complex topic that is not black or white, some approaches are ethical while others are not, but most are somewhere in the middle. 

Many of the new technologies being invented raise question about exactly what data about us do our employers own. Should an employer really be allowed to require its employees to wear a badge or use a device that tracks them throughout the day and records all sorts of personal information and then they get to own that data? If an engineer receives a personal phone call at work while wearing a device that records all their conversations should the employer really be entitled to that data? If an employer purchases a Fitbit or other such fitness device for an engineer should they own that data? is it ok that the information about my heart rate during work is owned by my company and not me? In my opinion this creates a dangerous environment where people are essentially owned by their employers while at work, employers can force employees to use all sort of technology to monitor every single aspect about them while maintaining full control of the data. Personally I do not believe an employer should be entitled to own any of this data about their employees, while this data may have value in increasing productivity and identifying issues at the work place this is incredibly personal and private information that should be up to the discretion of the employee to divulge if they wish to. 

Many of the technologies I have looked into claim that they are “opt-in” and thus it is up to employees to choose to be monitored and hand over their data, while this is a nice sentiment to claim we know historically that this simply isn’t how it will work in reality. Your boss can come to you and present you with a Humanyze badge claiming its up to you if you wish to wear it or not but if you walk into work on Monday morning and everyone else is wearing theirs then it becomes pretty obvious what is expected of you. <sup>[6]</sup> Only employees of vital importance can usually avoid going against the norm and opt-out of these things, new employees especially find it almost impossible to refuse as who would want to make a bad impression when they have just begun work. 

There is also the question of where it does all end, where do employers draw the line between personal information and useful information. There are many things not measured by these tools that could be useful such as how much sleep your employee is getting on average and the quality of food, they are eating through out the day. If we are willing to let companies monitor every single thing we do at work and we are willing to give them information about our health and vitals why would they not feel entitled to this information. When it comes to ideas like Humanyze there is also the question of how it will evolve, currently they do not gather personal data or record phone calls but that is not guaranteed to be the same. Ultimately devices like this condition employees to be used to the idea of being monitored and tracked, to accept that they do not have privacy at work. This can be developed overtime to be more intrusive and if Humanyze becomes popular it is only a matter of time before a competitor offers a more invasive version that collects much more data.

I find the idea behind StatusToday particularly concerning from an ethical perspective. From a practical point of view, I can see the use of such metrics, it is a good way to judge which employees are best suited to management positions and to determine which employees influence the office dynamic the most. My concern comes from the expectations that are created by this kind of data. If a company is choosing between two employees to fire, data like this can be used to help make that decision, if you are choosing between two relatively even engineers in terms of ability you will almost always keep the whichever one StatusToday tells you is more critical to the office dynamic. This kind of thinking feeds into the idea of the cult of the company where employees are expected to actively participate in office social dynamics rather than just keeping their head down and doing their work. It means “optional” events such as office parties and company retreats can be vital for keeping your job, employees are expected to work hard to make themselves popular and integral to the office dynamic. Employees already give the majority of their day five days a week to their job and should not be expected to maintain social relationships with colleagues outside of the office as well. 

The idea of breaking down human interaction into models and statistics is one I find deeply troubling. <sup>[10]</sup> These tools try to take an integral part of the human experience and turn it into a science that can be quantified and manipulated. I think it is wholly unethical to encourage the gamification of human interaction, to create an environment where employees become friends with each other purely for the sake of benefiting their careers rather than any real attachment to each other. It creates hollow fake relationships which can lead to a society where people are distrustful and begin to feel like they do not have any real friends. If your company is using a service like StatusToday it would cast doubt over anyone in the office who is trying to be your friend, how can you be sure they have an actual interest in you as a person and are not simply trying to please the algorithm. Our personal relationships should not be a part of the working world, they should be entirely separate. Employers have no right to know who you are friends with or to judge you based on who you wish to talk to. No employee should feel that a part of their job is to be friends with their co-workers or that they will be judged on how well liked they are.

The ideas of nepotism and cronyism are often thrown around when discussing the problems of the modern corporate world. In my opinion the gamification of working relations falls under a similar umbrella, it does not pick good employees by there ability to actually do their job it instead encourages companies to hire and promote people who are well connected and popular within the office. 

Even some of the productivity boosting solutions presented by these companies that may seem good on paper are also questionable from the employee’s perspective. An example I gave with Humanyze was designing a lunch schedule that gave overlapping lunch hours to employees that interact a lot. This seems like an innocent enough idea but at its core its designed to encourage employees to have meetings during their lunch break. Lunch break is meant to be as the name suggested a break in the day from your work, designing your timetable to try and force employees to use this time to have meetings instead goes against the very idea of giving them a break.

Employers already demand so much from their employees. Most jobs are eight hours a day five days a week, commute times in Dublin are on average about an hour total and when you factor in preparing for work and the lack of energy after work for most people a work day is pretty much entirely dedicated to their job. <sup>[9]</sup> Software Engineers in particular are all to familiar with the idea of crunch time and excessive overtime. So much is already given to our companies, is it really ok for them to begin monitoring every last detail about us on top of this? Just so they can attempt to squeeze every drop of productivity out of you. 

Of course, some of the tools looked at are perfectly fine, those not concerned with tracking vitals and monitoring conversations are much less objectionable. We do have to acknowledge in the field of software engineering that companies are paying incredible wages for the work being done and so naturally they would like to make sure it is being done to a high standard and that their employees are not slacking off. Tools like Jira and Trello that are simply tracking how much work and employee does are fine, this is a good way to ensure your engineers are keeping on top of their assignments and aren’t being overloaded without any questions of privacy or data ownership. An employee working on your code base doesn’t have expectations of ownership over that code and so is unlikely to take issue with you monitoring their contributions to the software. These tools are useful in allowing employees to keep on top of their work and monitor their own levels of productivity, if used appropriately they can lead to a decrease in stress and a more manageable workload.

The technologies I have criticised also do provide some value. StatusToday for example has a lot of tools for identifying overworking and burn-out. It can tell if an employee is working long hours out of office when they shouldn’t be and can identify sources of stress and burn out. They claim to encourage a better work life balance and believe in giving employees adequate time off and reducing workload when necessary. They have done statistical analysis on burnout and suggest employee friendly ways to reduce it such as better pay and reduced workload. <sup>[11]</sup> Humanyze aims to increase productivity and identify issues in the office. Their commitment to privacy means employees are not being exposed on an individual level instead department and office wide problems are identified, and solutions are suggested. Like StatusToday Humanyze aims to reduce stress and fix managerial problems that are making employees jobs worse. Humanyze also allows employers to identify culture problems within the office without putting employees in the firing line, it can tell if employees are not happy with each other by the tone of their conversations without revealing who was involved in the conversation. 

Ultimately, I think gathering data about your engineers that is beyond simply the quality or quantity of there work should not be encouraged. Employees should have the right to maintain some level of privacy at work and should not expect every single thing they do to be monitored. I also believe people should have full ownership of any data collected about themselves, if an employer wants to purchase Fitbits for the whole office that should not mean they own the data collected by these devices. Any and all information about my innerworkings, my hear rate, my fitness, my stress levels should belong to me and only me. It should be up to employees to share this information if they wish to and there should never be an expectation from the employer that they can access this. Our privacy is constantly being undermined in the modern world and this is starting to take over the working world. I do not believe it is ethical to track your employees at every possible second and to completely strip them of their privacy at work. Employees are people and not just tools to make a profit, productivity should not come at the cost of sacrificing our humanity. 


### Sources
[1] Norman E Fenton, Martin Neil. Software metrics: successes, failures and new directions. Journal of Systems and Software, July 1999.
https://www.sciencedirect.com/science/article/pii/S0164121299000357

[2] “Measuring programming progress by lines of code is like measuring aircraft building progress by weight.” – Bill Gates retrieved from: https://www.goodreads.com/quotes/536587-measuring-programming-progress-by-lines-of-code-is-like-measuring

[3] The Build Master: Microsoft's Software Configuration Management Best Practices – Vincent Maraia.
https://www.bookdepository.com/Build-Master-Vincent-Maraia/9780321332059

[4] Applying the ABC Metric to C, C++ and Java – Jerry Fitzpatrick.
https://www.softwarerenovation.com/ABCMetric.pdf

[5] Humanyze Organizational Health Score.
https://www.humanyze.com/organizational-health-score/

[6] Humanyze Data Privacy.
https://www.humanyze.com/data-privacy/

[7] ”Employees at a dozen Fortune 500 companies wear digital badges that watch and listen to their every move” – Business Insider 2016.
https://www.businessinsider.com/humanyze-badges-watch-and-listen-employees-2016-10?r=US&IR=T

[8] StatusToday.com
https://blog.statustoday.com

[9] Census of Population 2016 – Profile 6 Commuting in Ireland
https://www.cso.ie/en/releasesandpublications/ep/p-cp6ci/p6cii/p6td/

[10] Wei Pan, Wen Dong, Manuel Cebrian, et al, Modelling Dynamical Influence in Human Interaction. Media Laboratory, MIT, August 2018. 

[11] “Isaak helps managers transform workplace wellbeing by going further than engagement surveys” – StatusToday 2019.
https://blog.statustoday.com/isaak-helping-managers-transform-workplace-wellbeing-by-going-beyond-engagement-surveys-b123c2254f87

