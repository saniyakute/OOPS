# OOPS
1.	
import java.util.*;

class Complex_Op {
    float real, imag;

    Complex_Op() // Default Constructor
    {
        real = 0;
        imag = 0;
    }

    Complex_Op(float Comp1, float Comp2) // Parameterized Constructor
    {
        real = Comp1;
        imag = Comp2;
    }

    void AddNumbers(Complex_Op C1, Complex_Op C2) {
        float real, imag;
        real = (C1.real + C2.real);
        imag = (C1.imag + C2.imag);
        System.out.println("Addition:=" + real + "+" + imag + "i");
    }

    void SubtractNumbers(Complex_Op C1, Complex_Op C2) {
        float real, imag;
        real = (C1.real - C2.real);
        imag = (C1.imag - C2.imag);
        System.out.println("Subtraction:=" + real + "+" + imag + "i");
    }

    void MultiplyNumbers(Complex_Op C1, Complex_Op C2) {
        float real, imag;
        real = (C1.real * C2.real - C1.imag * C2.imag);
        imag = (C1.real * C2.imag + C2.real * C1.imag);
        System.out.println("Multiplication:=" + real + "+" + imag + "i");
    }

    void DivideNumbers(Complex_Op C1, Complex_Op C2) {
        float real, imag, deno;
        deno = (C2.real * C2.real + C2.imag * C2.imag);
        real = (C1.real * C2.real + C1.imag * C2.imag) / deno;
        imag = (C2.real * C1.imag - C1.real * C2.imag) / deno;
        System.out.println("Division:=" + real + "+" + imag + "i");
    }
}

public class Complex {
    public static void main(String args[]) {
        int num1, num2, answer;
        Complex_Op cal = new Complex_Op();
        Scanner input = new Scanner(System.in);
        System.out.println("Enter first number");
        num1 = input.nextInt(); // Real part
        num2 = input.nextInt(); // Imaginary Part
        Complex_Op Object1 = new Complex_Op(num1, num2);
        System.out.println("Enter the Second Number");
        num1 = input.nextInt(); // Real Part
        num2 = input.nextInt(); // Imaginary Part
        Complex_Op Object2 = new Complex_Op(num1, num2);
        cal.AddNumbers(Object1, Object2);
        cal.SubtractNumbers(Object1, Object2);
        cal.MultiplyNumbers(Object1, Object2);
        cal.DivideNumbers(Object1, Object2);
    }
}
Output: 
