﻿# LeetCode刷题笔记
## 每道题目需要注意的地方
1. **两数之和**
	1. 可以用暴力方法
	2. 推荐使用HashMap(key,value)处理
2. **两数相加**
	1. 链表的相加 (✖)
3. 最长子串长度(✖)    变形：求最长子串    
	思路：因为求解字符串中不包含重复字符的最长子串的长度。因为可以利用到java中天然不包含重复元素的结构Set。  
		1. 首先肯定得做原字符串是否是空字符串的判断  
		2. 可以定义两个变量pre(表示子串的前端)、i(表示字符串的当前位置)、maxLength(当前子串最长的长度)  
		3. 开始循环整个字符串，如果遇到了相同的字符，则计算当前子串长度，并且与maxLength做比较,并且pre的位置转移到(i+1)的位置，
				当然，这中间肯定需要再加一层while循环，用于转移pre。   
		4. 最后比较前面循环中的maxLength和最后的(i-pre)之间的大小。 
			
	3.1 **最长子串**  
		假设本题要求找出无重复的最长子串，则需要用两个变量保存窗口的左右位置，每当max_str更新的时候，
		就需要更新此时的窗口左右位置。最终使用s.substring(left, right)获取最长子串。

5. 最长回文子串    	
	1. 第一种方法：提供最暴力的方法   时间复杂度接近  O(n^3)   (超时)    
		1. 从最长的字符串开始迭代，如果找到了回文字符串则终止循环   
		2. 采用由两端 到中心的方法检验字符串是否为回文字符串。  
	2. 第二种方法：采用动态规划的方式。  时间复杂度O(n^2),空间O(n^2) 
		1. dp[i][j] 表示子串s[i…j]是否是回文
		2. 初始化：dp[i][i] = true (0 <= i <= n-1);  dp[i][i-1] = true (1 <= i <= n-1); 其余的初始化为false
		3. dp[i][j] = (s[i] == s[j] && dp[i+1][j-1] == true)(内部再用两个循环来遍历)
		4. 注意具体代码中：可以将字符串的长度按照length = 1 length = 2 、length > 2 来分别讨论，分别用k、i、j来表示长度、开始、结束
	3. 第三种方式：分别以每一个字符为中心，求解每个字符最长的偶数回文串及奇数回文串    时间复杂度O(n^2)，空间O(1)  
		1. 特点：上面两种方式，都只是定义start、及结果的length，而不是直接求end的位置。
		2. 主要是在一个for循环中，做两个while循环，分别做奇偶处理
6. z字形变化
	1. 第一种：按照每个字符所在的行进行排序，从左到右遍历字符串，将字符串填到合适的行，只有到移到最上方和最小法时方向才会改变。
	2. 第二种：按行访问，找出每个元素下标索引对应的规律。
		
		
7. 反转整数 
	1. 这个自己使用StringBuffer来处理的，全部的知识都和String相关，个人认为也是可以的，但是系统没有通过。
	2. 但是，估计这道题目目的在与考察，类似于栈的运用，及换个手段来判断是否存在溢出的情况。

8. 字符串整数
	1. 思路：去掉首尾段的空白字符、判断是否为空、标记正负、剔除空白字符、判断数值是否超过范围

9. 回文数
	1. 第一种：将数字转化为字符串
	2. 第二种：对数字求余，将余数分别存储在栈和队列中，利用一个“先进后出”，一个“先进先出”的特点

	
## 分类别讨论问题

### 链表
题目|java|
:----|:----:|
[删除链表的倒数第N个节点](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/RemoveNthFromEndMethod.java)|
[合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/MergeTwoListsMethod.java)|
[两两交换链表中的结点](https://leetcode-cn.com/problems/swap-nodes-in-pairs/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListSwapNode.java)|
[旋转链表](https://leetcode-cn.com/problems/swap-nodes-in-pairs/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListRotateRight.java)|
[删除排序链表中的重复元素](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list) | [答案1](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListRemoveNode.java) |
[删除排序链表中的重复元素](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list) | [答案2](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListRemoveNode2.java)|
[删除排序链表中的所有重复元素](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListRemoveAllSameNode.java)|
[分割链表](https://leetcode-cn.com/problems/partition-list/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListDivided.java)|
[反转链表](https://leetcode-cn.com/problems/reverse-linked-list/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListReverse.java)|
[反转部分链表](https://leetcode-cn.com/problems/reverse-linked-list-ii) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListPartReverse.java)|
[有序链表转换二叉搜索树](https://leetcode-cn.com/problems/convert-sorted-list-to-binary-search-tree/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListSortedToBST.java)|
[复制带随机指针的链表](https://leetcode-cn.com/problems/copy-list-with-random-pointer/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/src/com/hone/SwordOffer025/ComplicationLinkedCopy.java)|
[环形链表](https://leetcode-cn.com/problems/linked-list-cycle) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListHasCircle.java)|
[环形链表](https://leetcode-cn.com/problems/linked-list-cycle) | [答案2](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListHasCircle2.java)|
[环形链表的入口结点](https://leetcode-cn.com/problems/linked-list-cycle-ii/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListHasCircleDeleteEntry.java)|
[对链表进行插入排序](https://leetcode-cn.com/problems/insertion-sort-list) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListInsertSort.java)|
[排序链表](https://leetcode-cn.com/problems/sort-list/description/) | [答案1](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListSort.java)|
[排序链表](https://leetcode-cn.com/problems/sort-list/description/) | [答案2](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListSort2.java)|
[相交链表](https://leetcode-cn.com/problems/intersection-of-two-linked-lists/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListCommonNode.java)|
[两数相加](https://leetcode-cn.com/problems/add-two-numbers) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListAdd.java)|
[两数相加2](https://leetcode-cn.com/problems/add-two-numbers-ii) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListAdd2.java)|
[奇偶位置链表](https://leetcode-cn.com/problems/odd-even-linked-list/description/) | [答案1](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListoddEvenList.java)|
[奇偶位置链表](https://leetcode-cn.com/problems/odd-even-linked-list/description/) | [答案2](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListoddEvenList2.java)|
[删除链表中的结点](https://leetcode-cn.com/problems/remove-linked-list-elements/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListRemoveSomeNode.java)|
[回文链表](https://leetcode-cn.com/problems/palindrome-linked-list/description/) | [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/list/ListPalindrome.java)|




### 字符串
题目|java|
:----|:----:|
[字符串循环左移](https://www.nowcoder.com/practice/12d959b108cb42b1ab72cef4d36af5ec?tpId=13&tqId=11196&tPage=3&rp=3&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)| [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/string/StringLeftRotate.java)|
[最长公共子序列](https://www.cnblogs.com/xiaxj/p/7245840.html)|[答案](https://www.cnblogs.com/xiaxj/p/7245840.html)|
[字符串的全排列](https://www.nowcoder.com/practice/fe6b651b66ae47d7acce78ffdd9a96c7?tpId=13&tqId=11180&tPage=2&rp=2&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)|[答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/src/com/hone/SwordOffer027/StringSort.java)|
[最长回文子串](https://www.cnblogs.com/xiaxj/p/9613842.html)|[答案](https://www.cnblogs.com/xiaxj/p/9613842.html)|


### 树
题目|java|
:----|:----:|
[二叉树先序遍历](https://leetcode-cn.com/problems/binary-tree-preorder-traversal)| [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/tree/PreorderTraversal.java)|
[二叉树中序遍历](https://leetcode-cn.com/problems/binary-tree-inorder-traversal)| [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/tree/InorderTraversal.java)|
[二叉树后序遍历](https://leetcode-cn.com/problems/binary-tree-postorder-traversal)| [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/tree/PostorderTraversal.java)|
[二叉树层序遍历1](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/description/)| [答案](https://github.com/xiaAde/LeetCodeExercise/blob/master/LeetCode/tree/LevelOrderTraversal.java)|




### 排序
题目|java|
:----|:----:|

### 动态规划问题
:----|:----:|
[等差数列划分](https://leetcode-cn.com/problems/arithmetic-slices/description/)|[答案](https://www.cnblogs.com/xiaxj/p/9693046.html)|
[比特位计数](https://leetcode-cn.com/problems/counting-bits/)|[答案](https://www.cnblogs.com/xiaxj/p/9692902.html)|
[石头游戏](https://leetcode-cn.com/problems/stone-game/description/)|[答案](不会啊)|
[最长上升子序列](https://leetcode-cn.com/problems/longest-increasing-subsequence/description/)|[答案](https://www.cnblogs.com/xiaxj/p/9696606.html)|






	


# 剑指Offer笔记
## 每道题目需要注意的地方
1. **二维数组的查找(AC)**
	1. 思路：因为矩阵是有序的，所有可以将初始值定在左下角。(当然也可以定义在右上角)    
		从左下角来看，如果target大于左下角的数，则向右移;小于,则向左移动。
			
2. **替换空格(AC)**
	1. 这个主要利用replaceAll()。
	2. 从后往前替换
		
3. **从尾到头打印链表(AC)**
	1. 第一种方法：可以利用链表和栈的不同属性。栈(先进后出)，链表(先进可以先出).
	2. 递归(这种方法比较奇妙).

4. **重建二叉树(AC)**  
	其实就是根据前序遍历和中序遍历还原二叉树
	1. 第一个方法：肯定利用递归的思想。(技巧：重新构建一个方法)。
		前序遍历第一个元素肯定是二叉树的根节点，再根据该节点二分中序遍历数组。

5. **两个栈实现队列(AC)**
	1. 利用栈的先进后出，队列先进先出的性质

6. **旋转数组中的最小值(AC)**   
	其实该题目核心就是考察二分法。数组分为两半，每一半都是已经排好序的。
	1. 利用旋转数组的性质。a[i+1] < a[i] ,则整个a[i+1]一定是整个旋转数组最小值。
	2. 利用二分法。
	
7. **求解斐波那切数列(AC)**  
	1. 递归(时间复杂度不可控)
	2. 动态规划(定义两个变量,f,g. 时间复杂度 = O(n))
	3. 或者开辟一个n维数组的空间，其实和前面动态规划的思路差不多。
	
8. **跳台阶(AC)** 
	1. 其实核心就是找规律(斐波那切数列)
	2. 对于斐波那切数列，可以用递归或者迭代来解决。
	
9. **变态跳台阶(AC)** 
	1. 其实核心就是找规律(斐波那切数列)

10. **矩阵覆盖(AC)**
	1. 其实也是一个斐波那切数列问题，需要仔细分析，寻找规律。

11. **二进制中1的个数(AC)**
	1. 解法很奇妙(利用到位与运算的性质)[思路](https://www.nowcoder.com/questionTerminal/8ee967e43c2c4ec193b040ea7fbb10b8)
	
12. **数值的整数次方(AC)**	
	0. 思路：简单快速幂。
	1. 主要判断指数正负，底数是否为零的情况。
	2. 写出指数的二进制表示形式。
	3. 通过&1和>>1来逐位读取1101，为1时将该位代表的乘数累乘到最终结果。

13. **调整数组顺序使奇数在偶数的前面(AC)**		
	1.首先分别用两个LinkedList存储元素，将奇数和偶数元素分开存储，然后在存回到数组中。
	2. 方法2：利用类似于插入排序的思路。但是节省了空间，却消耗了时间。
	
14. **链表中倒数第k个结点(AC)**	
	1. 思路：首先统计该链表总共有多少个结点，查找倒数第k个结点，其实就是顺着的count-k个结点
	2. 思路：先让两个指针都指向头结点，然后让一个正走k步，到达第k个结点。
			然后两个指针同时往后移动，当第一个结点到达末尾的时候，第二个结点所在位置就是倒数第ķ个节点了。其实这么做的核心也是求正向的第N-K个。  
			注意如果k>N,则直接范湖Null。
	
15. **翻转链表(AC)**	
	1. 思路1：定义四个结点：pre、current、newHead、tmp
	2. 思路2：定义两个结点，next、pre

16. **合并两个排序的链表(AC)**
	1. 第一种方法：递归调用法。每次都读取list1或者list2上面的某一个值
	2. 第二种方法：上面思想的非递归版本。
	
17. **判断一个二叉树A是否包含二叉树B(AC)**
	1. 思路：采用递归的方式。  
			只有在root1和root2都不为空的时候，才开始判断，首先判断根节点组成的树(这里面需要利用到递归，利用递归判断该节点组成的树)， 
			是否是相等。
		
18. **二叉树的镜像(AC)**
	1. 递归
	2. 利用栈实现非递归的变换(每次都将根节点压入栈中)
		
19. **顺时针打印矩阵(NoByMyself)**
	1. 找规律的题目：核心就是找出整个矩阵需要几个圆圈。  
		然后依次左——右，上——下，右——左，下——上。开始依次遍历。
		
20. **构建包含min函数的栈(AC)**
	1. 因为题目中提供了一个stack包，我们可以借助辅助的Stack,再构建一个minStack.每次都把Stack中的最小元素存储在min中。
	2. 我们可以构建两个stack空间，一个用于正常的存储元素，一个按照顶部元素最小的来存储元素。

21. **栈的压入和弹出序列判断(NoByMyself)**
	1. 思路：模拟入栈的顺序，及出栈的顺序。如果最后出栈顺序可以吻合的话，则辅助栈空间最后为空。

22. **从上到下打印二叉树(AC)**
	1. 思路：题目本质考察的是层序遍历。可以借助队列的先进先出的性质，每次弹出一个结点，则压入左、右孩子结点。

23. **二叉搜索树的后序遍历序列(NoByMyself)**
	1. 二叉搜索树：对于二叉树，左子树所有结点数值比根节点小，右子树所有结点数组比根节点大。并且左、右子树的本身也是二叉搜索树(递归思想)
				   思路：最后一个点肯定是根节点，从根节点往前面遍历，如果找到比end小的点，则说明前半部分是左子树，然后判断左子树是否全部小于end。  
						 如果上面的成立，则再分别遍历各个部分。

24. **二叉树中和为某一值的路径(NoByMyself)**
	1. 从根节点开始寻找，将target作为剩余值，每次都递减，如果进行到叶子节点并且target==0，则给路径是目标路径。然后再分别左右递归子树。  
	   结束条件：如果刚好该节点是叶子节点，并且和为目标值，则打印该条路径。
	   核心：类似于深度优先搜索。
		
25. **复杂链表的复制(AC)**
	1. 核心想法分为三步走：第一步：复制每一个结点，放在就得结点后面，并且暂时不处理随机结点(也就是兄弟结点)   
						   第二步：遍历链表。并且初始化兄弟节点。  
						   第三步：拆分链表。得到新的和旧的链表。
						   
27. **字符串的排列(AC)**
	1. 第一种方法：回溯法。每次寻找时 都从本身开始依次向后回溯(将自身和每一个元素相交换)
	
	
24. **数组出现次数超过一半的数(NoByMyself)**
	1. 如果数字出现的次数超过数组长度的一半，则一定会有相邻的元素，通过

28. **数组出现次数超过一半的数(AC)**
	1. 第一种方法：回溯法。每次寻找时 都从本身开始依次向后回溯(将自身和每一个元素相交换)，每次都将两个不相等的数的值   
		赋值为0，则最后留下为1的数可能是最后所需的数。
	2. 可以直接定义一个计数器times，result = a[0],当值等于result，则加1，否则减1；并且如果times==0，直接令result=a[i],times赋值为1。
		那么最后留下来的肯定是带需要的可能值。

29. **最小的k个数(AC)**
	1. 直接利用两个ArrayList()来存储数据，一个用于存储比较之前的数，一个用于存储比较之后的数据。

30. **连续子数组的最大和(AC)**
	1. 方法一：暴力求解法。内部做两层循环，遍历所有的数对于各个数都分别求出最大子数组的和。    
	2. 方法二：递归调用。
	3. 线性求解法。(推荐) 定义两个变量一个是maxSubString,curSubString。注意区分两种情况即可，curSubString < 0,  curSubString > 0  
	
31. **数字中出现1的次数(AC)**
	1. 将每个数字都作为字符存储到StringBuffer中，然后开始遍历String，统计次数。核心思路还是将int——string。

32. **把数组排成最小的数(AC)**
	1. 思路：将所有的数存储到list中，然后做排序。但是这里面不是按照数排序，而是按照数字排序。也就是将int——String，然后在对数进行排序   
			比如：1234，345   在自定的比较器中 1234 345 < 345 1234。	

33. **丑数(NoByMyself)**
	1. 思路：下一个丑数是由上一个丑数x乘以2、3、5得到的。有其中最小的数得到的。  
		那么我们需要做得是每次将排列中的三个数中的其中一个给提取处理。  
		比如第一个  x = [1] ,则下次在(2,3,5)中挑选,下一个选择了2，则x=[1,2]    
		下一次在(3,5,4,6,10)中挑选最小的即可。   
		依次类推。   

34. **第一个只出现一次的字符的位置(AC)**
	1. 思路：将所有的字符定义为一个数组，将每个字符作为数组的下标值。

35. **数组中的逆序对(NoByMyself)**
	1. 思路：类似于归并排序
	
36. **两个链表中的第一个公共结点(AC)**
	思路：方法1：可以利用两个指针(引用)，从前到后一次遍历两个链表，如果p==null，则指向另外一个的头指针。
		  方法2：可以利用HashMap的特点或者set的特点。(独一无二的特点)

37. **数字在排序数组中出现的次数(AC)**
	1. 思路：方法1：暴力解决。用一个for循环依次遍历。
		  方法2：利用二分查找的思想。

38. **二叉树的深度(AC)**
	1. 思路1：递归。
	2. 思路2：非递归版本，将元素存储到queue中，其实就是类似于层序遍历。

39. **是否是平衡二叉树(Half)**
	1. 思路1：判断每个节点的左右子树的高度，观察是否相差大于1。但是内部用到了两层递归。
	2. 思路2：上面一种做法存在重复遍历节点。在判断上层结点的时候，会多次重复遍历下层结点，增加了不必要的开销。  
	       可以改为自下往上的遍历，如果子树是平衡二叉树则返回子树的高度，不是平衡二叉树则直接返回-1.
		
40. **数组中只出现一次的数字**
	1. 思路1：首先想到的肯定用hashMap来运算。因为hashMap很容易通过key获取value值。
	2. 思路2：使用异或思路。因为异或中，1 ^ 1 = 0   1 ^ 0 = 1   任何一个数字异或它自己都等于0 ,不过真的不会啊。

41. **和为S的连续正数序列(AC)**
	1. 思路：类似于滑动窗口，利用两个指针，两侧根据不同的情况相互移动。

42. **和为S的两个数(AC)**
	1. 思路1：a+b=sum,a和b越远乘积越小，而一头一尾两个指针往内靠近的方法找到的就是乘积最小的情况。   
		   如果是乘积最大的情况就是一直找到两个指针重合。

43. **左旋转字符串(NoByMyself)**
	1. 思路1：利用两个字符串做拼接。每部分取出需要的部分，但是空间复杂度高。而且违背了出题人的初衷
	2. 思路2：对字符串做三次翻转。对于原字符串s=XYZdefabc , n = 3 可以将s分为两部分A=XYZ   B = defabc   
			  如果需要将s旋转，只需要先将A旋转(A.T)，B旋转(B.T)，再将(A.TB.T)旋转

44. **翻转单词序列(AC)**
	1. 思路1：将句子用空格分成String类型的数组，然后合理的利用StringBuilder，因为利用String会产生很多的无用的对象。

45. **扑克牌顺子(AC)**
	1. 思路1：其实就是找规律的题目。如果是顺子需要满足以下条件：
		1. 除了零之外，没有重复的数。
		2. 统计除零之外的数间的间隔。
		3. 判断间隔数和零数之间的大小关系。
	2. 思路2：满足两个条件：(1) max-min < 5  (2) 除零之外，没有重复的数

46. **孩子们的游戏(AC)**
	1. 思路1：直接用数组模拟环。需要用好两个节点 i step.
	2. 利用java中可以移除结点的ArrayList.

47. **1+2+3...+n(NoByMyself)**
	1. 思路1：利用逻辑&&来递归

48. **实现加法**
	1. 思路1：利用BigInteger  
	2. 思路2：利用位运算。

49. **字符串转化为整数**
	1. 分门别类的处理字符串的情况即可。

50. **数组中重复的数字(AC)**
	1. 利用一个数组，将numbers[i]中的数作为新数组的下标值。

51. **构造乘机数组(NoByMyself)**
	1. [思路](https://www.nowcoder.com/questionTerminal/94a4d381a68b47b7a8bed86f2975db46)

52. **正则表达式(NotAC)**
	1. 思路：区分模式串中的*的作用。

53. **表示数值的字符串(NoByMyself)**
	1. 思路：利用正则表达式来匹配。
	2. 思路：相当于模拟整个判断数据的过程，类似于将上面的正则表达式处理的内容，用计算机的语言处理一遍。

54. **字符流中第一个不重复的字符(HalfByMyself)**
	1. 思路：其实解决思路类似于50题，将每个字符的值作为下标值。
	2. 思路2：对于这种一一对应的关系可以采用HashMap,当然最后查找遍历，必须使用list来处理。

55. **链表中环的入口结点(AC)**
	1. 思路：
		1. 第一步：找链表中的环中相汇的点。分别用p1，p2指向链表头部，p1每次走一步，p2每次走二步，直到p1==p2找到在环中的相汇点。   
		2. 第二步：找环的入口。接上步，当p1==p2时，p2所经过节点数为2x,p1所经过节点数为x,设环中有n个节点,p2比p1多走一圈有2x=n+x; n=x;    
				   可以看出p1实际走了一个环的步数，再让p2指向链表头部，p1位置不变，p1,p2每次走一步直到p1==p2; 此时p1指向环的入口。
	
56. **删除链表中的重复结点(AC)**
	1. 思路：建立一个新的头结点。
	
57. **二叉树的下一个结点(AC)**
	1. 思路：分门别类的讨论，判断是否有右子树，再在里面判断该节点是否是父结点的左子树。
	
58. **对称二叉树(AC)**
	1. 思路：可以通过先序遍历的变形方式，DLR和DRL方式，如果两种遍历的结果相等，则为对称二叉树。
			首先根节点以及其左右子树，左子树的左子树和右子树的右子树相同。左子树的右子树和右子树的左子树相同即可，采用递归。
	2. 思路2：利用非递归的方式。类似于先序遍历，DLR及DRL两种遍历方式，如果两者遍历的结果相等，则为对称二叉树。
	
59. **按照之字形打印二叉树(AC)**
	1. 思路：可以定义两个Stack分别存储从左往右遍历的结点及从右往左遍历的结点。可以通过一个计数器来判断层数。
	
	
60. **把二叉树打印成为多行(AC)**
	1. 思路：其实就是一个二叉树的层序遍历问题，只不过，需要将每一行的结点值按照层的方式添加到list中。
	
61. **序列化二叉树(AC)**
	1. 思路：所谓序列化指的是遍历二叉树为字符串;所谓反序列化指的是依据字符串重新构造成二叉树。
	
62. **二叉搜索树的第k个结点(AC)**
	1. 思路：二叉搜索树的各个结点顺序就是中序遍历的顺序。现在我们只需要利用递归的方式或者非递归的方式实现二叉树的中序遍历即可。
		1. 递归方式
		2. 非递归方式
		
	
63. **获取当前读取数据流的中位数(NoAC)**
	1. 思路：为了保证插入新数据和取中位数的时间效率都高效，这里使用大顶堆+小顶堆的容器，并且满足：
 		1、两个堆中的数据数目差不能超过1，这样可以使中位数只会出现在两个堆的交接处；
		2、大顶堆的所有数据都小于小顶堆，这样就满足了排序要求。
		
	
64. **滑动窗口的最大值(NoAC)**
	1. 思路：滑动窗口应当是队列，但为了得到滑动窗口的最大值，队列序可以从两端删除元素，因此使用双端队列。
		
65. **矩阵中的路径(AC)**
	1. 思路：回溯，递归思想。
		
65. **机器人的运动范围(AC)**
	1. 思路：回溯，递归思想。
		
