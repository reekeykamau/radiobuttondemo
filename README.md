<img width="180" height="240" alt="9" src="https://github.com/user-attachments/assets/0f9ed745-ce1b-47a3-ab38-139295234e72" />
<img width="180" height="240" alt="8" src="https://github.com/user-attachments/assets/4bfcff83-b1b9-488e-845c-73050322b4c4" />
<img width="180" height="240" alt="7" src="https://github.com/user-attachments/assets/90ffa352-bb4c-4804-ba6a-9c2fdd1a9a73" />
<img width="180" height="240" alt="6" src="https://github.com/user-attachments/assets/da89ddc1-60b5-404d-92e8-2caaf200f612" />
<img width="180" height="240" alt="5" src="https://github.com/user-attachments/assets/b76112ce-64a2-4550-b5ad-60412c0154fc" />
<img width="180" height="240" alt="4" src="https://github.com/user-attachments/assets/f8841ad8-6b73-4b3b-b5df-18a15426566c" />
<img width="180" height="240" alt="3" src="https://github.com/user-attachments/assets/dd75a57c-4344-409b-aa19-3f4ca9278ca5" />
<img width="180" height="240" alt="2" src="https://github.com/user-attachments/assets/990cf77f-311e-4aec-bb3f-6e29ba143079" />
<img width="180" height="240" alt="1" src="https://github.com/user-attachments/assets/7e7463e3-2850-40ed-b541-cac5a3ceb139" />

THE CODE

package radiobuttondemo;  // Remove this line if not using package

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.border.TitledBorder;

public class RadioButtonDemo extends JFrame {
    private JRadioButton birdRadio, catRadio, dogRadio, rabbitRadio, pigRadio;
    private ButtonGroup petGroup;
    private JButton showButton;
    
    public RadioButtonDemo() {
        setTitle("RadioButtonDemo");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout(15, 15));
        
        // Create radio buttons
        birdRadio = new JRadioButton("Bird");
        catRadio = new JRadioButton("Cat");
        dogRadio = new JRadioButton("Dog");
        rabbitRadio = new JRadioButton("Rabbit");
        pigRadio = new JRadioButton("Pig");
        
        // Group the radio buttons
        petGroup = new ButtonGroup();
        petGroup.add(birdRadio);
        petGroup.add(catRadio);
        petGroup.add(dogRadio);
        petGroup.add(rabbitRadio);
        petGroup.add(pigRadio);
        
        // Create panel for radio buttons
        JPanel radioPanel = new JPanel();
        radioPanel.setLayout(new GridLayout(5, 1, 10, 10));
        radioPanel.setBorder(BorderFactory.createTitledBorder(
            BorderFactory.createLineBorder(Color.BLUE, 2),
            "Select Pet",
            TitledBorder.CENTER,
            TitledBorder.TOP,
            new Font("Arial", Font.BOLD, 14),
            Color.BLUE
        ));
        radioPanel.add(birdRadio);
        radioPanel.add(catRadio);
        radioPanel.add(dogRadio);
        radioPanel.add(rabbitRadio);
        radioPanel.add(pigRadio);
        
        // Create Show button
        showButton = new JButton("Show Pet");
        showButton.setFont(new Font("Arial", Font.BOLD, 14));
        showButton.setBackground(new Color(70, 130, 180));
        showButton.setForeground(Color.WHITE);
        showButton.setFocusPainted(false);
        
        showButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                showSelectedPet();
            }
        });
        
        // Panel for button
        JPanel buttonPanel = new JPanel();
        buttonPanel.add(showButton);
        
        // Add components to frame
        add(radioPanel, BorderLayout.CENTER);
        add(buttonPanel, BorderLayout.SOUTH);
        
        // Frame settings
        setSize(350, 350);
        setLocationRelativeTo(null);
        setVisible(true);
    }
    
    private void showSelectedPet() {
        String selectedPet = "";
        String emoji = "";
        
        if (birdRadio.isSelected()) {
            selectedPet = "Bird";
            emoji = "🐦";
        } else if (catRadio.isSelected()) {
            selectedPet = "Cat";
            emoji = "🐱";
        } else if (dogRadio.isSelected()) {
            selectedPet = "Dog";
            emoji = "🐶";
        } else if (rabbitRadio.isSelected()) {
            selectedPet = "Rabbit";
            emoji = "🐰";
        } else if (pigRadio.isSelected()) {
            selectedPet = "Pig";
            emoji = "🐷";
        } else {
            JOptionPane.showMessageDialog(this, 
                "Please select a pet first!", 
                "No Selection", 
                JOptionPane.WARNING_MESSAGE);
            return;
        }
        
        JOptionPane.showMessageDialog(this, 
            "You selected: " + emoji + " " + selectedPet, 
            "Pet Selection", 
            JOptionPane.INFORMATION_MESSAGE);
    }
    
    public static void main(String[] args) {
        // Make sure this method exists
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new RadioButtonDemo();
            }
        });
    }
}
