# Email-Spam-Detection
#KNN Classifier 
#Cosine Similarity
###Feature selection For the KNN classifier, we also select all the words as the feature. However, I did some improvement when compute the K Nearest Neighbors.

For usual method, we create a dictionary to record all the words appeared. If the length of the dictionary is N, for every email, we create a vector of length N. Every index of the vector corresponds to one word. If the word appears in the email, we’ll set the corresponding index 1. If not, 0.

But, there is a problem. When we compute the distance later, we use the formula as following:

                 Cosine Distance(i,j)=(V_i*V_j)/(|V_i |*|V_j |)
As the vector has a length of N, which can be more thousands, it will take a lot of time to compute the distance of the unknown email to all other training emails. For my experiment, the time is unacceptable. So, we can change it a little bit.

The key of KNN method is to find the neighbors which are nearest. Instead of compute the distance directly, we could compute the similarity. If two emails have greater similarity, we can say they are more near.

Here is how we define similarity:

                     Cosine Similarity(i,j)=C/√(A+B)
Where A is the number of terms in email I, B is the number of terms in email B, and C is the number of terms that email i and j both have. ###Implement

For every email in testing set, split it and get the words in it.
After that, compute the similarity of this email to any email in training set.
Sort the training set by similarity and select the K nearest neighbors.
For the K nearest neighbors, classify the email as the class which has the most number of neighbors.
###Experiment Accuracy: 78.125% (when K=11)

#Eucledian Distance
1. Load the spam and ham emails
2. Remove common punctuation and symbols
3. Lowercase all letters
4. Remove stopwords (very common words like pronouns, articles, etc.)
5. Split emails into training email and testing emails
6. For each test email, calculate the similarity between it and all training emails
    6.1. For each word that exists in either test email or training email, count its frequency in both emails
    6.2. calculate the euclidean distance between both emails to determine similarity
7. Sort the emails in ascending order of euclidean distance
8. Select the k nearest neighbors (shortest distance)
9. Assign the class which is most frequent in the selected k nearest neighbours to the new email.
###Experiment Accuracy :71.875
