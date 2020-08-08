# Geo-index-and-Image-Recognition-based-Social-Network
I used Go programming language to build a geo-based social network web application based on Google Cloud Platform. 
This project allows users to submit a post that can include a message, geolocation, and media file, search nearby posts based on their current location and 
find all posts whose media file is a photo of a face.

## How to Run 

1. Setup your GCE instance and Launch a GCE Instance
2. Install Go 
3. Install related Go-based libraries
4. Create Google Kubernetes Engine
5. Build Docker image
6. Deploy Docker image to GKE Cluster


## About the Service

I use Go to build a web service that has three main APIs: post, search, and cluster. 
1. The post API allows users to submit a post that can include a message, geolocation, and media file. 
2. The search API allows users to search nearby posts based on their current location. 
3. The cluster API allows users to find all posts whose media file is a photo of a face.



### Google Cloud Storage 
I use GCS to store all media files posted by users. The corresponding link of each media file is stored as metadata in Elasticsearch.

### Google Cloud Vision 
Used Google Vision API to provide a face detection model and integrate with the Go service

### Elasticsearch 
I use Elasticsearch as a NoSQL database to store data posted by users. In addition, I create a geo index for the geolocation of each 
post so that I can provide a quick geolocation-based search for my users. 

### JSON Web Token
I use JSON Web Token for server authentication. Why I used JWT rather than Session? 
1. Stateless, Scalable and Decoupled

Stateless: The back-end does not need to keep a record of tokens. 
Self-contained, containing all the data required to check its validity. No DB lookup is needed. 

2. Mobile Friendly

Native mobile platforms and cookies do not mix well. With a session-based approach, you simply store the session ID in a cookie. 

### Google Kubernetes Engine and why I use it 
I use GKE to deploy my Go service. I build my program into a docker image and run the image on virtual machines managed by my GKE cluster.  
I use GKE because it can help to make my service run in a cluster with multiple virtual machines, which improved the reliability of my service. 
Since my service is running on multiple virtual machines, a single failure of one virtual machine won’t affect the whole service.

### CICD
Deploy your docker image to DockerHub by CircleCI


Here are some endpoints you can call:
```
http://YOUR_GCE_EXTERNAL_IP_ADDRESS:9200/post
http://YOUR_GCE_EXTERNAL_IP_ADDRESS:8080/search?lat=37&lon=122
http://YOUR_GCE_EXTERNAL_IP_ADDRESS:8080/cluster?term=face
http://YOUR_GCE_EXTERNAL_IP_ADDRESS:8080/signup
http://YOUR_GCE_EXTERNAL_IP_ADDRESS:8080/login
```


