
public class Main {

	
	public static void main (String[] args){
		
		CS321_readFile test = new CS321_readFile(); //file reader object
		TwitterConnect twitter_path = new TwitterConnect();
		
		try{
		command();
		twitter_path.buildUserFile(test.loadFile("C:/Users/Nathan Tefera/workspace/Project321/out.txt"));
		}catch(Exception e){
			
		System.out.println("Main file fail");
		}
	
	
	}
	
	public static void command(){
	   	  
	      Runtime rt = Runtime.getRuntime();
	   	   
	      try{
	         Process pr = rt.exec("cmd /c twurl -X GET /1.1/direct_messages/events/list.json > out.txt");
	         pr.waitFor();
	      }
	      catch(Exception e){
	      	   System.out.println("Where do i go from here");
	      }
	}
	
	
}
