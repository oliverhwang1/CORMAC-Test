# CORMAC-Test


A. There might be more than a fixed set of attributes and outcomes that appear in these returned dictionaries, but for convenience and good readability here, I set assumptions as follows:


	1. Assume that a fixed set of attributes of the procedure itself (appearing in the returned dictionary - get_procedure_attributes(procedure_id = None)) includes:

	'procedure_id', 'type of procedure', 'how long it lasted', 'severity of the condition being addressed'.


	2. Assume that a fixed set of granular measures of outcomes (appearing in the returned dictionary - get_procedure_outcomes(procedure_id) ) includes:


	'severity of post procedure complications', 'pain', 'recurrence of original condition'.


	3. Each procedure will not always have data for all attributes or outcomes above. For such procedures, missing values of attributes or outcomes in the returned dictionaries will be 'None'. 

	For example, when procedure_id = '123' and this procedure doesn't have all attributes above, the output of the dictionary( get_procedure_attributes('123) ) is {'procedure_id': '123', 'type of procedure': None, 'how long it lasted' : None, 'severity of the condition being addressed' : None}.


	4. Assume the number of procedure ids /observations in the dataset is n (which is an integer). Each observation in the dataset has different procedure_id given different procedure attributes.


B. For classifier algorithm chosen, I select the Random Forest classifier due to the following reasons:

     1. this classifier algorithm can overcome overfitting problems;
     2. it works good for both categorical and continuous values.
     3. it can automatically handle missing values in the data.


C. How I would intend for my code to be run:

	- Script 1:

	1. The first thing is to figure out the number of procedure ids or observations in the dataset(in my assumption, I set the number to be n(integer) ). I use the number n to extract the data using the specified API (three functions), because "procedure_id" uniquely identifies each procedure for which data was collected. 
	2. Construct the dataframe based on the extraction above.
	3. Data cleaning and transformation (including dealing with missing values and categorical variables).
	4. Feature importance evaluation using Logistic Regression model with Minimum AIC.
	5. Data spliting into training and test sets. Then, construct the Randomforest model - rfc based on the training data and test the accuracy on the test set.
	
	- Script 2:
	1. Given the trained model = rfc and the trained features X_features = X.columns done in the script 1, and we also have a dictionary of procedure attributes:

		d = {'procedure_id': value1, 'type of procedure': value2, 'how long it lasted': value3, 'severity of the condition being addressed': value4, 'severity of post procedure complications': None, 'pain': None, 'recurrence of original condition': None}

	   Then a prediction of success (True or False) is running my function: prediction(rfc, X_features, d).
	
