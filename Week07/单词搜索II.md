class Solution {
    public List<String> findWords(char[][] board, String[] words) {
        List<String> result = new ArrayList<String>();

        node node = buildTree(words);
          for(int i = 0;i< board.length;i++){
            for(int j = 0;j < board[0].length;j++){
                dps(board,i,j,node,result);
            }
        }
        return result;
    }
    public void dps(char[][] board,int i,int j,node node,List<String> result){
        char c = board[i][j];
        if( c == '#' || node.next[c-'a'] == null ) return;
        node = node.next[c-'a'];
        if(node.word != null) { 
            result.add(node.word); 
            node.word = null;}   
        board[i][j] = '#';

        if (i > 0)dps(board,i-1,j,node,result);
        if (i < board.length - 1)dps(board,i+1,j,node,result);
        if (j > 0)dps(board,i,j - 1,node,result);
        if (j < board[0].length - 1)dps(board,i,j + 1,node,result);
        board[i][j] = c;


    }

    public node buildTree(String[] words){
        node root= new node();
        for(String word: words){
            node node = root;
            for(char c:word.toCharArray()){
                  if(node.next[c - 'a'] == null) 
                   node.next[c - 'a'] = new node();
                   node = node.next[c - 'a'];
            }
            node.word = word;
        }
        return root;
    }

    class node{
       node[] next = new node[26];
       String word;
       node(){

       }
    }
}