#include <stdio.h>

#include <stdlib.h>


#include <time.h>

#include <string.h>

#include <ctype.h>

//Used macro

#define MAX_YR  9999

#define MIN_YR  1900

#define MAX_SIZE_USER_NAME 30

#define MAX_SIZE_PASSWORD  20

#define FILE_NAME  "PassengerRecordSystem.bin"

// Macro related to the passenger info

#define MAX_PASSENGER_NAME 50

#define MAX_PASSENGER_ADDRESS 300

#define MAX_PASSENGER_MOB_NUM 20

#define FILE_HEADER_SIZE  sizeof(sFileHeader)

//structure to store date

typedef struct
{

    int yyyy;
    
    int mm;
    
    int dd;
    
} Date;

typedef struct

{
    char username[MAX_SIZE_USER_NAME];
    
    char password[MAX_SIZE_PASSWORD];
    
} sFileHeader;

//Elements of structure

typedef struct// to call in program

{
    unsigned int passengerId; // declare the integer data type
    
    float ticketPrice;
    
    unsigned int passengerSeatNum;
    
    Date passengerTravelingDate;// declare the integer data type
    
    char passengerName[MAX_PASSENGER_NAME];// declare the character array for the name
    
    char passengerMobNum[MAX_PASSENGER_MOB_NUM];// declare the character array for the name
    
    char passengerAddr[MAX_PASSENGER_ADDRESS];// declare the character array for the address
    
} s_PassengerInfo;

//Own version of fgetsRemovedNewLine

void fgetsRemovedNewLine(char * restrict buf, int n,FILE * restrict stream)

{
    if (fgets(buf, n, stream) == NULL)
    
    {
        printf("Fail to read the input stream");
        
    }
    else
    
    {
        buf[strcspn(buf, "\n")] = '\0';
        
    }
}
//Align the message

void printMessageCenter(const char* message)

{
    int len =0;
    
    int pos = 0;
    
    //calculate how many space need to print
    
    len = (78 - strlen(message))/2;
    
    printf("\t\t\t");
    
    for(pos =0 ; pos < len ; pos++)
    
    {
        //print space
        
        printf(" ");
        
    }
    
    //print message
    
    printf("%s",message);
}
