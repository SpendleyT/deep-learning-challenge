# Deep Learning Challenge

<h2>Overview</h2> 

<p>The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. From Alphabet Soup’s business team, you have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization. 

The goal of this activity is to create a neural-network(NN) model that will predict success for groups requesting funding based on a variety of details. The focus will be to identify which values are critical to best predicting eventual success based on the past performance of Alphabet Soup's grantees.</p>


<h2>Results</h2> 
<p>The following steps were executed in the detemination process:

<h4>Data Preprocessing</h4>
<p>From the data provided, the target column for testing the model being build is the 'Is Successful' column, identifying those groups previously successful after receiving a grant.</p>

<p>Before processing , two (2) categories were removed from the dataset - the Identification Number (EIN) and the Group Name (NAME). These would not provide any additional differentiation as they could not be seperated into comparative bins.</p>

<p>The remaining columns (listed below) were then processed to prepare them for use within the NN model by converting them into relevant options (through grouping of outliers) or through classification via the "get_dummies" method of splitting values into columns. 

<p>Categories for modeling:</p>
<ul>
<li>APPLICATION_TYPE—Alphabet Soup application type</li>
<li>AFFILIATION—Affiliated sector of industry</li>
<li>CLASSIFICATION—Government organization classification</li>
<li>USE_CASE—Use case for funding</li>
<li>ORGANIZATION—Organization type</li>
<li>STATUS—Active status</li>
<li>INCOME_AMT—Income classification</li>
<li>SPECIAL_CONSIDERATIONS—Special considerations for application</li>
<li>ASK_AMT—Funding amount requested</li>
</ul>

<h4>Compiling, Training, and Evaluating the Model</h4>

<p>For the initial modeling attempt, the decision was made to use a total of 3 layers (2 hidden and 1 output layer). This was to provide some reduction of options at each pass, by using 80 and 40 units respectively in the hidden layers with relu processing, with an output layer utilizing sigmoid processing.</p>

<p>Following the first run for the model, the evaluation process (utilizing the NN.evalute method) resulted in a 73.7% accuracy. This did not meet the 75% threshold mandated by the client, and so a number of optimization steps were attempted. 

<h4>Optimization Actions</h4>
<p>Given the gap between the actual and the targeted accuracy rates, a number of model train/predict runs were then undertaken after each of the actions described below:</p>
<ul>
<li>Reduce Application Types to reduce # of bins (from &lt;500 to &lt;1000) </li>
<li>Add a 3rd hidden layer (additional combinations)</li>
<li>Moved epochs to 120 (had the model not processed far enough?)</li>
<li>Increase units in second layer and remove 3rd layer (alternate to option #2)</li>
<li>Increase Application Types to increase # of bins from &lt;500 to &lt;100 (Opposite of #1)</li>
<li>Increase Classification Types further (&lt;100). Was Classification more impactful than Application types?</li>
</ul>

<h2>Summary</h2>

<p>Regardless of the optimization selections, the model accuracy continued to hover around the 73.7% of the first attempt (&plusmn;0.05%). This could be due to the nature of the data or that the model-type being utilized here is not the best option. In an effort to improve the predicition accuracy, the data could pass through similar pre-processing and then run through a different model type (Logiistic Regression, Random Forest or other).</p>

<p><b>Suggestion:</b> Use the Random Forest model, given that all of the data is classification data (either yes/no or binned). Trees for each value would be easily split into individual results that overall could provide a consensus result.</p>

