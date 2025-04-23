# DSGA1019
1. Install the Google Cloud SDK if you haven't already. You can download it from the Google Cloud website.
   
2. Authenticate with Google Cloud:
```
gcloud auth login
```

3. Set your project ID:
```
gcloud config set project YOUR_PROJECT_ID
```

4. Create a bucket in Google Cloud Storage:
```
gsutil mb gs://your-dataset-bucket-name
```

5. Upload your CSV file directly to GCS:
```
gsutil cp /path/to/sentiment140.csv gs://your-dataset-bucket-name/
```

6. To ensure your GitHub repository has references to the dataset without storing the actual data, create a small text file in your repo (e.g., dataset_location.txt) that contains the GCS path:
```
gs://your-dataset-bucket-name/sentiment140.csv
```

7. Add and commit this small reference file:
```
echo "gs://your-dataset-bucket-name/sentiment140.csv" > dataset_location.txt
git add dataset_location.txt
git commit -m "Add reference to dataset in GCS"
git push origin main
```

This approach has several advantages:

No file size limitations to worry about
Direct access from Dataproc and other GCP services
Better performance for distributed processing
Proper separation of code (GitHub) and data (GCS)
