# Cloud SQL for PostgreSQL - Creating an Instance and Loading Data (Working Title)


## GSP629



![[/fragments/labmanuallogo]]



## Overview

In this lab you'll learn how to create and connect to a Google Cloud SQL PostgreSQL instance, load data from an existing PostgreSQL backup, and perform basic SQL operations using the Google Cloud Platform Console and the psql client to verify data characteristics.

OLD: In this lab you'll learn how to create and connect to a Google Cloud SQL PostgreSQL instance and perform basic SQL operations using the Google Cloud Platform Console and the psql client.


## Setup and Requirements




### Qwiklabs setup

![[/fragments/startqwiklab]]

![[/fragments/gcpconsole]]





## Create a Cloud SQL instance




Click on the menu icon in the top left of the screen to see the __Navigation menu__.

![742dc285f86cdd1f.png](img/742dc285f86cdd1f.png)

In the left menu of the Console, click on __SQL__.

![780d772292fb4b06.png](img/780d772292fb4b06.png)

Click __Create Instance__.

Click __PostgreSQL__, then __Next__.

Create your instance with the following settings:

* Enter myinstance for __Instance ID__.
* Enter a password for the postgres user. Save or remember this password, you'll need it in the next section.

![be5ab8687f97a392.png](img/be5ab8687f97a392.png)

Leave the default values for the other fields.

Click __Create__.

You are returned to the instances list. Your new instance is greyed out while it initializes and starts.

After a few minutes your instance is created and you can continue to the next section. If it seems to be taking a long time refresh your browser.

### Test Completed Task

Click __Check my progress__ to verify your performed task. If you have completed the task successfully you will granted with an assessment score.

<!--
<ql-activity-tracking step=1>
    Create a Cloud SQL instance
</ql-activity-tracking>
-->


## Test your Understanding

Below are multiple choice questions to reinforce your understanding of this lab's concepts. Answer them to the best of your abilities.

<ql-multiple-choice-probe stem="What PostgreSQL Database version used in lab to create Cloud SQL instance?"
                          optionTitles='[
                            "9.6",
                            "5.6",
                            "5.7",
                            "1.0"
                          ]'
                          answerIndex="0"
                          shuffle>
</ql-multiple-choice-probe>


## Connect to your instance using the psql client in the Cloud Shell




In the Google Cloud Platform Console, click the Cloud Shell icon in the upper right corner.

![55efc1aaa7a4d3ad.png](img/55efc1aaa7a4d3ad.png)

Then click "Start Cloud Shell".

At the Cloud Shell prompt, connect to your Cloud SQL instance by running:

```
gcloud sql connect myinstance --user=postgres
```

Enter your postgres password. __Note:__ The cursor will not move. Press __Enter__ when you're done typing.

You should now see the `psql` prompt.


## Upload data into the postgres database




Insert sample data into the postgres database:

```
CREATE TABLE guestbook (guestName VARCHAR(255), content VARCHAR(255),
                        entryID SERIAL PRIMARY KEY);
INSERT INTO guestbook (guestName, content) values ('first guest', 'I got here!');
INSERT INTO guestbook (guestName, content) values ('second guest', 'Me too!');
```

Retrieve the data:

```
SELECT * FROM guestbook;
```

You should now see:

```bash
 guestname   |   content   | entryid
--------------+-------------+---------
 first guest  | I got here! |       1
 second guest | Me too!     |       2
(2 rows)
postgres=>
```

You have created a Google Cloud SQL PosgreSQL instance and connected to it.


## Test your Understanding

Below are multiple choice questions to reinforce your understanding of this lab's concepts. Answer them to the best of your abilities.

<ql-multiple-choice-probe stem="What is the name of default database in Postgres Cloud SQL instance?"
                          optionTitles='[
                            "guestbook",
                            "postgres",
                            "information_schema",
                            "performance_schema"
                          ]'
                          answerIndex="1"
                          shuffle>
</ql-multiple-choice-probe>


## Congratulations!

### Finish Your Quest

![41ab6fa0d099216d.png](img/41ab6fa0d099216d.png)
![cloudsql-quest-badge.png](img/cloudsql-quest-badge.png)

Continue your Quest with [Baseline: Deploy & Develop](https://google.qwiklabs.com/quests/37) or [Cloud SQL](https://google.qwiklabs.com/quests/52). A Quest is a series of related labs that form a learning path. Completing this Quest earns you the badge above, to recognize your achievement. You can make your badge (or badges) public and link to them in your online resume or social media account. Enroll in [Baseline: Deploy & Develop](https://google.qwiklabs.com/quests/37/enroll) or [Cloud SQL](https://google.qwiklabs.com/quests/52/enroll) and get immediate completion credit if you've taken this lab.  [See other available Qwiklabs Quests](http://google.qwiklabs.com/catalog).

### Next Steps / Learn More

This lab is also part of a series of labs called Qwik Starts. These labs are designed to give you a little taste of the many features available with Google Cloud. Search for "Qwik Starts" in the [lab catalog](https://google.qwiklabs.com/catalog) to find the next lab you'd like to take!

![[/fragments/TrainingCertificationOverview]]

##### Manual Last Updated November 9, 2018

##### Lab Last Tested September 11, 2018

![[/fragments/copyright]]
