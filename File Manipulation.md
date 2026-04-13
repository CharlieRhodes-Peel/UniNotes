In [[Java]]
# Notes:
- To Read (r) and Write (w) files in [[Java]] you have to *stream* the data
- Can use an absolute path (yucky) or a relative path to file:
- Good to use File.separator (platform independence!)
	- it's / in windows and \ in [[linux]]

Example (relative path):

	String path = "src" + File.seperator + "test2.txt"
# Main Steps:
1. Get file ready will File class
2. Set up stream
3. Start to write
4. Close stream

# Byte-Based Stream:
- Best for dealing with **values**
### File out (w):
FileOutputStream override ([[Overloading]]) true means **APPEND** to file

	File f = new File("path name");                       // 1. Get file ready
	FileOutputStream out = new FileOutputStream(f, true); //2. Set up
	String str = "Hello World";
	byte b[] = str.getBytes();
	out.write(b);                                         // 3. Start to write
	out.close();                                          // 4. Close stream
### File input (r):

	File f = new File("path name");                 // 1. Get file ready
	FileInputStream input = new FileInputStream(f); // 2. Set up
	byte b[] = new byte[(int)f.length()];
	input.read(b);                                  // 3. Read
	input.close();                                  // 4. Close

# Char-Based Stream:
- Best for dealing with **text** (not values)
### File out (w):
FileWriter override ([[Overloading]]) true means to **APPEND** to the file

	File f = new File("path name"); //1. Get file ready
	Writer out = new FileWriter(f); //2. Set up
	String str = "Hello World";  
	out.write(str);                 //3. Write
	out.close();                    //4. Close
### File input (r):

	File f = new File("path name");       //1. Get file ready
	Reader reader = new FileReader(f);    //2. Set up
	 int temp = 0;
	 while((temp = reader.read()) != -1){  //reader.read() returns -1 at end
		 System.out.println((char)temp);  //3. Read
	 }
	 reader.close();                       //4. Close