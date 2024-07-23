# STL库用法

[toc]

## vector

动态数组，类似于arraylist。

```c++
vector<int> v1;//默认构造
vector<int> v2(v1.begin()+1,v1.begin()+4);//带参数的构造

//插入
push_back();
insert();

//数据存取
v1.at();v1[];v1.front();

//删除
pop_back();
clear();
erase();

//迭代器
begin();
end();
rbegin();//反向开始
rend();

//大小
size();
empty();
capacity();
resize();
shrink_to_fit();

//赋值
assign(const_iterator first,const_iterator last);//将当前容器中的first-last赋值到当前容器，之前														的元素会被清除
assign(size_type n,const T& x = T())//赋n个值为x的元素到容器中
operator=
swap();

```

## list

- 本质上是一个双向链表
- 不支持随机存储元素

```c++
list<int> l1;//默认构造
list<int> l2(l1.begin(),l1.end());

l2.push_back();
l2.push_from();
l2.pop_back();
l2.pop_front();
l2.emplace_back();//在末尾添加元素，不定参数
l2.emplace_front();
l2.emplace(const_iterator __position, _Args&&... __args);//在指定位置添加元素

l2.clear();
l2.erase(begin,end);
l2.erase(position);
l2.remove(element);
l2.remove_if();
l2.unique();

//迭代器
l2.begin();
l2.end();
l2.rbegin();
l2.rend();

//元素的存取
l2.front();
l2.back();

//赋值
l2.assign();
l2.swap(l1);

//大小
l2.size();
l2.empty();
l2.resize();

//排列
l2.sort();
l2.reverse();

//对容器的操作
l1.splice(position, list2):
//将list2中的所有元素剪贴到list1的position位置；
l1.splice(position, list2, iter):
//将list2中某个位置的迭代器iter指向的元素剪贴到list1中的position位置；
l1.splice(position, list2, iter1, iter2):
//将list2中的某一段位置iter1 ~ iter2的元素剪贴到list1中的position位置
```

## forward_list

对list进行了优化，是一个单向链表，少存储了一个指针：

- 只提供了前向迭代器，不支持反向迭代器
- 不提供size成员函数
- 没有指向最末元素的锚点，所以不提供back、push_back、pop_back
- 不提供随机访问
- 插入和删除元素不会造成“指向其他元素的”指针、引用、迭代器失效

## deque

- 双端数组，vector是单向的
- 可以随机存取元素

## set、multiset

- set保证元素唯一；不能保证最后的顺序是插入顺序
- 底层是红黑树，本质是平衡二叉树，插入和删除上比vector快；时间复杂度O(log n):
- 不可以直接存取元素
- multiset和set的区别：set支持唯一键值，而multiset中的元素可以出现多次
- 不可以直接修改set或者multiset中的元素值，因为这类容器是自动排序的，如果要修改其中的某个元素值，必须要首先删除原有值，然后重新添加新的元素

## map、multimap

- map是标准的关联容器，键值对中的第一个元素是first、第二是second，支持迭代器访问输出
- key唯一；不能保证插入顺序与实际顺序相同
- 采用的是红黑树的变体
- 支持直接存取key所对应的value，支持[]，如map[key]=value
- multimap与map的区别：map支持唯一键值，每个键只出现一次；multimap相同的箭可以出现多次，但是multimap不支持[]

##  priority_queue

```c++
priority_queue< type, container, function > queue：
//container:实现优先队列的底层容器,必须是数组类型的容器
//fuction:元素之间的比较方式
//后两个参数可以不写，默认是大顶堆
priority_queue< int, vector<int> ,greater<int> > queue2;
```



