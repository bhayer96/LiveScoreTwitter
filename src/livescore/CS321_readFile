import java.util.Scanner;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

public class CS321_readFile
{
     /** Holds the Lines that will be moved/copied/cut/etc. */
   private static String[] lineBuffer;

     /** Holds the total number of lines in the Document */
   public static int totalNumOfLines = 0;

   private static void countLines(File file)
   {
                         
      Scanner showAllReader = setUpReader(file);
      
      if(showAllReader != null)
      {
            
         totalNumOfLines = 0;
            
         while(showAllReader.hasNextLine())
         {
         
            totalNumOfLines++;
            showAllReader.nextLine();
                        
         }
      
      }
      
      else
      {
      
         //do nothing
      
      }
                     
   }

   /** 
    *  Takes a file and attempts to assign it a Scanner
    *  
    *  @param  file           the name of the file
    *  @return                a fully set up Scanner
    */
   public static Scanner setUpReader(File file)
   {
   
      //the reader
      Scanner showAllReader;
      
      try
      {
         
         showAllReader = new Scanner(file);
         
      }
         
      catch(FileNotFoundException fnfe)
      {
         
         showAllReader = null;
         
      }
      
      catch(NullPointerException npe)
      {
      
         showAllReader = null;
      
      }
   
      return showAllReader;
   
   }
    
   /**
    *  Loads the file
    *  
    *  @param  fileName       the name of the file
    *  @return                a File Object specified by the
    *                         username
    */
   public static String loadFile(String fileName)
   {
   
      boolean success = true;
      String temp = null;
      File file = null;
      FileReader fileR = null;
      BufferedReader reader = null;
                                 
      if(fileName != null && !(fileName.isEmpty()))
      {
      
         file = new File(fileName);
                           
         if(file.exists() == true)
         {
            
            countLines(file);
            lineBuffer = new String[totalNumOfLines + 1];
         
            try
            {
            
               fileR = new FileReader(file);
               // System.out.println(totalNumOfLines);
               reader = new BufferedReader(fileR);
                          
               for(int i = 1; i <= totalNumOfLines; i++)
               {
               
                  try
                  {
                  
                     temp = reader.readLine();
                     
                  
                  }
                  catch(IOException ioe)
                  {
                  
                     temp = " ";
                     success = false;
                     
                  }
                  
                  if(temp != null)
                  {
                  
                  
                  
                  }
               
               }
            
            }
            catch(FileNotFoundException fnfe)
            {
            
            //nothing necessary
               success = false;
            
            }
         
         }
         
         else
         {
         
            System.out.println("\nFile name is invalid");
            success = false;
         
         }
                    
      }
      
      else
      {
      
         System.out.println("\nNo file name was entered");
         success = false;
      
      }
      // System.out.println(success);
      // System.out.println(temp);
      
      return temp;
   
   }
      

}
