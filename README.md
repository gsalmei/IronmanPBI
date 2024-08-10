Ironman World Championship Until 2019

This project aims to create a dashboard with the results of the Ironman World Championship up to the year 2019.

To achieve this, the following questions were defined to be answered:

1 - According to the year, who were the winners, their times, and their nationalities?

2 - Who are the athletes with the most victories?

3 - Which countries have the most winners?

4 - According to the year, who were the athletes on the podium?

5 - What was the evolution, in the last 10 years, of the time it took for the winning athlete to complete the race?

Design

The dashboard design was created using Figma, referencing the Ironman website, primarily using the colors red, black, and white for the background of the charts.
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/a1accdf3-9d07-4bec-ace6-56aabc32cb8d)


Answering the Business Questions:

1 - According to the year, who were the winners, their times, and their nationalities?
To answer this question, cards filtered by year were used, as shown in the image below.
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/840e367a-9a07-42d1-9f5b-2e94a2f7d83a)

2 - Who are the athletes with the most victories?
In this case, a clustered side-by-side bar chart by gender was used.
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/20478d89-240f-42a8-bc74-385882f9ffbc)


3 - Which countries have the most winners?
Following the same idea as the previous question, a bar chart was also used, but instead of the athlete's name, the country code was displayed.
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/4f56901a-cac1-4baa-95b2-13c91b42e6c9)


4 - According to the year, who were the athletes on the podium?
Here, a table summarizing the data was used.
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/7db778f8-1a53-4184-8ce3-258cea4f4978)

5 - What was the evolution, in the last 10 years, of the time it took for the winning athlete to complete the race?
To answer this question, several steps were followed, described below:

1 - Create a table with the years available in the database to create the X-axis;

2 - Create a calculated column to have numeric values of the finish time. This measure converts the total time into seconds;
  
    Time Seconds = 
    HOUR(IM[Time])* 3600 + MINUTE(IM[Time]) * 60 + SECOND(IM[Time])
  
3 - Create a measure to convert the time into a string and use it as a data label in the line chart.
      
      Time Formated = 
      VAR TotalSegundos = SUM('IM'[Time Seconds])
      VAR Horas = INT(TotalSegundos / 3600)
      VAR Minutos = INT(MOD(TotalSegundos, 3600) / 60)
      VAR Segundos = MOD(TotalSegundos, 60)
      RETURN
      FORMAT(Horas, "00") & ":" & FORMAT(Minutos, "00") & ":" & FORMAT(Segundos, "00")
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/63692a5d-f7a3-46a1-a811-ef8c76e1e2cb)

As a final result, we obtained the dashboard below:
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/1c8918d0-337b-454e-b271-ea061dbdfa9d)


Link to access the report:


https://app.powerbi.com/view?r=eyJrIjoiMzg5MGFjYzctM2Y2Ni00MGE2LWEzNjAtZmZmMWJlNWVhOWYzIiwidCI6IjkxYTZhNTY5LTM0ZmItNGNiNC05OWE1LWIwMDllNjhlZTU1NSJ9


