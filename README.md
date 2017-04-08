First of all i create a local directory to work on my project using filesPath() function.Then i set my current working directory to this directory using the setwd() function.
Next i download and extract the Dataset.zip file from which i get the data to creat a tidy data set using the download.file() and unzip() functions .
		# Names after
Now load all the required packages i.e dplyr , data.table , tidyr using the library() function.
		#Load required packages

Next I creat data tables for the file that exists in the Dataset.zip file using tbl_df function , one each for SubjectTrain , SubjectTest , ActivityTest , ActivityTrain , DataTrain , DataTest.
		#Read subject files
		#Read activity files
		#Read data files

Nnow I merge the training and test sets to create a single data set.
	SubjectTrain + SubjectTest = all Subject data
	ActivityTest + ActivityTest = all Activity data
	DataTrain + DataTest = all data 
		#for both Activity and Subject files this will merge the training and the test sets by row binding 
			
		#and rename variables "subject" and "activityNum"
			using rbind() and setnames()  function
		#combine the DATA training and test files
			using rbind() function
		#name variables according to feature e.g.(V1 = "tBodyAcc-mean()-X")
			using setnames() colnames() names() function
		#column names for activity labels
			using setnames() read.table() names() functions
		# Merge columns
			using cbin()
Now I extract only the measurements on the mean and standard deviation for each measurement
		# Reading "features.txt" and extracting only the mean and standard deviation  #var name
			using grep() function
		# Taking only measurements for the mean and standard deviation and add "subject","activityNum"
			using union() and subset() functions

Then I use descriptive activity names to name the activities in the data set.
		#enter name of activity into dataTable 
			using merge() as.character() functions
		#create dataTable with variable means sorted by subject and Activity
			using as.character() aggregate() tbl_df(arrange()) functions

Now I appropriately labels the data set with descriptive variable names.
		#Names before	
		#Names after	 using name() and gsub() function	

From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
		#write to text file on disk

