#load features list and activity labels
features=read.table("features.txt")
activity_labels=as.data.frame(read.table("activity_labels.txt"))

#load subject train set and measurements for train set
subject_train=read.table("train/subject_train.txt",col.names="subject_id")
x_train=read.table("train/X_train.txt",col.names=as.character(features[,2]))

#get mean(), Mean() and std() variables from measurements set
mean=grep("mean",names(x_train),value=TRUE)
Mean=grep("Mean",names(x_train),value=TRUE)
std=grep("std",names(x_train),value=TRUE)
final_labels=c(mean,std,Mean)
#removes the columns that should not be included in the tidydata set
x_train_f=x_train[,c(final_labels)]

#load train activity data set
y_train=read.table("train/y_train.txt",col.names="activity")

#Change activity(number) to text category labels and convert to factor
for (i in 1:dim(y_train)[1])
{
 y_train[i,]= as.character(activity_labels[y_train[i,1],2])
}
y_train[,1]=as.factor(y_train[,1])

#build train dataset with subject_id, activity, and measurements
train=cbind(subject_train,y_train,x_train_f)



#load subject test set and measurements for test set
subject_test=read.table("test/subject_test.txt",col.names="subject_id")
x_test=read.table("test/X_test.txt",col.names=as.character(features[,2]))

#get mean() and std() variables from measurements set
mean=grep("mean",names(x_test),value=TRUE)
Mean=grep("Mean",names(x_test),value=TRUE)
std=grep("std",names(x_test),value=TRUE)
final_labels=c(mean,std,Mean)
x_test_f=x_test[,c(final_labels)]

#load test activity data set
y_test=read.table("test/y_test.txt",col.names="activity")
#Change activity(number) to text category labels and convert to factor
for (i in 1:dim(y_test)[1])
{
 y_test[i,]= as.character(activity_labels[y_test[i,1],2])
}
y_test[,1]=as.factor(y_test[,1])

#build test dataset with subject_id, activity, and measurements
test=cbind(subject_test,y_test,x_test_f)

#Build dataset by merging train and test datasets
data=rbind(train,test)
rm(x_test,y_test,x_train,y_train,x_train_f,x_test_f,train,test,subject_train,subject_test,features,final_labels,std,mean,Mean,i)


a=1
b=data.frame(NULL)
c=data.frame(NULL)
d=data.frame(NULL)
tidydata=data[NULL,]
for (i in 1:max(data$subject_id))
{
 for (j in 1:dim(activity_labels)[1])
 {
  
  b=subset(data,subject_id==i & activity==as.character(activity_labels[j,2]))
  c=sapply(b[,3:length(data)],mean)
  
  tidydata[a,]=c(i,as.character(activity_labels[j,2]),c)
  a=a+1
  
 }
 
}
rm(a,b,c,d,i,j,data,activity_labels)
