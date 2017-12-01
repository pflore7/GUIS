
import java.util.Random;// --> random #s utilities 
import java.awt.*;  //--> graphic user interface older one 
import javax.swing.*; //--> get back  better versions 
import java.awt.event.*;//--> click a button and what goes next

public class KFrame extends JFrame{
	//function to launch the GUI
	public void GUIRunner(){
		JFrame f= new JFrame("Red");    //frame object
        JPanel panel = new JPanel();  	//panel object
        	panel.setBounds(40,80,200,200);    
        	panel.setBackground(Color.red);  
        JButton b1=new JButton("Change color");    //button object 
        	b1.setBounds(50,100,80,30);  //setBounds(x, y, width, height) if you set the layout to null  
        	b1.setBackground(Color.yellow);    
        
        panel.add(b1); 		//adding the button to the panel
		
        b1.addActionListener( new ActionListener()  //listener - event handling for the button
		{
			@Override //instructs the compiler that you intend to override a method in the superclass. 
			//If the compiler detects that the method does not exist in one of the superclasses, 
			//then it will generate an error.
			public void actionPerformed(ActionEvent e)
			{
				Color current_color = panel.getBackground();
				if(current_color == Color.red){
					panel.setBackground(Color.blue);
					f.setTitle("blue");
				}
				else{
					panel.setBackground(Color.red);
					f.setTitle("red");
				}
			}
		});
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		//panel.setBounds(50,90,100,200);
		//panel.add(f);//Create your panel and put it in the frame.
		f.getContentPane().add(panel, BorderLayout.CENTER);//TA 
		//f.setSize(400, 500);//Size the frame.
		f.pack();
		//Show it.
		f.setVisible(true);
	}
	public static void main(String[] args){
		KFrame k = new KFrame();
		k.GUIRunner();
		LFrame l = new LFrame();
		l.GUIRunner();
		MFrame m = new MFrame();
		m.GUIRunner();
	}
}

class LFrame extends JFrame{
	public void GUIRunner(){
		JFrame f = new JFrame();
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        JPanel panel = new JPanel();
        panel.setLayout(new GridLayout(2,2)); //panel with a grid layout 
		JPanel[][] temp_panels = new JPanel[2][2]; // creating panels for each cell in the grid
		//adding the cell panels to the grid layout panel
		for(int m = 0; m < 2; m++) {
			for(int n = 0; n < 2; n++) {
			temp_panels[m][n] = new JPanel();
			panel.add(temp_panels[m][n]);
			}
		}
		JTextField t1, t2;  
		t1=new JTextField("Enter value here");  
		t1.setBounds(50,100, 200,30);  
		t2=new JTextField("Example");  
		t2.setBounds(50,100, 200,30);
		TextArea ta1 = new TextArea();
		TextArea ta2 = new TextArea();
		TextArea ta3 = new TextArea();
		ta1.setEditable(false);
		ta2.setEditable(false);
		ta3.setEditable(false);
		//common listener object created for the text fields
		ActionListener listener = new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				int option = Integer.parseInt(t1.getText());
				switch (option){
					case 1:
						ta1.setText(t2.getText());
						break;
					case 2:
						ta2.setText(t2.getText());
						break;
					case 3:
						ta3.setText(t2.getText());
						break;
					default:
						break;
				}
		}
		};
		//adding the text fields and the text areas to the desired locations in the grid
		t1.addActionListener(listener);
		t2.addActionListener(listener);
		temp_panels[0][0].add(t1);
		temp_panels[0][0].add(t2);
		temp_panels[0][1].add(ta1);
		temp_panels[1][0].add(ta2);
		temp_panels[1][1].add(ta3);
		
		f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		//Create your panel and put it in the frame.
		f.getContentPane().add(panel, BorderLayout.CENTER);
		//Size the frame.
		f.pack();
		//Show it.
		f.setVisible(true);
	}
}

class MFrame extends JFrame{
	int value = 1;
	public void GUIRunner(){
		JFrame f = new JFrame();
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		JPanel panel = new JPanel();
		panel.setLayout(new BoxLayout(panel, BoxLayout.Y_AXIS)); //panel with a box layout split horizontally
		JPanel panel1 = new JPanel();
		JPanel panel2 = new JPanel();
		panel.add(panel1);
		panel.add(panel2);
		JButton b1 = new JButton("Increment value");     
        b1.setBounds(50,100,80,30);    
        b1.setBackground(Color.yellow);    
        panel1.add(b1);  
		JLabel label = new JLabel(Integer.toString(value)); //label object to display "value"
		panel2.add(label);
		ActionListener listener = new ActionListener()
		{
			@Override
			public void actionPerformed(ActionEvent e)
			{
				value += 1;
				label.setText(Integer.toString(value));
			}
		};
		b1.addActionListener(listener);
		f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		//Create your panel and put it in the frame.
		f.getContentPane().add(panel, BorderLayout.CENTER);
		//Size the frame.
		f.pack();
		//Show it.
		f.setVisible(true);
	}
}



