
/*************************************************************************
Compiling Options
*************************************************************************/
1.IDE: 
	1.VC2010
4.Linux:
	1.g++ -std=c++0x example.cpp -o example_program (gcc compiler)
/*************************************************************************
Reference Books
*************************************************************************/
1. C reference: “The C Programming Language” by Kernighan and Ritchie (Old Testment,1972)
2. C reference: ANSI Standardization (New Testment,1989)


/*************************************************************************
Fundamental concepts
*************************************************************************/

How many ways are there to initialize a primitive data type in C++ and what are they? 
Why should you declare a destructor as virtual? 
What does it mean that C++ supports overloading? 
What are examples of overloading in C++? 
What is name mangling in C++ and why is it used? 
What is an abstract base class? 
What is RTTI? 
How can you access a variable that is “hidden” by another variable of the same name? 
What is a namespace and how is it used. 
What are the differences between a class and a struct in C++, and how does this compare to C? 
What are templates? How are they used? 
What is a copy constructor and when is it used, especially in comparison to the equal operator. 
What is the difference between a “shallow” and a “deep” copy? 
What is the const operator and how is it used? 
What are the differences between passing by reference, passing by value, and passing by pointer in C++? 
When is it and when is it not a good idea to return a value by reference in C++? 
What is the difference between a variable created on the stack and one created on the heap? 
How do you free memory allocated dynamically for an array? What are the implications of just using delete? 
What is multiple inheritance? When should it be used? 
What is a pure virtual function? 
What does the keyword mutable do? 
What does the keyword volatile do? 
What is the STL? 
What is a Vector? 
What is contained in the <algorithms> header? 
What is the difference between #include <iostream.h> and #include <iostream>? 
What’s the difference between “++i” and “i++”? 
What is short circuit evaluation? How can it be used? Why can is be dangerous? 
What is the ‘,’ operator? 
What is the only ternary operator? How is it used? 
What is the use of a const member function and how can it be used? 
How is try/catch used in C++? 
Why should you never throw an exception in a destructor? 
What is the explicit keyword? 
What is the proper way to perform a cast in C++? 
What does inline do? 



/*************************************************************************
Parsing User Input for arithmetic (page 58)
*************************************************************************/
#include <iostream>
#include <string>
#include <sstream>
using namespace std;

int main ()
{
  string name;
  int num;
  cout << "Please, enter your full name: ";
  getline (cin,name);
  stringstream (name) >> num;

  cout << "Hello, " << num << "!\n";

  return 0;
}

/*************************************************************************
Passing by reference
*************************************************************************/
#include <iostream>
using namespace std;
void duplicate (int& a, int& b, int& c)
{
	a*=2;
	b*=2;
	c*=2;
}
int main ()
{
	int x=1, y=3, z=7;
	duplicate (x, y, z);
	cout << "x=" << x << ", y=" << y << ", z=" << z;
	return 0;
}

/*************************************************************************
Function Overloading
*************************************************************************/
#include <iostream>
using namespace std;
int operate (int a, int b)
{
	return (a*b);
}
float operate (float a, float b)
{
	return (a/b);
}
int main ()
{
	int x=5,y=2;
	float n=5.0,m=2.0;
	cout << operate (x,y);
	cout << "\n";
	cout << operate (n,m);
	cout << "\n";
	return 0;
}


/*************************************************************************
Recursion
*************************************************************************/
#include <iostream>
using namespace std;
long factorial (long a)
{
	if (a > 1)
		return (a * factorial (a-1));
	else
		return (1);
}
int main ()
{
	long number;
	cout << "Please type a number: ";
	cin >> number;
	cout << number << "! = " << factorial (number);
	return 0;
}


/*************************************************************************
Equivalency of pointer and arrays(constant pointer)
*************************************************************************/
// more pointers
#include <iostream>
using namespace std;
int main ()
{
	int numbers[5];
	int * p;
	p = numbers; *p = 10;
	p++; *p = 20;
	p = &numbers[2]; *p = 30;
	p = numbers + 3; *p = 40;
	p = numbers; *(p+4) = 50;
	for (int n=0; n<5; n++)
	cout << numbers[n] << ", ";
	return 0;
}

/*************************************************************************
Void pointer for generic data type
*************************************************************************/
// increaser
#include <iostream>
using namespace std;
void increase (void* data, int psize)
{
	if ( psize == sizeof(char) )
		{ char* pchar; pchar=(char*)data; ++(*pchar); }
	else if (psize == sizeof(int) )
		{ int* pint; pint=(int*)data; ++(*pint); }
}
int main ()
{
	char a = 'x';
	int b = 1602;
	increase (&a,sizeof(a));
	increase (&b,sizeof(b));
	cout << a << ", " << b << endl;
	return 0;
}


/*************************************************************************
Dynamic Memory Allocation
*************************************************************************/
#include <iostream>
#include <new>
using namespace std;
int main ()
{
	int i,n;
	int * p;
	cout << "How many numbers would you like to type? ";
	cin >> i;
	p= new (nothrow) int[i];
	if (p == 0)
		cout << "Error: memory could not be allocated";
	else {
		for (n=0; n<i; n++) {
			cout << "Enter number: ";
			cin >> p[n];
		}
		cout << "You have entered: ";
		for (n=0; n<i; n++)
			cout << p[n] << ", ";
		delete[] p;
	}
	return 0;
}

/*************************************************************************
Data structure 
*************************************************************************/
// array of structures
#include <iostream>
#include <string>
#include <sstream>
using namespace std;
#define N_MOVIES 3
struct movies_t {
	string title;
	int year;
} films [N_MOVIES];
void printmovie (movies_t movie);

int main ()
{
	string mystr;
	int n;
for (n=0; n<N_MOVIES; n++)
{
	cout << "Enter title: ";
	getline (cin,films[n].title);
	cout << "Enter year: ";
	getline (cin,mystr);
	stringstream(mystr) >> films[n].year;
}
	cout << "\nYou have entered these movies:\n";
	for (n=0; n<N_MOVIES; n++)
		printmovie (films[n]);
	return 0;
}
void printmovie (movies_t movie)
{
	cout << movie.title;
	cout << " (" << movie.year << ")\n";
}


/*************************************************************************
Pointers to Data structure 
*************************************************************************/
#include <iostream>
#include <string>
#include <sstream>
using namespace std;
struct movies_t {
	string title;
	int year;
};
int main ()
{
	string mystr;
	movies_t amovie;
	movies_t * pmovie;
	pmovie = &amovie;
	cout << "Enter title: ";
	getline (cin, pmovie->title);
	cout << "Enter year: ";
	getline (cin, mystr);
	(stringstream) mystr >> pmovie->year;
	cout << "\nYou have entered:\n";
	cout << pmovie->title;
	cout << " (" << pmovie->year << ")\n";
	return 0;
}

/*************************************************************************
Nesting Data Structures
*************************************************************************/
struct movies_t {
	string title;
	int year;
};
struct friends_t {
	string name;
	string email;
	movies_t favorite_movie;
} charlie, maria;
friends_t * pfriends = &charlie;

Access members of objects:
	charlie.name
	maria.favorite_movie.title
	charlie.favorite_movie.year
	pfriends->favorite_movie.year



/*************************************************************************
Class
*************************************************************************/
// example: one class, two objects
#include <iostream>
using namespace std;
class CRectangle {
	int x, y;
public:
	void set_values (int,int);
	int area () {return (x*y);}
};
void CRectangle::set_values (int a, int b) {
	x = a;
	y = b;
}
int main () {
	CRectangle rect, rectb;
	rect.set_values (3,4);
	rectb.set_values (5,6);
	cout << "rect area: " << rect.area() << endl;
	cout << "rectb area: " << rectb.area() << endl;
	return 0;
}

/*************************************************************************
Class Constructor
*************************************************************************/


#include <iostream>
using namespace std;
class CRectangle {
int width, height;
public:
CRectangle (int,int);
int area () {return (width*height);}
};
CRectangle::CRectangle (int a, int b) {
width = a;
height = b;
}
int main () {
CRectangle rect (3,4);
CRectangle rectb (5,6);
cout << "rect area: " << rect.area() << endl;
cout << "rectb area: " << rectb.area() << endl;
return 0;
}


/*************************************************************************
Class Constructor and Destructor
*************************************************************************/

#include <iostream>
using namespace std;
class CRectangle {
int *width, *height;
public:
CRectangle (int,int);
~CRectangle ();
int area () {return (*width * *height);}
};
CRectangle::CRectangle (int a, int b) {
width = new int;
height = new int;
*width = a;
*height = b;
}
CRectangle::~CRectangle () {
delete width;
delete height;
}
int main () {
CRectangle rect (3,4), rectb (5,6);
cout << "rect area: " << rect.area() << endl;
cout << "rectb area: " << rectb.area() << endl;
return 0;
}

/*************************************************************************
Class Pointer
*************************************************************************/

#include <iostream>
using namespace std;
class CRectangle {
		int width, height;
	public:
		void set_values (int, int);
		int area (void) {return (width * height);}
};
void CRectangle::set_values (int a, int b) {
	width = a;
	height = b;
}
int main () {
	CRectangle a, *b, *c;
	CRectangle * d = new CRectangle[2];
	b= new CRectangle;
	c= &a;
	a.set_values (1,2);
	b->set_values (3,4);
	d->set_values (5,6);
	d[1].set_values (7,8);
	cout << "a area: " << a.area() << endl;
	cout << "*b area: " << b->area() << endl;
	cout << "*c area: " << c->area() << endl;
	cout << "d[0] area: " << d[0].area() << endl;
	cout << "d[1] area: " << d[1].area() << endl;
	delete[] d;
	delete b;
	return 0;
}


/*************************************************************************
Static Members (Global variable declared within a class)
*************************************************************************/

// static members in classes
#include <iostream>
using namespace std;
class CDummy {
	public:
	static int n;
	CDummy () { n++; };
	~CDummy () { n--; };
};

int CDummy::n=0;
int main () {
	CDummy a;
	CDummy b[5];
	CDummy * c = new CDummy;
	cout << a.n << endl;
	delete c;
	cout << CDummy::n << endl;
	return 0;
}


/*************************************************************************
Friendship and Inheritance
*************************************************************************/

// friend functions
#include <iostream>
using namespace std;
class CRectangle {
	int width, height;
	public:
	void set_values (int, int);
	int area () {return (width * height);}
	friend CRectangle duplicate (CRectangle);
};
void CRectangle::set_values (int a, int b) {
	width = a;
	height = b;
}
CRectangle duplicate (CRectangle rectparam)
{
	CRectangle rectres;
	rectres.width = rectparam.width*2;
	rectres.height = rectparam.height*2;
	return (rectres);
}
int main () {
	CRectangle rect, rectb;
	rect.set_values (2,3);
	rectb = duplicate (rect);
	cout << rectb.area();
	return 0;
}


/*************************************************************************
Input and Output with filea
*************************************************************************/
// output to a file
#include <iostream>
#include <fstream>
using namespace std;
int main () {
	ofstream myfile ("example.txt");
	if (myfile.is_open())
	{
		myfile << "This is a line.\n";
		myfile << "This is another line.\n";
		myfile.close();
	}
	else cout << "Unable to open file";
	return 0;
}


//input from a file
#include <iostream>
#include <fstream>
#include <string>
using namespace std;
int main () {
string line;
ifstream myfile ("example.txt");
if (myfile.is_open())
{
	while (! myfile.eof() )
	{
		getline (myfile,line);
		cout << line << endl;
	}
	myfile.close();
}
else cout << "Unable to open file";
return 0;
}


/*************************************************************************
Determine the size of a file
*************************************************************************/
#include <iostream>
#include <fstream>
using namespace std;
int main () {
	long begin,end;
	ifstream myfile ("example.txt");
	begin = myfile.tellg();
	myfile.seekg (0, ios::end);
	end = myfile.tellg();
	myfile.close();
	cout << "size is: " << (end-begin) << " bytes.\n";
	return 0;
}



















1.Fundamanetals


2.Important Algorithms



3.Common Data Structures






1.Searching and Sorting Algorithm


int sequential_search (double list[], int listlength,double item)
{
	for (int i=0; i<listlength; i++)
		if(list[i]==item)
			return 1;
	return -1;
}



selection sort


buble sort

shellsort

quciksort

void quickSort(double list[], int listLength)
{
	quickHelp(list,0,listLength-1);
}

void quckHelp (double list[],int low,int high)
{
	const int Moving_left=0;
	const int Moving_right=1;

	if(low < high)
	{
		int left=low;
		int right=high;
		int currentDirection =Moving_left;
		double pivot=listp[low];
		while(left<right)
		{
			if (currentDirection ==Moving_left)
			{
				while(list[right] >= pivot && left <right)
					right--;
				list[left]=list[right];
				currentDirection =Moving_right;
			}
			if (currentDirection ==Moving_right)
			{
				while(list[left] <= pivot && left <right)
					left++;
				list[right]=list[left];
				currentDirection =Moving_left;
			}
		}
		list[left]=pivot;
		quickHelp(list,low,left-1);
		quickHelp(list,right+1,high);
	}
}




1.Review of C and Overview of C++			1-5,7
2.Program compilation; Seperate Compilation		12.1
3.The Make Utility					lecutre
4.Pointers and Structures in C++			9,10.1
5.Pass-by-value vs pass-by-reference			4.5, 7.2
6.automatic/global/dynamic variables;scopes		4.5
7.C++ I/Out;cin and cout; stream formatting; error checking	4.5
8.C++ classes and objects;data members;function members		10.2
9.Access Control						10.2
10.Constructors and destructor					10.2
11.Operator overloading						11.2	
12.Pass-by-value vs pass-by-reference revistied; the const modifier	lecture
13.Dynamic allocation of objects and array of objects		11.3
14.shallow vs deep copying					11.4 and lecture
15.static variables, static data members and static functions		lecture
16.Linked list						13.1
17.recursion						14
18.Binary trees						lecture
19.Inheritence						15
20.Templates						17
21.Complexity Analysis					lecuture
22.Hash Tables						lecuture