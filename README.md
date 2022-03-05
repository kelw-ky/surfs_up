# surfs_up

## Overview 
We are using Python, Pandas functions and methods, and SQLAlchemy to see June and December temperature in order to determine if the surf and ice cream shop business is sustainable year-round.

## Results 
- The average temperature is lower in December than in June from around 71 F to 75 F. 
- The max temperature is 85 F and 83 F in June and December respectively.
- The minimum temperature is 56 F and 64 F in December and June respectively. 

![June_df](/Resources/June_df.png)  ![Dec_df](/Resources/Dec_df.png)

      June df.describe()                  December df.describe()

## Summary
Base on the two charts above, we can suggest to W. Avy that the surf and ice cream shop business can be sustainable year-round as the temperatures are relatively similar in June and December. Even though, the minimum temperature can hit pretty low, these temperatures usually hit at night as should not affect the business that much. 

### Additional Query #1: Finding Jun and Dec precipiation 

The following code was used to find June and December precipiation: 
june_prcp_temp = session.query(Measurement.date, Measurement.tobs, Measurement.prcp).\
                                                    filter(extract('month',Measurement.date) ==6).all()
june_prcp_temp_df = pd.DataFrame(june_prcp_temp,columns=['date','June Temperature','June Precipication'])
june_prcp_temp_df.describe()

Chart Outcome:

![Jun_Temp_Prep](/Resources/Jun_Temp_Prep.png)

dec_prcp_temp = session.query(Measurement.date, Measurement.tobs, Measurement.prcp).\
                                                    filter(extract('month',Measurement.date) ==12).all()
dec_prcp_temp_df = pd.DataFrame(dec_prcp_temp,columns=['date','Dec Temperature','Dec Precipication'])
dec_prcp_temp_df.describe()

Chart Outcome:

![Dec_Temp_Prep](/Resources/Dec_Temp_Prep.png)

### Additional Query #2: June and December Box and Whisker
june_boxplot = june_prcp_temp_df.boxplot(column=['June Temperature','June Precipication'])  
plt.tight_layout()
plt.title('June Box and Whisker')

![June_Box](/Resources/June_Box.png)

dec_boxplot = dec_prcp_temp_df.boxplot(column=['Dec Temperature','Dec Precipication'])
plt.tight_layout()
plt.title('December Box and Whisker')

![Dec_Box](/Resources/Dec_Box.png)

