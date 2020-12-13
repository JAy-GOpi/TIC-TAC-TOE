#include <stdio.h>
#include <stdlib.h>

int validity(char ar[],int num)                     //asks for user enter and add X or O in board
{                                                   //checks if entered character is valid or invalid
    char check='0';                                 //and updates table in X or O if character is valid
    char turn;
    int n;
    char c;

        if (num%2==0)   {turn='1';}
        else            {turn='2';}

        do{

            fflush(stdin);
            printf("\nplayer %c put Your %c : ",turn,turn=='1'?'X':'O');
            scanf("%d",&n);
            printf("\n");

        if (ar[n-1]=='X' || ar[n-1]=='O'){
            printf("invalid selection\n");
            check ='0';
            getch();
            continue;
        }

        if (n<1 || n>9){
            printf("invalid selection\n");
            check ='0';
            getch();
            continue;
        }
        if (n==1 || n==2 || n==3 || n==4 || n==5 || n==6 || n==7 || n==8 || n==9 ){
            if (turn=='1'){ return ar[n-1]='X'; }
            if (turn=='2'){ return ar[n-1]='O'; }
            check ='1';
            break;
        }
        else{
            printf("invalid selection\n");
            check ='0';
            getch();
            continue;
        }

        }while(check!='1');

};
void board(char ar[]){                                  //draws board

    system("cls");
    printf("---Tic Tac Toe---\n\n");
    printf("-'X' for player 1\n-'O' for player 2\n\nlets start game\n\n");

    printf("     |     |     \n");
    printf("  %c  |  %c  |  %c  \n",ar[0],ar[1],ar[2]);
    printf("_____|_____|_____\n");
    printf("     |     |     \n");
    printf("  %c  |  %c  |  %c  \n",ar[3],ar[4],ar[5]);
    printf("_____|_____|_____\n");
    printf("     |     |     \n");
    printf("  %c  |  %c  |  %c  \n",ar[6],ar[7],ar[8]);
    printf("     |     |     \n\n");



};

int result(char ar[]){                                  //checks if win or draw

    if(ar[0]==ar[1] && ar[0]==ar[2] && ar[0]=='O'){return 2;}  //row match for 'O'
    if(ar[3]==ar[4] && ar[3]==ar[5] && ar[3]=='O'){return 2;}
    if(ar[6]==ar[7] && ar[6]==ar[8] && ar[6]=='O'){return 2;}

    if(ar[0]==ar[3] && ar[0]==ar[6] && ar[0]=='O'){return 2;}  //column match for 'O'
    if(ar[1]==ar[4] && ar[1]==ar[7] && ar[1]=='O'){return 2;}
    if(ar[2]==ar[5] && ar[2]==ar[8] && ar[2]=='O'){return 2;}

    if(ar[0]==ar[4] && ar[0]==ar[8] && ar[4]=='O'){return 2;}  //cross match for 'O'
    if(ar[2]==ar[4] && ar[2]==ar[6] && ar[4]=='O'){return 2;}


        if(ar[0]==ar[1] && ar[0]==ar[2] && ar[0]=='X'){return 1;}  //row match for 'X'
        if(ar[3]==ar[4] && ar[3]==ar[5] && ar[3]=='X'){return 1;}
        if(ar[6]==ar[7] && ar[6]==ar[8] && ar[6]=='X'){return 1;}

        if(ar[0]==ar[3] && ar[0]==ar[6] && ar[0]=='X'){return 1;}  //column match for 'X'
        if(ar[1]==ar[4] && ar[1]==ar[7] && ar[1]=='X'){return 1;}
        if(ar[2]==ar[5] && ar[2]==ar[8] && ar[2]=='X'){return 1;}

        if(ar[0]==ar[4] && ar[0]==ar[8] && ar[4]=='X'){return 1;}  //cross match for 'X'
        if(ar[2]==ar[4] && ar[2]==ar[6] && ar[4]=='X'){return 1;}


            if(ar[0]=='1'){return 3;}
            if(ar[1]=='2'){return 3;}
            if(ar[2]=='3'){return 3;}
            if(ar[3]=='4'){return 3;}
            if(ar[4]=='5'){return 3;}
            if(ar[5]=='6'){return 3;}
            if(ar[6]=='7'){return 3;}
            if(ar[7]=='8'){return 3;}
            if(ar[8]=='9'){return 3;}


    else return 0;


};

void main()                                                 //our main
{

    char ar[9]={'1','2','3','4','5','6','7','8','9'};
    int num=0;


    do{
        board(ar);
        validity(ar,num);

        num++;

    }while(result(ar)==3);

    board(ar);

    if(result(ar)==1){printf("player 1 wins\n");}
    if(result(ar)==2){printf("player 2 wins\n");}
    if(result(ar)==0){printf("game draw\n");}

}
