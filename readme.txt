If you want to see the project in action watch this  youtube video I made : https://youtu.be/bnWyXeqFG4Q
Since Github does not support projects with size more than 100 MB, I had to upload the project on Google Drive because it have size of =~ 3.10GB in total, to clone the project you need to just download it from Google Drive From this link : https://drive.google.com/drive/folders/1nh8G--oMrFA9q4MYoaf6hlOa1YQ7XrvK?usp=sharing then unzip it in a folder, after doing that open cmd (command line) and go to the location of the files and activate the environment called "env" by typing "env\scripts\activate" after that type "python run_webapp.py" to run the web app. Make sure you already installed virtualenv if you didn’t just run “pip install virtualenv” on the command line. 

Project’s Big Picture: I just tried to build a model that given review from a google play store app it predicts the score of that comment or in other words the number of stars the user put on that comment 


How I got the Data? I’ve scraped comments and their scores from different apps  (around 400 app) with different categories. The result was like +200K samples, I only took 125K so the data become balanced (25K instances per label) 
How did I do the Preprocessing? I tried 3 Preprocessing pipelines:
	1) I just removed the emojis since their encoding will have the same value no matter what the emoji is, and removed double spaces caused by removing emojis then trained a model 
	2) Preprocessing with lemmitazing and segmenting entities in the text then trained a model
	3) No Preprocessing then trained a model
Most of models I’ve tested performed better when I don’t preprocess the documents at all so I didn’t preprocess the documents to train the final model.
Which Models I tried? I’ve tried Gradient Boosting (with BERT Vectorization & GloVe), LSTM(with BERT Vectorization & GloVe)  and BERT model.
The best results were in BERT then Gradient Boosting then LSTM 
=> Which model I choose? : I choose the BERT model since it was the best to perform on the validation even though it takes more time than the other models to make predictions and since I only cared about the performance not the speed of the prediction.
Metrics : I've used Accuracy as a metric because my data was balanced and my goal was to classify the most reviews correctly not to fully make the model distinguish between all scores since score 4 is so close to be a 5 and 2 was so close to be 1 in other words score 5 and 4 overlap and score 2 and 1 overlap…

Building the UI (User Interface) : I had basic knowledge of Javascript and HTML so I’ve used that. I also had to learn Flask framework along with Jinja Syntax and Basic JQuery like AJAX requests (this part took most time since I was fairly new to web development) 
