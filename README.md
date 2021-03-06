# leetcodeNotebook
record some thoughts


1. topological sort
* Course Schedule: https://leetcode.com/problems/course-schedule/ <br>
* Course Schedule ii: https://leetcode.com/problems/course-schedule-ii/ <br>
  Main ideas: use inDegree array to record the prerequisites relationship between courses, use stack to control and traverse the whole graph. 
  ```java
  public boolean canFinish(int numCourses, int[][] prerequisites) {
    int count = 0;
    int[] inDegree = new int[numCourses];
    //record the in-degree of each vertes
    for(int i = 0; i < prerequisites.length; i++){
      inDegree[prerequisites[i][0]]++;
    }
    //find the vertex with zero in-degree and put it in the stack
    LinkedList<Integer> stack = new LinkedList<>();
    for(int i = 0; i < inDegree.length; i++){
      if(inDegree[i] == 0)
        stack.push(i);
    }
    //traverse the graph
    while(!stack.isEmpty()){
      int cur = stack.pop();
      for(int i = 0; i < prerequisites.length; i++){
        if(prerequisites[i][1] == cur)
          inDegree[prerequisites[i][0]]--;
          if(inDegree[prerequisites[i][0]] == 0)
            stack.push(inDegree[prerequisites[i][0]]);
    }
    return count == numCourses;
  }
  ```

2. binary search
* Good summary from Grandyang: https://www.cnblogs.com/grandyang/p/6854825.html
* Search in Rotated Sorted Array: https://leetcode.com/problems/search-in-rotated-sorted-array/

3. DFS
* Combinations: https://leetcode.com/problems/combinations/

4. LCS(Longest Common Subsequence)
* Longest Common Subsequence: https://leetcode.com/problems/longest-common-subsequence/
