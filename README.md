# IO Java

<<<<<<< HEAD
public class Main {
    public static void main(String[] args) throws IOException {
        createFiles("myDir");
        getFiles("myDir");
        contentAdder("abc.txt");
        getReadFile("abc.txt");
        readFileAsChar("abc.txt");
        twoFilesMerge("myDir/mn0.txt", "myDir/mn1.txt");
        twoFilesMergeOneAfterTheOther("myDir/mn0.txt", "myDir/mn1.txt");
        mergeAllContentsOfAllFilesIntoOneFile();
        writeContentsFoundInOneFileButNotInOtherFile();
        removeDuplicateNumbers();
    }

//1. Creating multiple files: Passing name of a folder, many files are created
    public static void createFiles(String myDir) throws IOException {
        List<String> myListOfFiles = new ArrayList<>();
        for(int i = 0; i < 9; i++) {
            File f = new File("myDir", "mn" + i + ".txt");
            f.createNewFile();
        }
    }
//................................................................................................
//2. Getting names of files:
    public static void getFiles(String myDir){
        myDir = "myDir";
        File myFiles = new File(myDir);
        String[] list = myFiles.list();
        int count = 0;
        for(String s: list){
            File f = new File(myDir, s);
            if(f.isFile()){
                count++;
                System.out.println(f);
            }
        }
        System.out.println(count);
    }

//................................................................................................
//3. Creating a file using FileWriter and adding contents to it.
    public static  void contentAdder(String fileName) throws IOException {

        FileWriter myFile = new FileWriter("abc.txt", true);
        myFile.write(100);
        myFile.write("\n");
        myFile.write("...............");
        char[] ch = {'a', 'b', 'c'};
        myFile.write(ch);
        myFile.write("\n");
        myFile.write("...............");
        myFile.flush();
        myFile.close();
    }

//................................................................................................
//4. Read contents of a file using FileReader. INTEGER
    public static void getReadFile(String fileName) throws IOException {
        FileReader fr = new FileReader("abc.txt");
        int i = fr.read();
        while (i != -1){
            System.out.print((char)i);//type casting is must here
            i = fr.read();
        }
        fr.close();
    }

//................................................................................................
//5. Read contents of a file using FileReader. CHAR ARRAY
    public static void readFileAsChar(String fileName) throws IOException {
        File file = new File("abc.txt");
        char[] myCharacters = new char[(int)file.length()];
        FileReader fileReader = new FileReader(file);
        fileReader.read(myCharacters);
        for (char ch : myCharacters){
            System.out.print(ch);
        }
    }

// ................................................................................................
 //6. merging contents of two files line by line alternatively

    public static void twoFilesMerge(String a, String b) throws IOException {
        PrintWriter pw = new PrintWriter("myDir/abc.txt");
        BufferedReader br1 = new BufferedReader(new FileReader("myDir/mn0.txt"));
        BufferedReader br2 = new BufferedReader(new FileReader("myDir/mn1.txt"));
        String line1 = br1.readLine();
        String line2 = br2.readLine();
        while((line1 != null)||(line2 != null)){
            if(line1 != null){
                pw.println(line1);
                line1 = br1.readLine();
            }
            if(line2 != null){
                pw.println(line2);
                line2 = br2.readLine();
            }
        }
        pw.flush();
        br1.close();
        br2.close();
    }

//................................................................................................
 //7. merging contents of two files line by line contents of one file after the other
    public static void twoFilesMergeOneAfterTheOther(String a, String b) throws IOException {
        File f = new File("myDir/abc2.txt");
        PrintWriter pw = new PrintWriter(f);
        BufferedReader br1 = new BufferedReader(new FileReader("myDir/mn0.txt"));
        String line1 = br1.readLine();
        while((line1 != null)){
            if(line1 != null){
                pw.println(line1);
                line1 = br1.readLine();
            }

        }
        BufferedReader br2 = new BufferedReader(new FileReader("myDir/mn1.txt"));
        line1 = br2.readLine();
        while((line1 != null)){
            if(line1 != null){
                pw.println(line1);
                line1 = br2.readLine();
            }
        }
        pw.flush();
        br1.close();
        br2.close();
    }
//................................................................................................
//8. create a file and write the contents of all other files under a single directory
    public static  void mergeAllContentsOfAllFilesIntoOneFile() throws IOException {
        File f = new File("myDir/output.txt");
        PrintWriter pw = new PrintWriter(f);
        File fd = new File ("myDir");
        String[] files = fd.list();
        for(String file : files){
            File f1 = new File(fd, file);
            BufferedReader br = new BufferedReader(new FileReader(f1));
            String line = br.readLine();
            while(line != null){
                pw.println(line);
                line = br.readLine();
            }
        }
        pw.flush();
    }

//................................................................................................
//9. Out of two files, extract all the items in one file that are not in the second file, and write them in a third file
    public static void writeContentsFoundInOneFileButNotInOtherFile() throws IOException {
        PrintWriter pw = new PrintWriter("myDir/mn4.txt");
        BufferedReader br1 = new BufferedReader((new FileReader("myDir/mn5.txt")));
        String item1 = br1.readLine();
        while(item1 != null){
            boolean available = false;
            BufferedReader br2 = new BufferedReader(new FileReader("myDir/mn6.txt"));
            String item2 = br2.readLine();
            while(item2 != null){
                if(item1.equals(item2)){
                    available = true;
                    break;
                }
                item2 = br2.readLine();
            }
            if(available == false){
                pw.println(item1);
            }
            item1 = br1.readLine();
        }
        pw.flush();
    }

//................................................................................................
//10. write a program to remove duplicate numbers
    public static  void removeDuplicateNumbers() throws IOException {
        PrintWriter pw = new PrintWriter("myDir/mn8.txt");
        BufferedReader br1 = new BufferedReader(new FileReader("myDir/mn7.txt"));
        String item1 = br1.readLine();
        while(item1 != null){
            boolean available = false;
            BufferedReader br2 = new BufferedReader(new FileReader("myDir/mn8.txt"));
            String item2 = br2.readLine();
            while(item2 != null){
                if(item1.equals(item2)){
                    available = true;
                    break;
                }
                item2 = br2.readLine();
            }
            if(available == false){
                pw.println(item1);
                pw.flush();
            }
            item1 = br1.readLine();
        }
    }
}
=======
 
>>>>>>> 3ad6a72834c642eca6328f831094afc8ce671122
