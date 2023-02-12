## Solution

A walkthrough of the solution to SQL Murder Mystery by [Northwestern University Knight Lab. Solution by Mikhail Popov](https://mystery.knightlab.com/)

There's been a Murder in SQL City! The SQL Murder Mystery is designed to be both a self-directed lesson to learn SQL concepts and commands and a fun game for experienced SQL users to solve an intriguing crime.

>**Problem**
> 
A crime has taken place and the detective needs your help. The detective gave you the crime scene report, but you somehow lost it. You vaguely remember that the crime was a murder that occurred sometime on ​Jan.15, 2018​ and that it took place in ​SQL City​. Start by retrieving the corresponding crime scene report from the police department’s database.-

# Steps 

- select * from crime_scene_report where date='20180115' and city='SQL City'


![image](https://user-images.githubusercontent.com/108262010/218309683-0c7fbf2e-9f02-42a3-a79e-06e812e63eb1.png)

The first witness lives at the last house on "Northwestern Dr". The second witness, named Annabel, lives somewhere on "Franklin Ave".

- select * from person 
p join interview i on i.person_id=o.id 
where (address_street_name='Northwestern Dr' and address_number=(select max(address_number) from person))
or (address_street_name='Franklin Ave' and p.name like 'Annabel%)






![image](https://user-images.githubusercontent.com/108262010/218309743-eb58e1c3-73e1-4078-9e5f-d761836876aa.png)











Morty Schapiro :
  I heard a gunshot and then saw a man run out. He had a "Get Fit Now Gym" bag. The membership number on the bag started with "48Z". Only gold members have those bags. The man got into a car with a plate that included "H42W".
 
Annabel Miller : 
 I saw the murder happen, and I recognized the killer from my gym when I was working out last week on January the 9th.
 
 
 - select * from get_fit_now_member gm 
 join get_fit_now_check_in gc on gc.membership_id=gm.id where gm.id like '48Z%'
 and check_in_date=20180109
 
 
 ![image](https://user-images.githubusercontent.com/108262010/218309324-397944b3-728e-4b99-96df-32e3ef8a78f3.png)
 
 - select * from person p join drivers_license d on p.license_id=d.id 
 where d.plate_number like '%H42W%'
 
 ![image](https://user-images.githubusercontent.com/108262010/218309398-4a363403-8f88-4918-a58e-6310d186f652.png)

Jeremy Bowers-- 
Congrats, you found the murderer! But wait, there's more... If you think you're up for a challenge, try querying the interview transcript of the murderer to find the real villain behind this crime. If you feel especially confident in your SQL skills, try to complete this final step with no more than 2 queries. Use this same INSERT statement with your new suspect to check your answer.


- select * from person p join interview i on p.id=i.person_id where p.id=67318

![image](https://user-images.githubusercontent.com/108262010/218309540-2e15495f-6896-4c7c-bdce-a2e28cbe581a.png)


- select * from person p 
join drivers_license d on d.id=p.license_id
join facebook_event_checkin f on f.person_id=p.id
where d.gender='female' 
and d.hair_color='red'
and d.height>=65 
and d.height<=67
and d.car_make='Tesla'
and d.car_model='Model S'
and f.event_name like 'SQL Symphony Concert'




![image](https://user-images.githubusercontent.com/108262010/218309605-aef17fcc-c2cf-4b98-a85f-4f50dc181942.png)


Miranda Priestly
Congrats, you found the brains behind the murder! Everyone in SQL City hails you as the greatest SQL detective of all time. Time to break out the champagne






 
 

 
 
 
















