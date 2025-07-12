<h1># tic-tac-toe-game-using-c-language</h1>


#include<stdio.h>
int board[3][3] = {0};
int i,j;
//this is the function to print the board for tic tac toe
void printboard(){
    for(i = 0;i<=2;i++){
         for(j = 0;j<=2;j++){
            if (board[i][j] == 0){
                printf(".");}
            else 
            {
                printf("%d",board[i][j]);
            }
            if(j<2){
            printf("|");}
            }
            if(i<2){
                printf("\n________\n");    
        }  
    }//printf("\n");
};
int checkwinner(){
     for(i = 0;i<=2;i++){
      
       if(board[i][0]!= 0 && board[i][0] == board[i][1] && board[i][1] == board[i][2] ){
        return board[i][0];//for rows 
       }}
        for(j = 0;j<=2;j++){
        if(board[0][j]!= 0 && board[0][j] == board[1][j] && board[1][j] == board[2][j]){
        return board[0][j];//for columns
       }}
        if (board[0][0]!=0 && board[0][0] == board[1][1] && board[1][1] == board[2][2]){
        return board[0][0];//for diagonal 
       }
       else if(board[0][2]!= 0 && board[0][2] == board[1][1] && board[1][1] == board[2][0]){
       return board[0][2];//for second diagonal
       }
       return 0;   
};
int isdraw(){
    for(i = 0;i<=2;i++){
        for(j =0;j<=2;j++){
            if(board[i][j] == 0){
                return 0;
            }    
        }
    }
    return 1;
};
int main(){
    int player = 1;
    int row,col;
    printf("WELCOME TO THE TIC TAC TOE GAME ");
    printf("\nplayer 1 -> 1 and player 2 -> 2\n");
    while(1){
       
        printboard();
        printf("\nplayer %d : enter the row and column you want to chose(0-2)",player);
        scanf("%d %d",&row,&col);
        if( row < 0 || row > 2 || col>2 || col<0 || board[row][col]!= 0 ){
            printf("inavlid move ");
            continue;
        }
        board[row][col] = player;
        int winner = checkwinner();
        if (winner) {
            printboard();
            printf("Player %d wins!\n", winner);
            break;
        }
         else if (isdraw()) {
            printboard();
            printf("It's a draw!\n");
            break;
        }
        if (player == 1){
            player = 2;}
        else
            player = 1;
            printf("\n");

    };

  return 0;}
