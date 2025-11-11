import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;


class WordCounter extends JFrame implements ActionListener {
    private JTextArea textArea;
    private JButton submitButton, clearButton;
    private JLabel inputLabel, wordCountLabel, charCountWithSpacesLabel, charCountWithoutSpacesLabel;

    public WordCounter() {
        // Set up the frame
        setTitle("Word Counter");
        setSize(500, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        // Create panel for input and buttons
        JPanel inputPanel = new JPanel();
        inputPanel.setLayout(new BorderLayout());

        // Create label for user input
        inputLabel = new JLabel("Enter your String Here:");
        inputPanel.add(inputLabel, BorderLayout.NORTH);

        // Create text area for input
        textArea = new JTextArea();
        inputPanel.add(new JScrollPane(textArea), BorderLayout.CENTER);

        // Create panel for buttons
        JPanel buttonPanel = new JPanel();
        buttonPanel.setLayout(new FlowLayout());

        // Create submit button
        submitButton = new JButton("Submit");
        submitButton.addActionListener(this);
        buttonPanel.add(submitButton);

        // Create clear button
        clearButton = new JButton("Clear");
        clearButton.addActionListener(this);
        buttonPanel.add(clearButton);

        // Add button panel to input panel
        inputPanel.add(buttonPanel, BorderLayout.SOUTH);

        // Add input panel to frame
        add(inputPanel, BorderLayout.CENTER);

        // Create panel for result labels
        JPanel resultPanel = new JPanel();
        resultPanel.setLayout(new GridLayout(3, 1));

        // Create result labels
        wordCountLabel = new JLabel("Words: 0");
        charCountWithSpacesLabel = new JLabel("Characters (with spaces): 0");
        charCountWithoutSpacesLabel = new JLabel("Characters (without spaces): 0");

        // Add result labels to result panel
        resultPanel.add(wordCountLabel);
        resultPanel.add(charCountWithSpacesLabel);
        resultPanel.add(charCountWithoutSpacesLabel);

        // Add result panel to frame
        add(resultPanel, BorderLayout.SOUTH);

        // Make frame visible
        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == submitButton) {
            // Get text from text area
            String text = textArea.getText().trim();

            // Count words
            String[] words = text.split("\\s+");
            int wordCount = (text.isEmpty()) ? 0 : words.length;

            // Count characters with and without spaces
            int charCountWithSpaces = text.length();
            int charCountWithoutSpaces = text.replace(" ", "").length();

            // Update result labels
            wordCountLabel.setText("Words: " + wordCount);
            charCountWithSpacesLabel.setText("Characters (with spaces): " + charCountWithSpaces);
            charCountWithoutSpacesLabel.setText("Characters (without spaces): " + charCountWithoutSpaces);

        } else if (e.getSource() == clearButton) {
            // Clear text area and result labels
            textArea.setText("");
            wordCountLabel.setText("Words: 0");
            charCountWithSpacesLabel.setText("Characters (with spaces): 0");
            charCountWithoutSpacesLabel.setText("Characters (without spaces): 0");
        }
    }

    public static void main(String[] args) {
        new WordCounter();
    }
}
# Word-Count
It is a simple Java application using Swing that counts the number of words in a given paragraph entered by the user. The application will have a text area where users can type or paste a paragraph and a button that, when clicked, will calculate and display the total number of words in the text area.
