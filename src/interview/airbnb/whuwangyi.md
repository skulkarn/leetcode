Airbnb的题目往往都很啰嗦，其实简单几句话就可以概括的。要求代码写完了能够编译，然后自己写测试用例并跑过。感觉这样的好处是的确很考察代码功力，那种当场一次bug free，然后跑几个测试用例全过的感觉很爽。不好的地方是容易增加变数，因为即使自己本身水平不变，不同时候发挥略有差异，检查一两个bug用的时间可能就没机会做后面的follow up了。


第一轮实现分页显示。给了以下一些输入数据，要求将以下行分页显示，每页12行，其中每行已经按score排好序，分页显示的时候如果有相同host id的行，则将后面同host id的行移到下一页。

[

"host_id,listing_id,score,city",

"1,28,300.1,SanFrancisco",

"4,5,209.1,SanFrancisco",

"20,7,208.1,SanFrancisco",

"23,8,207.1,SanFrancisco",

"16,10,206.1,Oakland",

"1,16,205.1,SanFrancisco",

"6,29,204.1,SanFrancisco",

"7,20,203.1,SanFrancisco",

"8,21,202.1,SanFrancisco",

"2,18,201.1,SanFrancisco",

"2,30,200.1,SanFrancisco",

"15,27,109.1,Oakland",

"10,13,108.1,Oakland",

"11,26,107.1,Oakland",

"12,9,106.1,Oakland",

"13,1,105.1,Oakland",

"22,17,104.1,Oakland",

"1,2,103.1,Oakland",

"28,24,102.1,Oakland",

"18,14,11.1,SanJose",

"6,25,10.1,Oakland",

"19,15,9.1,SanJose",

"3,19,8.1,SanJose",

"3,11,7.1,Oakland",

"27,12,6.1,Oakland",

"1,3,5.1,Oakland",

"25,4,4.1,SanJose",

"5,6,3.1,SanJose",

"29,22,2.1,SanJose",

"30,23,1.1,SanJose"

]


这题的思路不难，但是实现起来还是有点难度的。在遍历的时候需要维护一个LinkedHashMap作为page并且完成去重。用LinkedHashMap的好处是可以保证所有的entry是按插入的顺序排序的，所以仍然可以保证按score排序的性质。另外，一旦遇到相同的host_id，则将其对应的行存到另一个buffer里。由于需要变遍历边增减容器里的数据，需要用ListIterator，并调用remove和add方法。之前只用过remove，从来没用过add。


第二轮是他家一道高频题，给一堆租房的request，作为输入数组，找一个array subset，其中任意两个元素不能相邻，（因为要打扫房间），求使得子集里所有元素之和最大。一维DP解之，另外可以使用滚动数组让空间开销为常数。


第三轮是实现一个CSV格式的Parser。其中处理转义字符比较tricky，当时只给了三个最基本的test case，所以都过了，但是由于花了些时间debug，有些特殊情况一开始处理错了，后来没时间进行处理了。这一轮面得很郁闷，面试官没怎么理我，感觉在做自己的事情，没什么交流。测试的时候把不小心把输入内容给贴错了，花了不少时间检查。

