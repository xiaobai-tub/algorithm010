## 正常脑回路的写法 复杂度n！
class Solution {
    int[] main ;
    int[] second;
    int[] col ;
    int[] quene ;
    int n;
    List<List<String>> res = new ArrayList<List<String>>();
    public List<List<String>> solveNQueens(int n) {
        int[] main = new int[2 * n];
        int[] second = new int[4 * n];
        int[] col = new int[n];
        int[] quene = new int[n];
        this.n = n;
        recur(0);
        return res;
        
    }        

    
        Boolean isUnderAttack(int row,int col){
            int o = main[row+col] + second[row-col+2n] + col[col];
            return o == 1?true:false;
        }
        void recur(int row){
            for(int i = 0;i < n;i++){
                placeQuene(row,i);
                if(row == n-1)addResult();
                else recur(row + 1);
                removeQuene(row,i);

            }

        }
        void placeQuene(int row,int col){
            quene[row] = col;
            main[row+col] = 1;
            second[row-col+2n] = 1;
            col[col] = 1;
        }
        void removeQuene(int row,int col){
            quene[row] = 0;
            main[row+col] = 0;
            second[row-col+2n] = 0;
            col[col] = 0;
        }
        void addResult(int i){
            for(int r = 0;r < quene.length;r++){
            List<String> re = new ArrayList<>();
            int col = quene[i];
                for(int i = 0;i< col;i++){
                    re.add('.');
                }
                re.add('Q');
                for(int i = 0;i < n-col-1;i++){
                    re.add('.');
                }
                res.add(re);
            }  
        }

}