class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        for(int i=0;i<9;i++)
        {
            for(int j=0;j<9;j++)
            {
                if(board[i][j]!='.') 
                {
                    char c = board[i][j];
                    if(isvalid(i, j, c, board) == false)
                    return false;
                }
            }
        }
        return true;
    }
    bool isvalid(int row, int col, int c, vector<vector<char>> &board)
    {
        int count =0;
        for(int k=0;k<9;k++)
        {
            if(board[row][k] == c) count++;
            if(board[k][col] == c) count++;
            if(board[3*(row/3) + k/3][3*(col/3) + k%3] == c)  count++;
        }
        return count >3 ? false : true;
    }
};
