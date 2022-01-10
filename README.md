# Semi-Automated Data Processing
Preparing data for model learning is one of the most important steps in any project—and traditionally, one of the most time consuming. Data Analysis plays a very important role in the entire Data Science Workflow. In fact, this takes most of the time of the Data science Workflow. There’s a nice quote (not sure who said it)According to Wikipedia, In statistics, exploratory data analysis (EDA) is an approach to analyzing data sets to summarize their main characteristics, often with visual methods. A statistical model can be used or not, but primarily EDA is for seeing what the data can tell us beyond the formal modeling or hypothesis testing task. Exploratory data analysis was promoted by John Tukey to encourage statisticians to explore the data, and possibly formulate hypotheses that could lead to new data collection and experiments.“In Data Science, 80% of time spent prepare data, 20% of time spent complain about need for prepare data.”

This projects handles the task with minimal user interaction by analyzing your data and identifying fixes, screening out fields that are problematic or not likely to be useful, deriving new attributes when appropriate, and improving performance through intelligent screening techniques. You can use the project in semi-interactive fashion, previewing the changes before they are made and accept or reject them as you want. **All these steps has to be carried out by the user by calling the several functions as follows:**<br />
<br />
**1) identify_feature(data)=**<br />  This function identifies the categorical, continuous numerical and discrete numerical features in the datset. It also identifies datetime feature and extracts the relevant info from it.<br />
>**Input:**<br />
  >data=Dataset<br />
>**Output:**<br />
  >df=Dataset<br />
  >data_cont_num_feature= List of features names associated containing continuous numerical values<br />
  >data_dis_num_feature=List of features names associated containing discrete numerical values<br />
  >data_cat_feature=List of features names associated containing categorical values<br />
  >dt_feature=List of features names associated containing datetime values<br />
  
 2) plot_nan_feature(data, continuous_features, discrete_features, categorical_features,dependent_var)=It identifies the missing values in the dataset and visualize them their impact on dependent feature.
  Input:
  data=Dataset
  continuous_features= List of features names associated containing continuous numerical values
  discrete_features=List of features names associated containing discrete numerical values
  categorical_features=List of features names associated containing categorical values
  dependent_var= Dependent feature name in string format
  Output:
  df= Dataset
  nan_features= List of feature names containing NaN values
  
 3) visualize_imputation_impact(data,continuous_features, discrete_features, categorical_features,nan_features,dependent_var):The function visualizes the impact of different NaN value impution on the distribution of values the feature.
Input:
data=Dataset
  continuous_features= List of features names associated containing continuous numerical values
  discrete_features=List of features names associated containing discrete numerical values
  categorical_features=List of features names associated containing categorical values
  nan_features= List of feature names containing NaN values
  dependent_var= Dependent feature name in string format
Output:
  None
4) nan_imputation(data,mean_feature,median_feature,mode_feature,random_feature,new_category):The function imputes the NaN values in the feature as per the user input.
Input:
data=Dataset
mean_feature= List of feature names in which we have to carry out mean_imputation
median_feature=List of feature names in which we have to carry out median_imputation
mode_feature=List of feature names in which we have to carry out mode_imputation
random_feature=List of feature names in which we have to carry out random_imputation
new_category=List of feature names in which we we create a new category for the NaN values
5) cross_visualization(data,continuous_features,discrete_features, categorical_features,dt_features):The function visualise the relationship between the different independent features
Input:
df=Dataset
  data_cont_num_feature= List of features names associated containing continuous numerical values
  data_dis_num_feature=List of features names associated containing discrete numerical values
  data_cat_feature=List of features names associated containing categorical values
  dt_feature=List of features names associated containing datetime values
 Output:
 continuous_features2=List of features names associated containing continuous numerical values, except the dependent feature
6) dependent_independent_visualization(data,continuous_features,discrete_features, categorical_features,dt_features,dependent_feature): The function visualise the relationship between the different independent features.
Input:
data_cont_num_feature= List of features names associated containing continuous numerical values
  data_dis_num_feature=List of features names associated containing discrete numerical values
  data_cat_feature=List of features names associated containing categorical values
  dt_feature=List of features names associated containing datetime values
  dependent_var= Dependent feature name in string format
 Output:
 None
7) outlier_removal(data,continuous_features,discrete_features,dependent_var,dependent_var_type,action): The function visualizes the outlliers using the boxplot and removes them
data=Dataset
  continuous_features= List of features names associated containing continuous numerical values
  discrete_features=List of features names associated containing discrete numerical values
  dependent_var= Dependent feature name in string format
  dependent_var_type= Contain string tells if the problem is regression (than use 'Regression') or else
  action= Give input as 'remove' to delete the rows associated with the outliers
  Output:
  df=Dataset
 8) transformation_visualization(data,continuous_features,discrete_features,dependent_feature): The function visualize the feature after performing various transormation techniques.
 Input:
 data=Dataset
  continuous_features= List of features names associated containing continuous numerical values
  discrete_features=List of features names associated containing discrete numerical values
  dependent_feature= Dependent feature name in string format
 Output:
 None
 10) feature_transformation(train_data,test_data,continuous_features,discrete_features,transformation,dependent_feature): The function performing the feature transormation technique as per the user input.
 Input:
 train_data=Training dataset
 test_data=Test dataset
 continuous_features= List of features names associated containing continuous numerical values
  discrete_features=List of features names associated containing discrete numerical values
  transformation=Type of transformation:
                                        none=No transformation
                                        log=Log Transformation
                                        sqrt= Square root Transformation
                                        reciprocal= Reciprocal Transformation
                                        exp= Exponential Transformation
                                        boxcox=Boxcox Transformation
  dependent_feature= Dependent feature name in string format
  Output:
  X_data=Training dataset
  t_data=Test dataset
  11) categorical_transformation(train_data,categorical_encoding): This function transforms the categorical featres in the numerical ones using encoding techniques.
  Input:
  train_data=Training dataset
  categorical_encoding={'one_hot_encoding':[],'frequency_encoding':[],'mean_encoding':[],'target_guided_ordinal_encoding':{}}
  Output:
  X_data=Training dataset
  12) feature_selection(Xtrain,ytrain, threshold, data_type, filter_type): This function performs the feature selection based on the dependent and independent features.
 Input:
 Xtrain=Training dataset
 ytrain=dependent data in training dataset
 threshold= Threshold for the correlation
{'in_num_out_num':{'linear':['pearson'],'non-linear':['spearman']},
                   'in_num_out_cat':{'linear':['ANOVA'],'non-linear':['kendall']},
                   'in_cat_out_num':{'linear':['ANOVA'],'non-linear':['kendall']},
                   'in_cat_out_cat':{'chi_square_test':True,'mutual_info':True},}
data_type= Data linear or non-linearly dependent on the output label
filter_type= If input data is numerical and output is numerical then --'in_num_out_num' as shown in the above dictionary
 Output:
 Xtrain= Training dataset
 feature_df= Dataframe containig features with their pvalue 
 13) convert_dtype(data,categorical_features):This function converts the categorical fetaures containing the numeric values but presented as categorical into the int format.
 Input:
 data= Dataset
 categorical_features=List of features names associated containing categorical values
 Output:
 df=Dataset
