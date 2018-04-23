import java.net.*;
import java.io.*;
import net.sf.json.*;
import org.apache.commons.lang.exception.*;
import java.lang.*;

import java.util.Scanner;

public class TwitterConnect {

   Scanner scan = new Scanner(System.in);
   LiveScore bot;
	
   String consumer_key = "vqg9L1A1RLJT5yZ6GH1RHc6Bg";
   String consumer_secret_key = "SUN1VKDhJR8PseynsmywINiVuoJkfcIrefWbdmWhgQJbBLF6v9";
   String access_key = "O59PWPRqS7XlANA4bYFcyY44XFvxt6W";
   String acess_secret_key = "63MdTu0HfJ7CJHd5oH171vPNEkE5623aOBACthZkHstvN";
   String owner = "LiveScore321";
   String owner_id = "984128983863365632";
	
   public TwitterConnect(LiveScore bot)
   {
   
      this.bot = bot;
   
   }
	
   public void buildUserFile(String container) throws Exception{
   	
      try{
      	
         JSONObject x = JSONObject.fromObject(container); //reads in textfile as a JSONObject
      	
         JSONArray messages = (JSONArray)(x.get("events")); 
         JSONObject message_1 = messages.getJSONObject(0);
      	
      	
         JSONObject message_1_create = message_1.getJSONObject("message_create");
         JSONObject message_target = message_1_create.getJSONObject("target");         //unwraps appropriate JSONObjects
         JSONObject message_data = message_1_create.getJSONObject("message_data");
      	
      	
      	
         String message_1_id = (String)message_1.get("id");
         String message_text = (String)message_data.get("text");
         String message_sender = (String)message_1_create.get("sender_id"); //sets appropriate JSON Strings
      	
         // System.out.println(message_1_id);
         // System.out.println(message_text);
         // System.out.println(message_sender);
         
         String[] buffer = message_text.split(" "); //splits the message by white spaces and gets the first index.
         String team = buffer[0]; 
      	
                  	//sends data to Baldeep's code
      
         bot.setMessageSender(message_sender);
         bot.setDesiredTeam(message_text);
         
      }
      catch(Exception e){
      	
         System.out.print("Error building user file");
      	
      }
   	
   }
   
   public String translateUserName(String jsonData)
   {
   
      JSONObject ms = JSONObject.fromObject(jsonData);
      
      return (String)ms.get("screen_name");
   
   }

   
   public static String readURL(String webservice) throws Exception  //reads in urls
   {
         
      URL oracle = new URL(webservice);
         
      BufferedReader in = new BufferedReader(new InputStreamReader(oracle.openStream()));
      
      String inputLine;
      String result = "";
      
      while ((inputLine = in.readLine()) != null)
      {
         
         result = result + inputLine;
         
      }
         
      in.close();
      return result;
         
   }
   
}
