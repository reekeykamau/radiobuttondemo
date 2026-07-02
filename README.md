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
