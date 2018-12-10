import pandas as pd
import datetime
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

def hetedik_feladat(datafilename, resultdiagramname):
    df = pd.read_csv(datafilename, parse_dates=["datetime"],sep=';', index_col=0)
    df["day"] = df.index.date
    df["month"] = df.index.month
    df["year"] = df.index.year
    df = df[df.year==2014]
    df = df.groupby("day").mean()
    df["temp_sf"] = df["temp_sf"] - 273.15
    df["temp_la"] = df["temp_la"] - 273.15
    df["temp_lv"] = df["temp_lv"] - 273.15
    labels= ["temp_sf","temp_la","temp_lv"]

    plt.figure(1, figsize=(20,20))

    a=1
    for x in range(3):
        for y in range (3):
            plt.subplot(3,3,a)
            if x == y:
                plt.title("Column: "+ labels[x] )
                sns.distplot(df[labels[x]])
            elif x>y:
                plt.title(labels[x]+"  vs  "+ labels[y])
                plt.plot(df.index, df[labels[x]], color="r")
                plt.plot(df.index, df[labels[y]], color="b")
            else:
                plt.title(labels[x]+"  vs  "+ labels[y])
                plt.scatter(df[labels[x]], df[labels[y]], c=df.month)
            a+=1
    plt.savefig(resultdiagramname)
