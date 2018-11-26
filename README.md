# Java_Parser
The system is checked with respect to several aspects and the screenshots with respect to test results are attached below:

The above screenshot shows the GUI of the program.
This is the main page of the application.It consists of Input text field named as “Code Input” and output text area named as “Output”.
Input content can be given directly in the input text field.
It has the icons namely “New code” and “Compile”. They are generated using the following codes:


//New code:
private void refresh_lblMouseClicked(java.awt.event.MouseEvent evt) {
this.code_input_area.setText("");
this.output_area.setText("");
}


//Compile:
private void compile_lblMouseClicked(java.awt.event.MouseEvent evt) {
this.output_area.setText("");
try{
File file = new File("code.txt");
if(!file.exists())
file.createNewFile();
PrintWriter p = new PrintWriter(file);
p.print(this.code_input_area.getText().trim());
p.close();
Thread.sleep(500);
}
catch (Exception e){
JOptionPane.showMessageDialog(this, e.toString());
System.out.println(e);
e.printStackTrace();
}

These are the two events that happens on clicking the two buttons(ode input and Compile).
Whenever the code input button is clicked the code in the text field will be cleared and space for the new code will be provided.
On clicking the compile button the contents in the Output area will be cleared and the code given in the input text area will be sent to a file named ”code.txt”.
The contents of the file code.txt will be “written” everytime and not “appended”.

The further processing of the input code is as shown below

try {
CompilationUnit u =  JavaParser.parse(new File("code.txt"));
List<Comment>L = u.getComments();
for( Comment c : L){
output_area.append(c.toString());
System.out.println(c);
}
}
catch (NullPointerException npe){
this.output_area.setText("No Comments found!!");
}

catch( Exception e){
JOptionPane.showMessageDialog(this, e);
System.out.println(e);
e.printStackTrace();} }

A code consisting of both “Single line” and “Java document” comme

catch (NullPointerException npe){
this.output_area.setText("No Comments found!!");
}

NullPointerException will be executed when there  are no comments found in the input code.
In such cases the block will print the message as 
“NO COMMENTS FOUND”
