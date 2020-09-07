# leetcodeNotebook
record some thoughts


1. topological sort
* Course Schedule: https://leetcode.com/problems/course-schedule/
  Main ideas: use inDegree array to record the prerequisites relationship between courses, use stack to control and traverse the whole graph. 
        
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
