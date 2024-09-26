class Solution {
    public long totalCost(int[] costs, int k, int candidates) {
        PriorityQueue<int[]> pql = new PriorityQueue<>((a,b)->a[0] - b[0] == 0 ? a[1] - b[1] : a[0] - b[0]);
        PriorityQueue<int[]> pqr = new PriorityQueue<>((a,b)->a[0] - b[0] == 0 ? a[1] - b[1] : a[0] - b[0]);
        
        int l = 0;
        int r = costs.length -1 ;
        int n = costs.length;
        
        if(2* candidates >= n){
            
            int res = 0;
            PriorityQueue<int[]> rem = new PriorityQueue<>((a,b)->a[0] - b[0] == 0 ? a[1] - b[1] : a[0] - b[0]);
            for(int i = 0; i < n ; i++){
                rem.add(new int[]{ costs[i], i});
            }
            
            for(int j =0; j < k; j++){
                res += rem.poll()[0];
            }
            return res;
        }

        for(int i = 0; i < candidates && i < n ; i++){
            pql.add(new int[]{ costs[l], l});
            l++;
            pqr.add(new int[]{ costs[r], r});
            r--;
        }
        long res = 0;
        int i= 0;
        for(; i < k && l <= r; i++){
            
            if(pql.peek()[0] < pqr.peek()[0]){
                res += pql.poll()[0];
                pql.add(new int[]{ costs[l], l});
                l++;
            }else if(pql.peek()[0] > pqr.peek()[0]){
                res += pqr.poll()[0];
                pqr.add(new int[]{ costs[r], r});
                r--;
            }else{
                if(pql.peek()[1] < pqr.peek()[1]){
                    res += pql.poll()[0];
                    pql.add(new int[]{ costs[l], l});
                    l++;
                }else{
                    res += pqr.poll()[0];
                    pqr.add(new int[]{ costs[r], r});
                    r--;
                }
            }
        }
        
        PriorityQueue<int[]> rem = new PriorityQueue<>((a,b)->a[0] - b[0] == 0 ? a[1] - b[1] : a[0] - b[0]);
        rem.addAll(pql);
        rem.addAll(pqr);
        for(; i < k; i++){
            res += rem.poll()[0];
        }
        
        return res;
        
    }
}
