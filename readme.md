## Architecture diagram

![image](https://github.com/user-attachments/assets/474d4b43-f850-44ef-9bdb-24ae88b22244)


## Explanation

1. User Interface Creation (JFrame and Swing Components):
    - The code creates a JFrame named "Image Inference" with a set size and default close operation.
    - It defines a JButton named "Select Image" for user interaction.
    - A JTextArea named resultTextArea is created to display the inference results. This area is non-editable and has a set font style and size.
    - A JScrollPane is used to provide scrollable functionality for the results text area within the limited window space.
    - A JPanel is created with a BorderLayout layout manager.
    - The button and scroll pane are added to the panel at specific locations (North and Center) using the layout manager.
    - Finally, the panel is added to the main JFrame window.
2. User Interaction and Image Selection:
    - An ActionListener is attached to the "Select Image" button.
    - When the button is clicked, a JFileChooser dialog appears, allowing the user to select an image file.
    - If the user clicks "Open" (JFileChooser.APPROVE_OPTION), the selected file's path is retrieved.
    - The processImage method is called to handle the selected image.
3. Image Processing and API Interaction:
    - The processImage method takes the selected image path as input.
    - It reads the entire image file into a byte array using Files.readAllBytes.
    - The byte array is then encoded into a Base64 string using Base64.getEncoder().encodeToString.
    - The code defines an API key and model endpoint (likely specific to Roboflow).
    - It constructs a URL for the inference API call, including the API key, model endpoint, and a filename for the image data.
    - An HttpURLConnection object is created to connect to the API URL.
    - The request method is set to "POST" as the application is sending data to the API.
    - Necessary headers are set, including "Content-Type" and "Content-Length" for the encoded image data.
    - Output is enabled using connection.setDoOutput(true).
    - The encoded image data (byte array) is written to the connection's output stream using an OutputStream.
    - The response from the API is then retrieved using a BufferedReader and stored in a StringBuilder object.
    - Optionally, the formatJson method might be called to format the JSON response from the API for better readability.
    - Finally, the formatted (or raw) response is displayed in the resultTextArea.
4. Main Method and Execution:
    - The main method is the program's entry point.
    - It uses SwingUtilities.invokeLater to ensure proper threading for the Swing UI components.
    - Within the run method of the anonymous Runnable, a new instance of InferenceLocal is created and set to be visible, launching the application with the user interface.

## Output

![image](https://github.com/user-attachments/assets/0e4a57e9-a65b-46f1-a552-1c8a79a0f0a6)


![image](https://github.com/user-attachments/assets/da7a771a-507e-4f4c-ac63-b7b10efc70dd)
