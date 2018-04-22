
package livescore;

import java.io.*;

public class LiveScore {

    /*
    Takes in JSON data that was already parsed into Strings. These Strings contain the username
    and the team preferance of a particular user. storeUserFile() creates a txt file for 
    each user, with the file name containing the username and the file contents containing
    team preferances. If a file already exists for a user, the boolean true passed into
    the FileWriter object allows the team preferences to be appended onto the end 
    of the exisitng file. There is no return for this function.
    */
    public void storeUserFile(String username, String desiredTeam){
        BufferedWriter out;
        
        // Write to a file of name "username".txt.
        try{
            out = new BufferedWriter(new FileWriter((username + ".txt"), true));
            out.write(desiredTeam);
            out.close();
        }
        catch (IOException e){
            System.out.println("Could not create user file or write data to it.");
        }
    }
    
    /*
    Given a string containing all the details of the tweet to be posted, delimit the
    string to split up the String into two separte parts needed to post a tweet: excerpt
    and url. This split will be done base on the string "~~~". Once the string has 
    been split, use postTweet() to post the two parts of the tweet. There is no return
    for this function.
    */
    public void delimitForTweet(String loadedVal){
   
      String excerpt; // Stores the message to be posted to Twitter.
      String url; // Stores the link to the article relevant to the message.
      
      // Split the loadedVal string to obtain the excerpt and url.
      String [] tweet = loadedVal.split("~~~");
      
      excerpt = tweet[0];
      url = tweet[1];
      
      // Post the tweet to the twitter using postTweet().
      postTweet(excerpt, url);
   
    }

    public void postTweet(String excerpt, String url){
        
    }

    public static void main(String[] args) {
        LiveScore bot = new LiveScore();
    }
    
}
