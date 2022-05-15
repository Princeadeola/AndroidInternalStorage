# AndroidInternalStorage
This is an example to explain internal storage on java android studio application

It covers the basic understanding of internal storage in Android development using java


Internal storage is the storage of the private data on the device memory.

By default these files are private and are accessed by only your application and get deleted , when user delete your application.


<h1>Following FreeCodeCamp Blog</h1>

Internal Storage
When each application is run on the operating system, it has its own internal storage. This storage is private and only for the use of the application. Meaning, other applications cannot access it, nor can the user. Another thing to keep in mind when using internal storage is the availability of it. Unlike external storage, internal storage is always available for your application.

Using this storage has its drawbacks, though. If the user removes the application, all the data stored in your app's internal storage is removed as well. Imagine what would happen if you installed a game on your phone and somewhere down the road decided to remove it. You would like to have your game progress saved, if by any chance you would install the game again.

So, how do we save a file to internal storage?

public void saveFileInternalStorage() {
   
        String FILENAME = "hello_world_file";
        String inputToFile = "Hello From Internal Storage!";
   
        try {
            FileOutputStream fileOutputStream = openFileOutput(FILENAME, Context.MODE_PRIVATE);
            fileOutputStream.write(inputToFile.getBytes());
            fileOutputStream.close();
            Toast.makeText(getApplicationContext(),
                    "File " + FILENAME + " has been saved successfully",
                    Toast.LENGTH_SHORT).show();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
            Toast.makeText(getApplicationContext(),
                    "File " + FILENAME + " has not been saved successfully due to an exception " + e.getLocalizedMessage(),
                    Toast.LENGTH_SHORT).show();
        } catch (IOException e) {
            e.printStackTrace();
            Toast.makeText(getApplicationContext(),
                    "File " + FILENAME + " has not been saved successfully due to an exception " + e.getLocalizedMessage(),
                    Toast.LENGTH_SHORT).show();
        }
 }
Saving a file called hello_world_file
As you can see in the code example, we are saving a file called hello_world_file that contains the text, “Hello From Internal Storage!”. I have created two catch clauses just to demonstrate the exceptions that may occur when trying to do this, but you can minimize them to one catch clause with the general Exception object.

Pay attention that the method openFileOutput will open the file if it already exists, but if not, will create it. The second parameter to this method is the file mode. This parameter designates the scope of the file and access to it. The default value is MODE_PRIVATE, which makes the file accessible to your application only.

The other two values for this parameter are MODE_WORLD_READABLE and MODE_WORLD_WRITEABLE, but they have been deprecated since API 17. Sharing private files with other applications uses a different set of logic that you can read more about here. Finally, when writing to the file, we convert our string to bytes and we make sure to close the file at the end.
