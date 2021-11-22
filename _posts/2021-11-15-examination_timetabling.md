---
layout: post
title: Solving a Real Examination Timetabling Problem
categories: [Mathematical Modeling,Integer Programming,GAMS]
---
                                               
This project was a joint work of me and [my friend](https://ostadgeorge.github.io/) for the combinatorial optimization course, which was instructed by [Dr.Hooshmand](https://scholar.google.com/citations?user=psOw7bMAAAAJ&hl=en).


In this project, we had to schedule mid-term exams of the entire MCS department at the [AmirKabir University of Technology](https://aut.ac.ir/).

More precisely, we had a list of students that had taken some courses. Our job was to find the best examination schedule for all students so that there is at most one exam for any student in one day and there is a suitable gap between exams from students' point of view.

Because each student could have a different set of courses, our biggest challenge was to make everyone happy with their examination schedule!

It is worth mentioning that we used [Numpy](https://numpy.org/) and [Pandas](https://pandas.pydata.org/) for preprocessing and the python API of [GAMS](https://www.gams.com/) to solve our MINLP models.

```
Note:
- We couldn't schedule any exams on the weekend.
- Each exam had to be scheduled in its own course time.
```

### Definition of decision variables and parameters:

<img src="https://drive.google.com/thumbnail?id=1XAXVI0jgO2KLgXyYsUl5LTXPy4hQu7eG&sz=w640-h480"/>  

### The first formulation - It worked, but it wasn't fast enough! :

In this model, we tried to specify some penalties for more dense exams in a non-linear fashion. Since we had to schedule all the exams in two weeks, the two inner summations helped us consider the gap between each t and t' pair in these weeks. 
When we first ran the above model, we observed that there was no feasible solution for two weeks. 

<img src="https://drive.google.com/thumbnail?id=12Pu-OD1uPFsO0v3vUJBEHoSLN3F3dei-&sz=w640-h480"/> 

Later we realized there was no feasible solution until we considered four weeks for examination. ([project1_experiment1.gms](https://github.com/KooroshMoslemi/Examination-Timetabling-Problem))

We also identified 118 students that prevented our model from finding a feasible solution. ([project1_experiment2.gms](https://github.com/KooroshMoslemi/Examination-Timetabling-Problem))

We ran this model for seven hours without the forementioned students, and we found a two-week integer solution.

We also tested this model on a smaller subset of 6 students, and we confirmed it is trying its best to meet the conditions of our problem:

<img src="https://drive.google.com/thumbnail?id=1H3zalxDfaReH2QmZjcTbD_4o4Lguq0uR&sz=w640-h480"/>


### The second formulation - It was linear and fast, but it wasn't good enough! :

In our second try, we defined a linear model. It had to minimize the maximum number of exams in a week for each student. Our idea was that the model would try to distribute exams between weeks as uniformly as possible to reach a lower objective. 

<img src="https://drive.google.com/thumbnail?id=1QnEtpewcDpCgjfdy6nzvUQNfbeaf-0SD&sz=w640-h480"/>

The main disadvantage of this model was it did not consider any penalty for dense exams in a week.

Here is a schedule we found with this model:

<img src="https://drive.google.com/thumbnail?id=15iZubpMmjaU9Xot4eTXdip7oYX3ah5V6&sz=w640-h480"/>



### The third formulation - It had the best of both worlds! :

Combining the ideas of the previous formulations, we came up with the following model:

<img src="https://drive.google.com/thumbnail?id=1mXL9uXiTxhO1dsBjiP0PBbq4rY1DmAq9&sz=w640-h480"/>

To avoid complexities, we skipped some details regarding indexes' limitations. (For more information, please check out [project1_v1.6.gms](https://github.com/KooroshMoslemi/Examination-Timetabling-Problem))

We ran the model for 6 hours, and we reached the following integer solution:

<img src="https://drive.google.com/thumbnail?id=1eOiI9mVQHwAUoqC4hPkWm471awKOWPti&sz=w640-h480"/>

We also tried to ignore the 118 students we identified by our first experiment, and we got the following optimal solution for two weeks in 15 minutes!

<img src="https://drive.google.com/thumbnail?id=1GE--gx99wlTJ79NGwz5TUTf0DKoDfXua&sz=w640-h480"/>

The complete source code is available in [this](https://github.com/KooroshMoslemi/Examination-Timetabling-Problem) repository.










