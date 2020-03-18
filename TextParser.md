# Java

```java

import java.io.BufferedReader;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.HashSet;
import java.util.Iterator;
import java.util.List;
import java.util.Set;

public class TextParser {
	static HashSet<String> q = new HashSet<String>();
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		try{
            //파일 객체 생성
            File file = new File("D:\\hvpn_user\\hvpn01_IN2003.log");
            //입력 스트림 생성
            FileReader filereader = new FileReader(file);
            //입력 버퍼 생성
            BufferedReader bufReader = new BufferedReader(filereader);
            String line = "";
            
            while((line = bufReader.readLine()) != null){
                String[] temp = line.split(",");
                
                if(!temp[5].isEmpty()) {
//                	System.out.println(temp[2] + " " + filter(temp[5]));    
                	q.add(filter(temp[5]));
//                	System.out.println(filter(temp[5]));
                }
            }
            
            System.out.println("size is  " + q.size());
        	String[] ss = new String[q.size()];
        	q.toArray(ss);
        	Arrays.sort(ss);
        	
        	for (int i = 0; i < q.size(); i++) {
        		if(ss[i].contains("@")) {
        			System.out.println(ss[i]);
        		}
        		
			}
        	
            bufReader.close();
            
            
        }catch (FileNotFoundException e) {
            // TODO: handle exception
        }catch(IOException e){
            System.out.println(e);
        }catch(ArrayIndexOutOfBoundsException e){
        	
        }
	}

	private static String filter(String string) {
		// TODO Auto-generated method stub
		StringBuffer s = new StringBuffer(string);
		s.deleteCharAt(string.length()-1);
		s.deleteCharAt(0);	
		
		string = s.toString();
		
		return string;
	}

}


```

HashSet<객체>를 담을땐 Overrride로 equals, hashcode 함수를 바꿔야한다.
