# Execute_GCP_DF_from_local
Execute the google Dataflow from local (windows) using Anaconda prompt(python)


# Steps to set up 
1.Install the Anaconda in your local windows system. Please Refer https://docs.anaconda.com/anaconda/install/windows/

2.Open the Anaconda command prompt to deploy the Apache beam and google cloud pakages. please Refer https://beam.apache.org/get-started/quickstart-py/

3.You can ignore Install Python virtual environment

4.Install the "pip install apache-beam[gcp]" for doing the operation with google cloud

5.Execute a pipeline using below command. Apache beam will use your local system paths to process.

python -m apache_beam.examples.wordcount --input /path/to/inputfile --output /path/to/write/counts

6.As part of the initial setup, install Google Cloud Platform specific extra components. Make sure you
  complete the setup steps at /documentation/runners/dataflow/#setup
  
  pip install apache-beam[gcp]
  
python -m apache_beam.examples.wordcount --input gs://dataflow-samples/shakespeare/kinglear.txt \
                                         --output gs://<your-gcs-bucket>/counts \
                                         --runner DataflowRunner \
                                         --project your-gcp-project \
                                         --region your-gcp-region \
                                         --temp_location gs://<your-gcs-bucket>/tmp/
  
 7.Befor execute the above script you need to set the enviromnemt variable in your local system to connect the Google cloud project through service account.
  
  ->create service account in your google cloud project and provide access to create DF job and create/access to storage.
  
  ->download the json key from the SA.
  
  ->set your local environment varible using the path of SA json key file. e.g.   GOOGLE_APPLICATION_CREDENTIALS="C:\Users\username\Downloads\service-account-file.json"
  

