# Pewlett-Hackard-Analysis

Analysis for Module 7 and PH Challenge

## Overview of Project:

Once I began to feel more comfortable with SQL I was tasked with a couple of more assignments. I was asked to:

- Determine the number of employees retiring based off their title
- Determine which employees were eligible for the mentorship program

This was a difficult task but luckily, I was able to continue to utilize the ERD map I had created (to map out the database) and I built on the code I was already creating!

## Results:

The results of my analysis are as follows

### Results for Determining the number of employees retiring based off title:

In order to keep my code readable and organized, a lot of my code was amended by creating aliases for readability. To determine the number of employees retiring based off title I utilized my schema from my previous work which saved me a lot of time.

I pulled employee number, first name, last name, title, from date, and then to date and created a new table called retirement_titles. I took the data gathered from previous work (in a file called employees) and joined it with another file (titles). I was able to determine eligibility based on the line with birthdate (between 1952 and 1955).

### The code run in SQL is shown:

![image](https://user-images.githubusercontent.com/96212660/154565872-09118475-452b-4112-a606-bb623c62ec01.png)

### The results of my code:

![image](https://user-images.githubusercontent.com/96212660/154566112-48fa2c16-af9a-4adf-b27a-065cd4da19b1.png)

As you can see from the results in my output that there are duplicates. These are because some individuals have promotions within their time at the company, I used the following code to remove duplicate rows and get a better understanding of what the data is showing me.

![image](https://user-images.githubusercontent.com/96212660/154566153-d00d70cd-d8d5-46f2-9bd0-f97bcd71cefd.png)

### The results of my code:

![image](https://user-images.githubusercontent.com/96212660/154566206-93f1948f-25dd-4d4d-8611-6f4e95854095.png)

Tada, just like that as you can see the duplicates (for example: Chirstian Koblick, Kyoichi Maliniak, Peac Sumant) have been removed and their most up to date titles are left. The results of this were then saved into a new table called “unique titles”.

The next step is determining the number of employees who are about to retire.

### The results are shown:

![image](https://user-images.githubusercontent.com/96212660/154566283-c79e3f98-a45b-4d52-af60-67fd26b21d8f.png)

### The code to get this was pretty straightforward:

 ![image](https://user-images.githubusercontent.com/96212660/154566369-be9788f8-96f9-4175-b82f-5eff4dfd0e54.png)

I used a count function from the unique titles data table, and I grouped by title. The results are in a descending order for easier analysis. And just like that I was able to gather how many employees were going to be retiring and sorted it by their position.

### Results for Determining employees eligible for the Mentorship Program:

### By utilizing the ERD I created:

![image](https://user-images.githubusercontent.com/96212660/154566460-34eee406-bd5e-40c8-afde-419eeb9060a6.png)
 
I created a query to incorporate a table called “mentorship_eligibility”. 

![image](https://user-images.githubusercontent.com/96212660/154566486-1f4f2709-34f8-40df-bbbb-6067afa501b7.png)

### The code for this output:

![image](https://user-images.githubusercontent.com/96212660/154566557-f545000a-26bf-4fca-8b0f-8868538cbdfb.png)

I once again pulled data from the employee data set and gathered the start and to date from the department employee table (from my earlier analysis) and used the distinct function to gather the original occurrence of the employee number for each row. I filtered the birthdates to be between January 1, 1965 and December 31, 1965 (this was the eligibility indicator). The final results were exported to the mentorship_eligbility table. In total there are 1940 eligible employees to participate.

![image](https://user-images.githubusercontent.com/96212660/154566628-6dc99465-0649-46b9-b81a-ed52152f31e2.png)

## Summary:

- The results of the analysis show that there are a total of 90,398 total employees who will be retiring 
- There are not enough qualified, retirement ready employees in the departments to mentor the next generation. There are only 1,940 eligible. That would require each mentor to have around 46 employees in their mentor program. That sounds a bit intense and would essentially defeat the purpose of being a mentor.

I wanted to play around and figure out some other potential conclusions the data was telling me:

### I amended the eligibility code to the following:

![image](https://user-images.githubusercontent.com/96212660/154566731-79ce2d4b-4be1-4f9f-934a-d5435c17f566.png)

My changes extended the age 2 years, and the results show:

47,933 eligible employees! That is a significant difference (I extended the birth date to 2 years earlier) and we can see that there is a more manageable mentor to mentee ratio!

![image](https://user-images.githubusercontent.com/96212660/154566781-1371f4b0-47f9-4577-8fc8-5fc5bed5484d.png)

The second comparison I wanted to see was how many of the individuals from the mentorship_eligibility group were in which title. That way I could get a better understanding of how the mentors to mentees ratio could be dispersed (is it too clumped in one specific group or are they all fairly broken up). In order to do this, I ran the following code:

![image](https://user-images.githubusercontent.com/96212660/154566809-d6cee432-5f14-40f8-b652-36ebf6b298b3.png)

The code was simple, I took the count from earlier and created a new table, the results are as shown:

### From previous (number of employees retiring):

![image](https://user-images.githubusercontent.com/96212660/154566842-3b7eda53-8f6b-4a4f-811d-31bbd59651e8.png)

### The number of mentors per group:

![image](https://user-images.githubusercontent.com/96212660/154566902-ad00934e-9cd4-49cc-a1f1-57c875d763b0.png)

By comparing the available mentors and then the number of retiring employees would leave the following groups with the following ratio of mentor to mentees:

- **Senior Staff: 1:12**
- **Senior Engineer: 1:138**
- **Engineer: 1:22**
- **Assistant Engineer: 1:17**
- **Technique Leader: 1:45**
- **Staff: 1:119**

That leaves an inconsistent ratio per group. I think that there needs to be a little more thought that goes into this mentorship program because the current approach is not very efficient or consistent.

