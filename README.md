# CORMAC-Test


A. There might be more than a fixed set of attributes and outcomes that appear in these returned dictionaries, but for convenience and good readability here, I set assumptions as follows:


1. Assume that a fixed set of attributes of the procedure itself (appearing in the returned dictionary - get_procedure_attributes(procedure_id = None)) includes:

'procedure_id', 'type of procedure', 'how long it lasted', 'severity of the condition being addressed'.


2. Assume that a fixed set of granular measures of outcomes (appearing in the returned dictionary - get_procedure_outcomes(procedure_id) ) includes:


'severity of post procedure complications', 'pain', 'recurrence of original condition'.


3. Each procedure will not always have data for all attributes or outcomes above. For such procedures, missing values of attributes or outcomes in the returned dictionaries will be 'None'. 

For example, when procedure_id = '123' and this procedure doesn't have all attributes above, the output of the dictionary( get_procedure_attributes('123) ) is {'procedure_id': '123', 'type of procedure': None, 'how long it lasted' : None, 'severity of the condition being addressed' : None}.


4. Assume the number of procedure ids /observations in the dataset is n (which is an integer).


B. For classifier algorithm chosen, I select the Random Forest classifier due to the following reasons:

     1. this classifier algorithm can overcome overfitting problems;
     2. it works good for both categorical and continuous values.
     3. it can automatically handle missing values in the data.
