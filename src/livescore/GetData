import java.awt.EventQueue;
import java.awt.EventQueue;

import javax.swing.JFrame;
import javax.swing.JOptionPane;
import javax.swing.JButton;
import javax.swing.JTextField;
import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.WebTarget;
import javax.ws.rs.core.MediaType;
import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;
import javax.xml.parsers.ParserConfigurationException;

import org.w3c.dom.Document;
import org.xml.sax.InputSource;
import org.xml.sax.SAXException;

import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
import java.io.IOException;
import java.io.StringReader;
import java.util.ArrayList;
import java.util.List;
import java.awt.Window.Type;

import org.json.simple.JSONArray;
import org.json.simple.JSONObject;
import org.json.simple.parser.JSONParser;
import org.json.simple.parser.ParseException;



public class GetData {
	
	
	// i use jersey libery to call webapi and json-simple-1.1 jar 
	//that include in lib folder
	
	
   private JFrame frame;
   public String finalMessage = "";
   public List<Source> slist;
   public List<Articles> alist;
   public List<ResponseData> rlist;
	
   public List<Articles> showlist;
   
   public String getFinalMessage()
   {
   
      return this.finalMessage;
   
   }
   
   public void setFinalMessage(String finalMessage)
   {
   
      this.finalMessage = finalMessage;
   
   }

	/**
	 * Launch the application.
	 */
   public static void main(String[] args) {
      EventQueue.invokeLater(
         new Runnable() {
            public void run() {
               try {
               
               // there is the entry point of exection
                  GetData window = new GetData(false,"fox-sports","Guentzel",1,"583d233722744e44954d03a1f4653c88");
                  //window.frame.setVisible(true);
               } catch (Exception e) {
                  e.printStackTrace();
               }
            }
         });
   }

	/**
	 * Create the application.
	 */
   public GetData(boolean topHeadlines, String newsSource, String desiredContent, int pageNumber, String apiKey) {
   	
   	// then system call this 
      //initialize();
      setUp(topHeadlines, newsSource, desiredContent, pageNumber, apiKey);
   }

   public void setUp(boolean topHeadlines, String newsSource, String desiredContent, int pageNumber, String apiKey)
   {
   
      setFinalMessage(buildNewsCall(topHeadlines,newsSource,desiredContent,pageNumber,apiKey));
            
   
   }

	/**
	 * Initialize the contents of the frame.
	 */
   /*private void initialize() {
      frame = new JFrame();
      frame.setBounds(100, 100, 450, 300);
      frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
   	
      frame.getContentPane().setLayout(null);
   	
      JButton Requestid = new JButton("Request");
      Requestid.addActionListener(
         new ActionListener() {
            public void actionPerformed(ActionEvent arg0) {
            
            // on Button click event  i can user define function 
            // you can change value are link source , Desire content, api ket etc
            
               System.out.println(buildNewsCall(false,"fox-sports","Yankees",1,"583d233722744e44954d03a1f4653c88"));
            
            }
         });
      Requestid.setBounds(25, 11, 89, 23);
      frame.getContentPane().add(Requestid);
   }
   */
   public String buildNewsCall(boolean topHeadlines, String newsSource, String desiredContent, int pageNumber, String apiKey)
   {
      String jsonData,excerpt = "";
      String headlines = "";
      if(topHeadlines == false)
      {headlines = "everything";}
         
      else
      {
         headlines = "top-headlines";
      }
      String url = "https://newsapi.org/v2/"+headlines+"?sources="+newsSource+"&q="+desiredContent+"&page="+pageNumber+"&sortBy=relevancy&apiKey=" + apiKey+"";
      Client client = ClientBuilder.newClient();
   	
      WebTarget target = client.target(url);
   	
      jsonData  = target.request(MediaType.APPLICATION_JSON).get(String.class).toString();
   	
      String finalUrl = "";
      
      try {
      
         slist = new ArrayList<>();
         alist = new ArrayList<>();
         rlist = new ArrayList<>();
      
         ResponseData Resp = new ResponseData();
         rlist.clear();
         alist.clear();
         if(jsonData != null){
            JSONObject rootJSON = (JSONObject) new JSONParser().parse(jsonData);
           //String Status = rootJSON.get("status").toString();
            Resp.Status = rootJSON.get("status").toString();
            Resp.TotalRecords = rootJSON.get("totalResults").toString();
           //Long TotalRecord = rootJSON.ge("status");
            JSONArray dataList = (JSONArray) rootJSON.get("articles");
           
           
           // get arry oject one by one and add in artical list
            for(Object projectObj: dataList.toArray()){
               JSONObject project = (JSONObject)projectObj;
              // String title = project.get("title").toString();
               Articles art = new Articles();
               Source src = new Source();
               JSONObject getSth = (JSONObject) project.get("source");
               //Object name = getSth.get("name");
               //Object id = getSth.get("id");
               slist.clear();
               src.name = getSth.get("name").toString();
               src.Id = getSth.get("id").toString();
               slist.add(src);
               //art.Author = project.get("author").toString();
               art.Title = project.get("title").toString();
               art.Description = project.get("description").toString();
               art.Url = project.get("url").toString();
               art.urltoimage = project.get("urlToImage").toString();
               art.publishedAt = project.get("publishedAt").toString();
               art.source = slist; 
               alist.add(art);
               finalUrl = art.Url;
            
            }
            Resp.Artical = alist;
           
           // this is you list that contain all data 
            rlist.add(Resp);
         }
      }catch (ParseException e) {
           //do smth
         e.printStackTrace();
      }
   	
   
      showlist = new ArrayList<>();
      showlist.clear();
        //here you can get data from list throug you choice like loop etc for now i get throug hard coded index
        //i assign Main Response list to new list from display 
      showlist.addAll(rlist.get(0).getArtical());
      //here you can show each item from list
      String finalMessage = // showlist.get(0).getAuthor().toString() + "  " + 
         showlist.get(0).getTitle().toString();
      //JOptionPane.showMessageDialog(null, finalMessage);
   	
      finalMessage = buildTweet(url, finalMessage);
      return finalMessage;
      // return finalMessage + " " + finalUrl;
   }
   
   public String buildTweet(String url, String excerpt){ //builds tweet that David's code will be sending out
      String tweet = excerpt.substring(0,150); //cuts off past 150 characters
      tweet.concat("~~~");
      tweet.concat(url);
   	
   	
      
      return tweet;
   }
   
/*
	
   public String buildNewsCall(boolean topHeadlines, String newsSource, String desiredContent, int pageNumber, String apiKey)
   {
      String jsonData,excerpt = "";
      String headlines = "";
      if(topHeadlines == false)
      {headlines = "everything";}
         
      else
      {
         headlines = "top-headlines";
      }
      String url = "https://newsapi.org/v2/"+headlines+"?sources="+newsSource+"&q="+desiredContent+"&page="+pageNumber+"&apiKey="+apiKey+"";
      Client client = ClientBuilder.newClient();
   	
      WebTarget target = client.target(url);
   	
      jsonData  = target.request(MediaType.APPLICATION_JSON).get(String.class).toString();
   	
      try {
      
      
      
         slist = new ArrayList<>();
         alist = new ArrayList<>();
         rlist = new ArrayList<>();
      
         ResponseData Resp = new ResponseData();
         rlist.clear();
         alist.clear();
         if(jsonData != null){
            JSONObject rootJSON = (JSONObject) new JSONParser().parse(jsonData);
           //String Status = rootJSON.get("status").toString();
            Resp.Status = rootJSON.get("status").toString();
            Resp.TotalRecords = rootJSON.get("totalResults").toString();
           //Long TotalRecord = rootJSON.ge("status");
            JSONArray dataList = (JSONArray) rootJSON.get("articles");
           
           
           // get arry oject one by one and add in artical list
            for(Object projectObj: dataList.toArray()){
               JSONObject project = (JSONObject)projectObj;
              // String title = project.get("title").toString();
               Articles art = new Articles();
               Source src = new Source();
               JSONObject getSth = (JSONObject) project.get("source");
               //Object name = getSth.get("name");
               //Object id = getSth.get("id");
               slist.clear();
               src.name = getSth.get("name").toString();
               src.Id = getSth.get("id").toString();
               slist.add(src);
               art.Author = project.get("author").toString();
               art.Title = project.get("title").toString();
               art.Description = project.get("description").toString();
               art.Url = project.get("url").toString();
               art.urltoimage = project.get("urlToImage").toString();
               art.publishedAt = project.get("publishedAt").toString();
               art.source = slist; 
               alist.add(art);
            
            }
            Resp.Artical = alist;
           
           // this is you list that contain all data 
            rlist.add(Resp);
         }
      }catch (ParseException e) {
           //do smth
         e.printStackTrace();
      }
   	
   
      showlist = new ArrayList<>();
      showlist.clear();
        //here you can get data from list throug you choice like loop etc for now i get throug hard coded index
        //i assign Main Response list to new list from display 
      showlist.addAll(rlist.get(0).getArtical());
      //here you can show each item from list
      String finalMessage = showlist.get(0).getAuthor().toString() + "  " + showlist.get(0).getTitle().toString();
      JOptionPane.showMessageDialog(null, finalMessage);
   	
      finalMessage = buildTweet(url, finalMessage);
      
      return finalMessage;
   }
*/

}
