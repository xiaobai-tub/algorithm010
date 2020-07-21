学习笔记
#动态规划的实现及关键点
** java 递归代码模板
   public void recur(int level,int param){
   //terminator
   if(level > 	MAX_LEVEL){
	//process result
	return;
   }
   //process current logic;
   process(level,param);
   
   //drill down
   recur(level:level + 1,newParam);
   //restore current status;
   }
   ps:java 递归过程参数是会复制的，对于这种形式的变量传递是不需要变量恢复的
   
** 分治代码模板
	def divide_conquer(problem,param1,param2,...);
		//recursion terminator
		if problem is none;
			print_result
			return
			
		//prepare data
		data = prepare_data(problem)
		subproblem = split_problem(problem,data)
		
		//conquer subproblems
		subresult1 = self.divide_conquer(subproblems[0],p1,..)
		subresult2 = self.divide_conquer(subproblems[1],p1,..)
		subresult3 = self.divide_conquer(subproblems[2],p1,..)
		
		..
		
		// process and generate final result
		result = process_result(subresult1,subresult2,subresult3,...)
		
		//revert the current level status
		
** 动态规划的关键点 3点
	*** 最优子结构 opt[n] = best_of(opt[n-1],opt[n-2],...) 有些时候可能直接是最大值或者最小值
	*** 存储中间状态 opt[n] 这个和递归的区别是动态规划直接开辟一个新的数组，分治把状态直接放在递归的函数中
	*** 递推公式（状态转移方程或者DP方程）