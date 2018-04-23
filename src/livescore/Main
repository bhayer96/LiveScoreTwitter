public class Main {

   public Main()
   {
   
      CS321_readFile rf = new CS321_readFile(); //file reader object
      LiveScore bot = new LiveScore();
      TwitterConnect twitter_path = new TwitterConnect(bot);
      GetData gd;
      String holder = "";
      
      try{
         requestDMs();
         holder = rf.loadFile("out.txt");
         twitter_path.buildUserFile(holder);
         
         requestUserName(bot.getMessageSender());
         holder = rf.loadFile("post.txt");
         bot.setMessageSender(twitter_path.translateUserName(holder));
         bot.storeUserFile();
         System.out.println(bot.getDesiredTeam());
         gd = new GetData(false, "fox-sports", bot.getDesiredTeam(), 1, "583d233722744e44954d03a1f4653c88");
         bot.delimitForTweet(gd.getFinalMessage());
         System.out.println(gd.getFinalMessage());
         
      }catch(Exception e){
      	
         System.out.println("Main file fail");
         
      }
   
   }
   
   public void requestUserName(String message_sender)
   {
      	  
      Runtime rt = Runtime.getRuntime();
      	   
      try{
         Process pr = rt.exec("cmd /c twurl -X GET /1.1/users/show.json?user_id=" + message_sender + " > post.txt");
         pr.waitFor();
         
      }
      catch(Exception e){
         System.out.println("Failed to translate username");
      }
   
   }
   
   public static void requestDMs(){
      	  
      Runtime rt = Runtime.getRuntime();
      	   
      try{
         Process pr = rt.exec("cmd /c twurl -X GET /1.1/direct_messages/events/list.json > out.txt");
         pr.waitFor();
      }
      catch(Exception e){
         System.out.println("Request to DM's failed");
      }
   }
	
   public static void main (String[] args){
   	
      Main m = new Main();
   
   }
	
}
