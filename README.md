# ClustCrypt
SM Zobaed Code of Submission to HPCC 2019


## Introduction
ClustCrypt is an approach to cluster encrypted unstructured data semantically. The approach is effective for secure search system that perform search over encrypted unstructured Big data. ClustCrypt approximates number of clusters based on the statistical characteristics of the uploaded encrypted dataset. Later, it builds cluster set to prune the central index topically. Subsequently, instead of exhaustive searching over the index, clustcrypt searches over the clusters. Clustcrypt is effective for performing meaningful search with fewer time overhead. 

If you are using clustcrypt, please cite the following paper:
```@inproceedings{clustcrypt,
  title={Clustcrypt: Privacy-preserving clustering of unstructured big data in the cloud},
  author={Zobaed, SM and Ahmad, Sahan and Gottumukkala, Raju and Salehi, Mohsen Amini},
  booktitle={Proceedings of the 21st International Conference on High Performance Computing and Communications (HPCC)},
  pages={609--616},
  year={2019},
  organization={IEEE}
} ```

## S3BD Running Instructions

S3BD is composed of two projects named Client Encrypted Search and Encrypted Search Server that act as client and cloud respectively.  
These two can be run on the same machine, or on two machines connected by a network.  There are three primary actions you can perform when running the system: Uploading documents, Partitioning the dataset into clusters, and Searching over the dataset.

## Uploading Documents

To start an upload, launch the cloud server and select upload as its action (the ``` -u ``` flag), and choose how they'll be uploaded based on your project configuration (``` -f ``` for cloud and client being on the same machine, ``` -n ``` for them being remote). Alternatively, launch the project from the command line with the two flags following as arguments.

Once the server is running, launch the client and select upload as its action (again, the ``` -u ``` flag).  To perform a batch upload, enter the path for the directory with the files.  Alternatively, run it in the commandline with ``` -u ``` and the path following as arguments.  Single file uploads are not currently supported.

## Partitioning Dataset

To start partitioning the dataset, launch the cloud server and select partition as its action (the ``` -p ``` flag).  The process will start automatically.  The console will display the progress of the partitioning.  Once the console notes that it is ready to connect to the client, launch the client, select partitioning as its action, and the files will be transferred.

## Searching

To start a search, launch the cloud server and select search as its action (the ``` -s ``` flag).  The cloud will begin loading relevant data.

Once the server is ready to accept a search, launch the client and select search as its action, then enter the desired search query.  The client's console should soon show the results of the search.

## Configuration details.

The config files for each project can be found in the utilities subdirectory of the src directory.  Most importantly:

### Client Project

  * cloudIP - the IP used to connect to the server. Use localhost if both projects are local.
  * socketPort - the socket used for data transfers. Ensure this is the same on both client and cloud.
  * calcMetrics - only set this to true if you are testing speeds.
  * numSearchedAbstracts - determines the number of abstracts and clusters that should be searched over.  Has a heavy impact on speed and accuracy.
  
### Cloud Project

  * socketPort - the socket used for data transfers.  Ensure this is the same on both client and cloud.
  * abstractIndexCound - the number of terms that will be included in an abstract index.
  * k - the number of clusters created during partitioning.
  * calcMetrics - only set this to true if you are testing speeds.

## How to Contribute
We welcome new features, extension, or enhancements of S3BD.

We are, in particular, looking for new collaborations to enhance the clustering policy. As extension, we are researching on clustering dynamic dataset instead of static datasets that have been used in this research. Please drop us an email if you are interested to collaborate. 

## Contacts
* [Dr. Mohsen Amini Salehi](http://hpcclab.org/index.php/contact-us/)
* [SM Zobaed](zobaedsakib@gmail.com)
