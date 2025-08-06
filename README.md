# SQL-Island

SQL Island is a fun introduction to learning and using SQL. The challenge can solved on this website SQL ISLAND  
This is my approach to solving the SQL Island challenge.

## Question and Answer

QUESTION: It seems there are a few people living in these villages. How can I see a list of all inhabitants?  
```sql
SELECT *
FROM INHABITANT;
```

QUESTION: Man! I'm hungry. I will go and find a butcher to ask for some free sausages.  
```sql
SELECT *
FROM INHABITANT
WHERE job = 'butcher';
```

QUESTION: Thank you, Edward! Okay, let's see who is friendly on this island...  
```sql
SELECT *
FROM INHABITANT
WHERE state = 'friendly';
```

QUESTION: There is no way around getting a sword for myself. I will now try to find a friendly weaponsmith to forge me one.  
```sql
SELECT *
FROM INHABITANT
WHERE state = 'friendly' AND job = 'weaponsmith';
```

QUESTION: Oh, that does not look good. Maybe other friendly smiths can help you out, e.g. a blacksmith. Try out: job LIKE '%smith' to find all inhabitants whose job ends with 'smith'.  
```sql
SELECT *
FROM INHABITANT
WHERE state = 'friendly' AND job LIKE '%smith';
```

QUESTION: That looks better! I will go and visit those smiths. Hi stranger! Where are you going? I'm Paul, I'm the major of Monkeycity. I will go ahead and register you as a citizen.  
```sql
INSERT INTO INHABITANT (name, villageid, gender, job, gold, state)
VALUES ('Stranger', 1, '?', '?', 0, '?');
```

QUESTION: No need to call me stranger! What's my personid?  
```sql
SELECT personid
FROM INHABITANT
WHERE name = 'Stranger';
```

NOTE: This returns a personid of 20  

QUESTION: Hi Ernest! How much is a sword? I can offer to make you a sword for 150 gold. That's the cheapest you will find! How much gold do you have?  
```sql
SELECT gold
FROM INHABITANT
WHERE personid = 20;
```

QUESTION: Damn! No mon, no fun. There has to be another option to earn gold other than going to work. Maybe I could collect ownerless items and sell them! Can I make a list of all items that don't belong to anyone?  
```sql
SELECT *
FROM ITEM
WHERE owner ISNULL;
```

QUESTION: So much cool stuff! Yay, a coffee cup. Let's collect it!  
```sql
UPDATE ITEM
SET owner = 20
WHERE item = 'coffee cup';
```

QUESTION: Do you know a trick how to collect all the ownerless items?  
```sql
UPDATE ITEM
SET owner = 20
WHERE owner ISNULL;
```

QUESTION: Now list all of the items I have!  
```sql
SELECT *
FROM ITEM
WHERE owner = 20;
```

QUESTION: Find a friendly inhabitant who is either a dealer or a merchant. Maybe they want to buy some of my items.  
```sql
SELECT *
FROM INHABITANT
WHERE state = 'friendly'
AND job = 'dealer' OR job = 'merchant';
```

QUESTION: I'd like to get the ring and the teapot. The rest is nothing but scrap. Please give me the two items. My personid is 15.  
```sql
UPDATE ITEM
SET owner = 15
WHERE item IN ('teapot', 'ring');
```

QUESTION: Thank you! Here, some gold!  
```sql
UPDATE INHABITANT
SET gold = gold + 120
WHERE personid = 20;
```

QUESTION: Unfortunately, that's not enough gold to buy a sword. Seems like I do have to work after all. Maybe it's not a bad idea to change my name from Stranger to my real name before I will apply for a job.  
```sql
UPDATE INHABITANT
SET name = Ahmed
WHERE name = 'Stranger';
```

QUESTION: Since baking is one of my hobbies, why not find a baker who I can work for?  
```sql
SELECT *
FROM INHABITANT
WHERE job = 'baker'
ORDER BY gold DESC;
```

[...] (truncated here to avoid large output, but it continues with similar format)
