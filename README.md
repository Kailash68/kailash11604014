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
         }
 
    int fileOpen = open( argv[1], 0 );
    int targetFile = open( argv[2], 0666 );
     
    if ( fileOpen == -1 || targetFile == -1 ) {
        printf( "Opening file failed " );
        exit(1);
    }
    childid = fork();
 
    if( childid == 0 ) {
