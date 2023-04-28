# pandas-challenge
This repository contains the code for a Jupyter Notebook that goes through a set data set of schoools and provides details based on factoers like buegt, school size, school type and test scores. The repository also contains the datasets used as CSV's and a Word Document of the written report.

The following code was devised from: https://stackoverflow.com/questions/17071871/how-do-i-select-rows-from-a-dataframe-based-on-column-values

school_types = school_data_complete.loc[(school_data_complete["type"] == "District") | (
                                         school_data_complete["type"] == "Charter"), ["school_name", "type"]]
school_types = school_types.drop_duplicates(subset=["school_name"])


The following code was devised from: https://pandas.pydata.org/docs/reference/api/pandas.concat.html & https://stackoverflow.com/questions/18062135/combining-two-series-into-a-dataframe-in-pandas

per_school_summary = pd.concat([per_school_counts,per_school_capita,per_school_passing_reading, overall_passing_rate,per_school_passing_math], axis=1,join = "inner")


https://sparkbyexamples.com/pandas/pandas-merge-multiple-dataframes-2/

per_school_summary = pd.merge(pd.merge(school_types, per_school_summary,how="left", on="school_name"),per_school_budget["budget"],on="school_name")
per_school_summary = pd.merge(pd.merge(per_school_math["math_score"], per_school_summary,how="left", on="school_name"),per_school_reading["reading_score"],on="school_name")


https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.rename_axis.html
per_school_summary = per_school_summary.rename_axis("school_name")
per_school_summary = per_school_summary.rename_axis("")

https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.drop_duplicates.html
school_types = school_types.drop_duplicates(subset=["school_name"])

https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.set_index.html
school_types = school_types.set_index("school_name")
