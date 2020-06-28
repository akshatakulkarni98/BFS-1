# BFS-1
# Problem 1
Binary Tree Level Order Traversal (https://leetcode.com/problems/binary-tree-level-order-traversal/)


# Problem 2
Course Schedule (https://leetcode.com/problems/course-schedule/)

class Solution {
public:
    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {

        vector<int> count(numCourses,0);
        unordered_map<int,vector<int>> map;
        queue<int> q;

        for(int i=0;i<prerequisites.size();i++){
            count[prerequisites[i][0]]++;
            map[prerequisites[i][1]].push_back(prerequisites[i][0]);
        }


        for(int i=0;i<count.size();i++){
            if(count[i] == 0){
                q.push(i);
            }
        }

        while(!q.empty()){
            int sub = q.front();
            q.pop();
            for(auto it:map[sub]){
                count[it]--;
                if(count[it] ==0)
                    q.push(it);
            }   
        }
        for(int i=0;i<count.size();i++){
            if(count[i]>0){
                return false;
            }
        }
        return true;

    }
};

# Problem 3
Binary Tree Right Side View (https://leetcode.com/problems/binary-tree-right-side-view/)
