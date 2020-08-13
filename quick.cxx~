/*
 * quick.cxx
 *
 * Copyright 2016 Gabriel Vargas <gabreta@VmGabriel96>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 * MA 02110-1301, USA.
 *
 *
 */


#include <iostream>
#include <time.h>
#include <sys/time.h>

using namespace std;

double timeval_diff(struct timeval *a, struct timeval *b)
{
    return
	(double)(a->tv_sec + (double)a->tv_usec/1000000) -
	(double)(b->tv_sec + (double)b->tv_usec/1000000);
}

void intercambio (int * a, int posa,int posb)
{
    //posa = posicion de origen
    //posb = posicion de destino
    int t=a[posb];
    a[posb]=a[posa];
    a[posa]=t;
}

int aleatorio ()
{
    int a = rand() % 5000 + 5000;
    return a;
}

void llenar (int * a, int n)
{
    for (int i=0;i<n;i++)
    {
	a[i]=aleatorio();
    }
}

void imprimir (int * a, int n)
{
    cout <<"[ ";
    for (int i=0;i<n;i++)
    {
	cout<<a[i]<<" ";
    }
    cout <<"]"<<endl;
}

void ordenrapido(int * a, int izq, int der)
{
    int i, j;
    int v;
    if (der> izq)
    {
        v= a[der];
        i = izq -1;
        j= der;
        for(;;)
        {
            while (a[++i]<v);
            while (a[--j] >v);
            if(i>=j) break;
            intercambio(a,i,j);
        }
        intercambio(a, i, der);
        ordenrapido(a, izq, i-1);
        ordenrapido(a, i+1,der);
    }
}

int main(int argc, char **argv)
{
    int n;
    for (n=50;n<=500;n+=10)
    {
	struct timeval t_ini, t_fin;
	double secs;
	
	int * num = new int[n];
	llenar(num,n);
	//cout<<"Funcion sin Ordenar"<<endl;
	//cout<<"------------------"<<endl;
	//cout<<"------------------"<<endl;
	//cout<<"Funcion Ordenada"<<endl;
	//cout<<"------------------"<<endl;
	gettimeofday(&t_ini, NULL);
	ordenrapido(num,0,n);
	gettimeofday(&t_fin, NULL);

	secs = timeval_diff(&t_fin, &t_ini);

	//cout<<"------------------"<<endl;

	cout<<"Time with "<<n<<" is "<<secs<<endl;
    }
    return 0;
}
