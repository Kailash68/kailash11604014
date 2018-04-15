#include<stdio.h>
#include<sys/types.h>
#include<sys/stat.h>
#include<fcntl.h>
#include<string.h>
#include<stdlib.h>
 
int main( int argc, char* argv[] ) 
{
    int fdone[2];
    pid_t childid;
    char readBuff[50];
    char writeBuff[50];
    int readCounter;
 
    pipe( fdone );
 
    if( argc < 3 ) {
        printf( "Atleast need 2 params " );
        exit(1);
