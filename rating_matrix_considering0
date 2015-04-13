#include <cassert>
#include <cctype>
#include <cstdio>
#include <cstdlib>
#include <cstring>
#include <ctime>
#include <algorithm>
#include <bitset>
#include <deque>
#include <iostream>
#include <iomanip>
#include <limits>
#include <list>
#include <map>
#include <queue>
#include <set>
#include <sstream>
#include <stack>
#include <utility>
#include <vector>
#include <fstream>
#include<cmath>
//approx 43 minutes
	int user_bo[10003][1003];
//	int rated_mat[10003][1003];
using namespace std;
int main()
{
	int first_10000_us[10008];
	ifstream user_book;
	user_book.open("user_book_matrix.txt");
	int count = 0;
	int book,i,j,k;
	clock_t start = clock();
	char ch;

	map<int,map<string,int> > only_rated;

		for(i=0;i<500;i++)  {
			for(j=0;j<1000;j++) {
				user_book>>book>>ch;
				user_bo[i][j]=book;         //user book rating matrix
			/*	if(j==1 || j==2)
				cout<<user_bo[i][j]<<" ";*/

			}
		/*	cout<<endl;
			if(i==2)
			break;*/
		}
		user_book.close();
		ifstream max_users;
		max_users.open("max_10000.txt");
		for(i=0;i<10000;i++) {
			for(j=0;j<=1;j++) {
				max_users>>k;
			first_10000_us[i] = k;   // to store users id
			}
			/*cout<<endl;
			if(i==5)
			break;*/
		}
		 max_users.close();

		 ifstream max_books;
		 max_books.open("max_1000.txt");
		 string first_1000_bo[1002];      // to store books id
		 string g;
		for(i=0;i<1000;i++) {
			max_books>>g;
			first_1000_bo[i]=g;
		/*	cout<<g<<endl;
			if(i==5)
			break;*/
		}
		ifstream infile;
		double U_2d[10003][3];
		double a;
		infile.open("U.txt");
		for(i=0;i<10000;i++) {
			for(j=0;j<10000;j++) {
					infile>>a>>ch;
					if(j==0 || j== 1) {
						U_2d[i][j] = a;        // matrix of U in 2 dimension
					//	cout<<a<<" ";
					}
					//cout<<a<<" ";
			}
		}
		cout<<"u2d= "<<U_2d[9999][0]<<"     "<<U_2d[9999][1]<<endl;
		infile.close();
			double den,num,simusr,min,dist;
            cout<<"till here done\n";
			int pos=0;
			for(i=0;i<1000;i++)  {
				for(j=0;j<1000;j++) {         //to access book columns
							min = 2.0;
							for(k=0;k<1000;k++) {
								if(i!=k) {
									if(user_bo[k][j]!=0) {
										num = (U_2d[i][0] * U_2d[k][0]) + (U_2d[i][1] * U_2d[k][1]);
										den = ( (pow(U_2d[i][0],2)*pow(U_2d[i][1],2)) + (pow(U_2d[k][0],2)*pow(U_2d[k][1],2)) );
										den = sqrt(den);
										if(den!=0)
										simusr = num/den;
										else
                                        simusr = 2;
										//dist = ((U_2d[i][0]-U_2d[k][0]) * (U_2d[i][0]-U_2d[k][0]))+((U_2d[i][1]-U_2d[k][1]) * (U_2d[i][1]-U_2d[k][1]));
										if(simusr<0)
										simusr *= -1;
										if(min > simusr)  {
											min = simusr;
											pos = k;
										}
									}
								}
							}
							user_bo[i][j] = user_bo[pos][j];
					}
				}
				cout<<"till here not done\n";
				ofstream f("final_rated_matrix_considering0.txt");
				ofstream checkpre("bool_user_book_considering0.txt");
				for(i=0;i<500;i++) {
                    for(j=0;j<1000;j++) {
                            f<<user_bo[i][j]<<",";  // final rated matrix
                            if(user_bo[i][j] > 8)
                                checkpre <<1<<" ";
                            else
                                checkpre<<0<<" ";
                    }
                    checkpre<<endl;
                    f<<endl;
				}
                // to find error

			clock_t end = clock();
		printf("time = %lf",((float)(end-start)/CLOCKS_PER_SEC));


	return 0;
}
