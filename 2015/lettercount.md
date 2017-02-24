---
layout: default
---

# 英文字母频率统计
2015.03.06

读取文件，统计各个字母出现的频率。

源程序：
```Java
/**
 * Count the frequence of each character by reading a file.
 * 
 * @author LuoPeng
 * @time 2015.3.5
 *
 */
public class CharacterFrequence {

    /**
     * Count the frequence of each character
     * @param filePath the path of the file to be read
     * @return the frequence of each character
     */
    public double[] countFrequence ( String filePath ) {
        
        double [] frequence = null;
        int [] counts = null;
        long totalCharacter = 0L;
        BufferedReader br = null;
        
        try {
            // Get the reader
            br = new BufferedReader(new InputStreamReader(new FileInputStream(filePath)));
            // Read message from the file if the reader is not null
            if ( br != null ) {
                // Make and initialize the array
                frequence = new double[26];
                counts = new int[26];
                
                // Store the message of each line
                String line = br.readLine();
                // Store the length of line
                int tempCount = 0;
                // The loop variable
                int i = 0;
                while ( line != null ) {
                    line = line.trim().toLowerCase();
                    tempCount = line.length();
                    for ( i = 0; i < tempCount; i++ ) {
                        switch (line.charAt(i)) {
                        case 'a':
                            counts[0]++;
                            break;
                        case 'b':
                            counts[1]++;
                            break;
                        case 'c':
                            counts[2]++;
                            break;
                        case 'd':
                            counts[3]++;
                            break;
                        case 'e':
                            counts[4]++;
                            break;
                        case 'f':
                            counts[5]++;
                            break;
                        case 'g':
                            counts[6]++;
                            break;
                        case 'h':
                            counts[7]++;
                            break;
                        case 'i':
                            counts[8]++;
                            break;
                        case 'j':
                            counts[9]++;
                            break;
                        case 'k':
                            counts[10]++;
                            break;
                        case 'l':
                            counts[11]++;
                            break;
                        case 'm':
                            counts[12]++;
                            break;
                        case 'n':
                            counts[13]++;
                            break;
                        case 'o':
                            counts[14]++;
                            break;
                        case 'p':
                            counts[15]++;
                            break;
                        case 'q':
                            counts[16]++;
                            break;
                        case 'r':
                            counts[17]++;
                            break;
                        case 's':
                            counts[18]++;
                            break;
                        case 't':
                            counts[19]++;
                            break;
                        case 'u':
                            counts[20]++;
                            break;
                        case 'v':
                            counts[21]++;
                            break;
                        case 'w':
                            counts[22]++;
                            break;
                        case 'x':
                            counts[23]++;
                            break;
                        case 'y':
                            counts[24]++;
                            break;
                        case 'z':
                            counts[25]++;
                            break;
                            default:
                                ;
                        }
                    }
                    line = br.readLine();
                }
                
                // calculate the number of characters
                for ( i = 0; i < counts.length; i++ ) {
                    totalCharacter += counts[i];
                }
                // calculate the frequence
                for ( i = 0; i < frequence.length; i++ ) {
                    frequence[i] = 1.0*counts[i]/totalCharacter;
                }
            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
            System.out.println("Could not find the file...");
        } catch (IOException e) {
            e.printStackTrace();
            System.out.println("Read message error...");
        } finally {
            // Close the IO
            try {
                br.close();
            } catch (IOException e) {
                e.printStackTrace();
                System.out.println("Close IO exception...");
            }
        }
        
        return frequence;
        
    }
}
```
![letter-count-1](./../images/letter-count-1.png?raw=true)

![letter-count-2](./../images/letter-count-2.png?raw=true)