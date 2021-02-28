# Calculator
Crear una biblioteca dinámica que contenga las operaciones matemáticas básicas en números enteros, dicha biblioteca deberá ser referencia a una aplicación de CALCULADORA, por lo que cada una de esas operaciones que ejecute CALCULADORA deberá realizarse desde la biblioteca.

package Calculadora;

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.*;

public class Program_calcu {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		MarcoCalculadora mimarco=new MarcoCalculadora();
		mimarco.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		mimarco.setVisible(true);

		
		
	}

}

class MarcoCalculadora extends JFrame{
	public MarcoCalculadora() {
		setTitle("Calculadora");
		setBounds(500,300,450,300);
		LaminaCalculadora milamina=new LaminaCalculadora();
		
		add(milamina);
		//pack();
		
	}
	
}

class LaminaCalculadora extends JPanel{
	
	public LaminaCalculadora() {
		
		principio=true;
		
		setLayout(new BorderLayout());
		
		pantalla=new JButton("0");
		pantalla.setEnabled(false);
		add(pantalla,BorderLayout.NORTH);
		
		milamina2=new JPanel();
		milamina2.setLayout(new GridLayout(4,4));
		
		ActionListener insertar=new InsertaNumero();
		
		ActionListener  orden=new AccionOrden();
		
		ponerBoton("7",insertar);
		ponerBoton("8",insertar);
		ponerBoton("9",insertar);
		ponerBoton("/",orden);
		
		ponerBoton("4",insertar);
		ponerBoton("5",insertar);
		ponerBoton("6",insertar);
		ponerBoton("*",orden);
		
		ponerBoton("1",insertar);
		ponerBoton("2",insertar);
		ponerBoton("3",insertar);
		ponerBoton("-",orden);
		
		ponerBoton("0",insertar);
		ponerBoton(".",insertar);
		ponerBoton("=",orden);
		ponerBoton("+",orden);
		
		add(milamina2, BorderLayout.CENTER);
		
		ultimaOperacion="=";
		
	}
	private void ponerBoton(String rotulo, ActionListener oyente) {
		JButton boton=new JButton(rotulo);
		boton.addActionListener(oyente);
		
		milamina2.add(boton);
	}
	
	private class InsertaNumero implements ActionListener{

		@Override
		public void actionPerformed(ActionEvent e) {
			// TODO Auto-generated method stub
			
			String entrada=e.getActionCommand();
			
			if(principio) {
				pantalla.setText("");
				principio=false;
			}
			pantalla.setText(pantalla.getText()+entrada);
			
		}
		
	}
	private class AccionOrden implements ActionListener{

		@Override
		public void actionPerformed(ActionEvent e) {
			// TODO Auto-generated method stub
			
			String operacion=e.getActionCommand();
			calcular(Double.parseDouble(pantalla.getText()));
			ultimaOperacion=operacion;
			principio=true;
			
		}
		public void calcular(double x) {
			if(ultimaOperacion.equals("+")) {
				resultado+=x;		

			}
			else if(ultimaOperacion.equals("-")) {
				resultado-=x;		
			}
			else if(ultimaOperacion.equals("*")) {
				resultado*=x;		
			}
			else if(ultimaOperacion.equals("/")) {
				resultado/=x;		
			}
			else if(ultimaOperacion.equals("=")) {
				resultado=x;		
			}
		pantalla.setText(""+resultado);
			
		}
	}
	
	private JPanel milamina2;
	private JButton pantalla;
	private boolean principio;
	private double resultado;
	private String ultimaOperacion;
	
}

Importando biblioteca a un nuevo proyecto.

import Calculadora.Program_calcu;

public class prueba {

	public static void main(String[] args) {
		
 Program_calcu dahe = new Program_calcu();

	}

}


![hj](https://user-images.githubusercontent.com/71053185/109427153-a689f580-79b6-11eb-8e22-79fd3e6e6110.png)

Gracias por ver;
