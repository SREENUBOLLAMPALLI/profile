# profile
i made a simple application about my information using JAVA SWING



-->>here is the code -->>
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.awt.geom.Ellipse2D;
import java.awt.image.BufferedImage;
import java.io.File;
import java.net.URI;
import javax.imageio.ImageIO;

public class info {
    public static void main(String[] args) {
        JFrame frame = new JFrame("MY INFO");
        frame.setSize(900, 600);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(null);

        Container c = frame.getContentPane();
        c.setBackground(new Color(10, 25, 49)); // Premium Navy Blue

        // ===== Menu Bar =====
        JMenuBar menuBar = new JMenuBar();
        JMenu fileMenu = new JMenu("File");
        JMenuItem exitItem = new JMenuItem("Exit");
        exitItem.addActionListener(e -> System.exit(0));
        fileMenu.add(exitItem);

        JMenu profileMenu = new JMenu("Profile");
        JMenuItem eduItem = new JMenuItem("Education");
        JMenuItem skillsItem = new JMenuItem("Skills");
        JMenuItem hobbyItem = new JMenuItem("Hobbies");
        JMenuItem personalItem = new JMenuItem("Personal");

        JMenu helpMenu = new JMenu("Help");
        JMenuItem aboutItem = new JMenuItem("About");
        aboutItem.addActionListener(e -> JOptionPane.showMessageDialog(frame,
                "This is a personal profile GUI created by Sreenu Bollampalli.",
                "About", JOptionPane.INFORMATION_MESSAGE));
        helpMenu.add(aboutItem);

        menuBar.add(fileMenu);
        menuBar.add(profileMenu);
        menuBar.add(helpMenu);
        frame.setJMenuBar(menuBar);

        // ===== Main Label =====
        JLabel nameLabel = new JLabel("SREENU BOLLAMPALLI");
        nameLabel.setBounds(50, 50, 400, 30);
        nameLabel.setForeground(new Color(255, 87, 34)); // Orange Red
        nameLabel.setFont(new Font("SansSerif", Font.BOLD, 20));
        c.add(nameLabel);

        // ===== Circular Profile Image =====
        try {
            BufferedImage original = ImageIO.read(new File("/home/user/Pictures/Wallpapers/srinu.jpg")); // <-- Change path
            int size = 100;
            BufferedImage circleImage = new BufferedImage(size, size, BufferedImage.TYPE_INT_ARGB);
            Graphics2D g2 = circleImage.createGraphics();

            g2.setClip(new Ellipse2D.Float(0, 0, size, size));
            g2.drawImage(original, 0, 0, size, size, null);
            g2.dispose();

            JLabel profilePic = new JLabel(new ImageIcon(circleImage));
            profilePic.setBounds(770, 10, size, size);
            c.add(profilePic);
        } catch (Exception ex) {
            System.out.println("Profile image not found!");
        }

        // ===== Education Section =====
        JButton eduButton = new JButton("More Info");
        eduButton.setBounds(50, 150, 150, 40);
        c.add(eduButton);

        JLabel eduLabel = new JLabel("Education Background");
        eduLabel.setBounds(50, 200, 250, 30);
        eduLabel.setForeground(Color.GREEN);
        eduLabel.setVisible(false);
        c.add(eduLabel);

        JTextArea eduText = new JTextArea(
                "• I completed my schooling in AP RESIDENTIAL SCHOOL with 9.6 CGPA\n" +
                        "• Currently studying at IIIT IDUPULAPAYA\n" +
                        "• Department: Computer Science and Engineering"
        );
        eduText.setBounds(50, 230, 700, 60);
        eduText.setEditable(false);
        eduText.setVisible(false);
        c.add(eduText);

        eduButton.addActionListener(e -> {
            boolean isVisible = eduText.isVisible();
            eduLabel.setVisible(!isVisible);
            eduText.setVisible(!isVisible);
            c.revalidate();
            c.repaint();
        });

        // ===== Skills Section =====
        JButton skillsButton = new JButton("Skills");
        skillsButton.setBounds(220, 150, 150, 40);
        c.add(skillsButton);

        JLabel skillsLabel = new JLabel("Technical Skills");
        skillsLabel.setBounds(50, 300, 200, 30);
        skillsLabel.setForeground(Color.YELLOW);
        skillsLabel.setVisible(false);
        c.add(skillsLabel);

        JTextArea skillsText = new JTextArea(
                "• Programming: Java, Python, C++\n" +
                        "• Web: HTML, CSS, JavaScript\n" +
                        "• Frameworks: React.js, Node.js"
        );
        skillsText.setBounds(50, 330, 700, 60);
        skillsText.setEditable(false);
        skillsText.setVisible(false);
        c.add(skillsText);

        skillsButton.addActionListener(e -> {
            boolean isVisible = skillsText.isVisible();
            skillsLabel.setVisible(!isVisible);
            skillsText.setVisible(!isVisible);
            c.revalidate();
            c.repaint();
        });

        // ===== Hobbies Section =====
        JButton hobbyButton = new JButton("HOBBIES");
        hobbyButton.setBounds(390, 150, 150, 40);
        c.add(hobbyButton);

        JTextArea hobbyText = new JTextArea(
                "* Solving problems on LeetCode\n" +
                        "* Watching movies and web series\n" +
                        "* Learning new technologies"
        );
        hobbyText.setBounds(50, 400, 750, 60);
        hobbyText.setVisible(false);
        hobbyText.setEditable(false);
        c.add(hobbyText);

        hobbyButton.addActionListener(e -> {
            boolean isVisible = hobbyText.isVisible();
            hobbyText.setVisible(!isVisible);
            c.revalidate();
            c.repaint();
        });

        // ===== Personal Info =====
        JButton personalButton = new JButton("PERSONAL");
        personalButton.setBounds(560, 150, 150, 40);
        c.add(personalButton);

        personalButton.addActionListener(e -> {
            JOptionPane.showMessageDialog(frame,
                    "Name: Sreenu Bollampalli\n" +
                            "DOB: 01-Jan-2003\n" +
                            "Nationality: Indian",
                    "Personal Info", JOptionPane.INFORMATION_MESSAGE);
        });

        // ==== Hooking Menu Items ====
        eduItem.addActionListener(e -> eduButton.doClick());
        skillsItem.addActionListener(e -> skillsButton.doClick());
        hobbyItem.addActionListener(e -> hobbyButton.doClick());
        personalItem.addActionListener(e -> personalButton.doClick());

        profileMenu.add(eduItem);
        profileMenu.add(skillsItem);
        profileMenu.add(hobbyItem);
        profileMenu.add(personalItem);

        // ===== Approach Link =====
        JLabel approachLabel = new JLabel("Approach:");
        approachLabel.setBounds(50, 500, 80, 30);
        approachLabel.setForeground(Color.WHITE);
        c.add(approachLabel);

        JLabel linkedInLabel = new JLabel("<html><a href=''>Approach me on LinkedIn</a></html>");
        linkedInLabel.setBounds(140, 500, 250, 30);
        linkedInLabel.setForeground(Color.CYAN);
        linkedInLabel.setCursor(Cursor.getPredefinedCursor(Cursor.HAND_CURSOR));
        linkedInLabel.addMouseListener(new java.awt.event.MouseAdapter() {
            public void mouseClicked(java.awt.event.MouseEvent evt) {
                try {
                    Desktop.getDesktop().browse(new URI("https://www.linkedin.com/in/sreenu-bollampalli-a62a12344/"));
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }
        });
        c.add(linkedInLabel);

        frame.setVisible(true);
    }
}
