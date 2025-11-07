---
title: "Solving a Real Examination Timetabling Problem"
date: 2021-11-15T00:00:00+00:00
description: "A combinatorial optimization project to schedule mid-term exams for the MCS department at AmirKabir University of Technology, using mathematical modeling and GAMS."
author:
  name: "Koorosh Moslemi"
  image: "images/author/john.png"
categories:
  - "Mathematical Modeling"
  - "Integer Programming"
  - "GAMS"
tags:
  - "Combinatorial Optimization"
  - "Mathematical Modeling"
  - "GAMS"
  - "MINLP"
hero: "schedule.jpg"
menu:
  sidebar:
    name: "Examination Timetabling"
    identifier: "examination-timetabling"
    weight: 50
---

This project was a collaboration with [my friend](https://ostadgeorge.github.io/) for the combinatorial optimization course, instructed by [Dr. Hooshmand](https://scholar.google.com/citations?user=psOw7bMAAAAJ&hl=en). Our task was to create a mid-term exam schedule for the entire MCS department at the [AmirKabir University of Technology](https://aut.ac.ir/).

The primary challenge was to devise a schedule that accommodated all students, ensuring that no student had more than one exam on any given day and that there were adequate gaps between exams. Given that each student had a unique set of courses, satisfying everyone's schedule was a complex problem.

For data preprocessing, we used [Numpy](https://numpy.org/) and [Pandas](https://pandas.pydata.org/), and we used the Python API of [GAMS](https://www.gams.com/) to solve our Mixed-Integer Non-Linear Programming (MINLP) models.

{{< alert type="info" >}}
**Constraints:**
- No exams could be scheduled on weekends.
- Each exam had to be scheduled during its own course time.
{{< /alert >}}

### Decision Variables and Parameters

{{< img src="https://drive.google.com/thumbnail?id=1XAXVI0jgO2KLgXyYsUl5LTXPy4hQu7eG&sz=w640-h480" title="Decision Variables and Parameters" align="center" >}}

### Formulation 1: Non-Linear and Slow

In our first attempt, we used a non-linear model to penalize dense exam schedules. The model aimed to maximize the gap between exams within a two-week period. However, we quickly found that a two-week schedule was not feasible.

{{< img src="https://drive.google.com/thumbnail?id=12Pu-OD1uPFsO0v3vUJBEHoSLN3F3dei-&sz=w640-h480" title="First Formulation" align="center" >}}

After extending the scheduling period to four weeks, we were able to find a feasible solution. We also identified 118 students whose schedules created conflicts. By excluding them, we found a two-week integer solution after running the model for seven hours.

{{< img src="https://drive.google.com/thumbnail?id=1H3zalxDfaReH2QmZjcTbD_4o4Lguq0uR&sz=w640-h480" title="First Formulation Results" align="center" >}}

### Formulation 2: Linear and Fast, but Suboptimal

Our second approach was a linear model that minimized the maximum number of exams per week for each student. While this model was much faster, it didn't adequately penalize dense exam schedules within the same week.

{{< img src="https://drive.google.com/thumbnail?id=1QnEtpewcDpCgjfdy6nzvUQNfbeaf-0SD&sz=w640-h480" title="Second Formulation" align="center" >}}

{{< img src="https://drive.google.com/thumbnail?id=15iZubpMmjaU9Xot4eTXdip7oYX3ah5V6&sz=w640-h480" title="Second Formulation Schedule" align="center" >}}

### Formulation 3: The Best of Both Worlds

Our final formulation combined the ideas from the previous two models.

{{< img src="https://drive.google.com/thumbnail?id=1mXL9uXiTxhO1dsBjiP0PBbq4rY1DmAq9&sz=w640-h480" title="Third Formulation" align="center" >}}

This model produced an integer solution after six hours. When we excluded the 118 problematic students, we found an optimal two-week schedule in just 15 minutes.

{{< img src="https://drive.google.com/thumbnail?id=1eOiI9mVQHwAUoqC4hPkWm471awKOWPti&sz=w640-h480" title="Third Formulation Results 1" align="center" >}}

{{< img src="https://drive.google.com/thumbnail?id=1GE--gx99wlTJ79NGwz5TUTf0DKoDfXua&sz=w640-h480" title="Third Formulation Results 2" align="center" >}}

The complete source code is available in this [GitHub repository](https://github.com/KooroshMoslemi/Examination-Timetabling-Problem).
