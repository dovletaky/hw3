# hw3
Complex Numbers
//============================================================================
// Name        : complex_numbers.cpp
// Author      : 
// Version     :
// Copyright   : Your copyright notice
// Description : Hello World in C++, Ansi-style
//============================================================================

#include <iostream>
#include <string>
using namespace std;

struct Complex {
    double real; // real part
    double imag; // imaginary part

    // constructor
    Complex () {
        real = 1;
        imag = 1;
    }

    // constructor
    Complex (double a, double b) {
    	real = a;
    	imag = b;
	  }

    ~Complex() {

	  }

    // overload *= operator
    void operator*=(Complex& c) {
      double temp = real;
      real = real*c.real - imag*c.imag;
      imag = temp*c.imag + imag*c.real;
	  }

    // overload += operator
	  void operator+=(Complex& c) {
		  real += c.real;
		  imag += c.imag;
	  }

	  // overload -= operator
	  void operator-=(Complex& c) {
		  real -= c.real;
		  imag -= c.imag;
	  }
};


// overload operator left shift '<<'
ostream& operator << (ostream& out, Complex& c) {
	out << c.real << " + " << c.imag << 'i';
	return out;
}

// overload operator right shift '>>'
istream& operator >> (istream& in, Complex& c) {
	in >> c.real >> c.imag;
	return in;
}

 // main starts execution
int main()
{
	// Initialize the complex numbers
	Complex X(3,5);
	Complex Y(4,8);

	// complex to have input from user
	Complex Z;

	// output complex numbers before alteration
	cout << X << endl;
	cout << Y << endl;

	// perform *= operation
	cout << "\nAfter multiplying two complex numbers " << X << " and " << Y <<
				" , the result is " << endl;
	X*=Y;
	cout << X << endl;

	// perform += operation
	cout << "\nAfter adding two complex numbers " << X << " and " << Y <<
			" , the result is " << endl;
	X+=Y;
	cout << X << endl;

	// perform -= operation
	cout << "\nAfter subtracting " << Y << " from " << X <<
			" , the result is " << endl;
	X-=Y;
	cout << X << endl;

	// input the real and imaginary parts of the Z
	cout << "\nInput the real and imaginary parts of complex number: " << endl;
	cin >> Z;
	cout << Z << endl;
}
