---
title: '[Immersive_Sprint.js] Tree, Graph, Hash Table, Binary Tree'
description: Code States의 Immersive Sprint를 수강하고 있다.
date: '2017-12-24T09:29:15.520Z'
category: 'basic'
keywords: []
draft: false
slug: /@lyhlg0201/immersive-sprint-js-tree-graph-hash-table-binary-tree-a7a122424974
---

[Code States](http://www.codestates.com)의 Immersive Sprint를 수강하고 있다.

1주차에 진행한 내용은 **자료 구조** 이다

1.  Stack & Queue
2.  Linked List
3.  Tree
4.  Graph
5.  Hash Table
6.  Binary Tree

위처럼 목차대로 1주차를 진행하였다.

Graph부터 Binary Tree까지 정리하려고 봤더니,, 배웠던 부분도 적지 않은 부분이지만 실제로 기본이 되는 내용만 배운지라 새로 또 공부해서 포스팅을 하려니 부담이 된다..

그래서 나머지는 어느정도 묶어서 포스팅을 해야겠다.

먼저…

### Tree

트리구조는 Graph의 일종이다.

트리의 종류에도 여러 종류가 있지만, 여기서는 단순히 Tree에 대해서만 이야기하고 아래에서 Binary Tree에 대해서도 간단히 설명하고 구현한다.

Tree는 자신의 값 (value)와 자식노드(children) 의 값을 가진다.

그리고 child 추가, searching에 대한 메소드를 갖는다. (단순하다.ㅎㅎ 삭제가 있었다면.. 정말 어려웠을거 같다. 나중엔 구현해봐야지)

`newTree` (type : object)

- Tree 생성자를 통해 새로운 객체를 만들었을 경우 node의 값 및 각종 필요한 메소드들을 담고 있다.

`newTree.value` (type : number)

- 노드 생성시 노드의 값을 저장한다.

`newTree.children` (type : array)

- 자식 노드의 연결 관계를 명시한다.
- 여기서는 input된 순서대로 배열에 담았다.

`newTree.addChildren`

- 노드를 추가하기 위한 메소드

`newTree.contains`

- 특정한 value 값을 가진 node가 현재 tree에 있는지 확인하기 위한 메소드
- 트리구조에서 특정 값을 얻어오기위해서는 마지막 childNode가 null 일때까지 돌린 후 재귀로 다시 부모 node 혹은 root로 돌아와야 한다.
- 그래서재귀를 돌렸다

내용이 너무 단순해서.. (물론 코드를 찾아 나가는데에는 오래걸렸지만 ㅠㅠ) 바로 코드를 추가한다.

var Tree = function(value) {  
 var newTree={};  
 newTree.value = value;  
 newTree.children = \[\];  
 \_.extend ( newTree, treeMethods);  
 return newTree;  
};

var treeMethods = {};

treeMethods.addChild = function(value) {  
 var tree = Tree(value);  
 this.children.push(tree);  
 return tree;  
};

treeMethods.contains = function(target) {  
 var flag = false;  
 function recurForTarget (current){  
 for (var i = 0; i < current.length; i++) {  
 if ( current\[i\].children.length !==0 ){  
 recurForTarget ( current\[i\].children );  
 }  
 else {  
 if ( current\[i\].value === target ){  
 flag = true;  
 }  
 }  
 }  
 return flag;  
 }  
 return recurForTarget(this.children);  
};

### Graph

자료 구조에서 그래프는 방향을 가진 그래프 ( directed graph ) 와 무방향 그래프 ( undirected graph )로 나뉜다.

내가 구현한 그래프는 방향이 없는 그래프이다. 나는 엄청나게 단순하게 구현했는데.. 더 좋은 방법들은 충분히 많을 것 같다.

아래와 같은 변수와 메소드를 통해 구현을 하였다.

`node` (type : object)

- node의 값들을 저장하기 위한 변수 ( 배열로 해도되나 ? 왜 객체로 했는지는 까먹었다. )
- 새로 1이라는 값을 가진 노드를 추가하게 되면 아래와 같이 추가가되게된다.
- node = {1: ‘1’};

`edge` (type : object)

- node들간 연결을 표현하기 위한 변수
- 1이라는 value를 가진 노드와 3이라는 value를 가진 노드가 연결되게 되면 아래와 같이 표현된다.
- edge = {1 : ‘3’};
- undirected graph의 형태이기 때문에 1이 key가 되어도 3이 key가 되어도 상관없다.

`addNode`

- 노드를 추가하기 위한 메소드
- 단순히 node object에 추가된다.

`contains`

- 특정 value 값이 node에 포함되어있는지 확인하기 위한 메소드
- node 변수의 값중 찾고자하는 value값이 포함되어 있으면 true return

`removeNode`

- 특정 value 값을 node에서 삭제하기 위한 메소드
- 삭제된 node를 return 한다.

`hasEdge`

- 특정 값을 가진 두개의 node가 연결 되어 있는지 확인하는 메소드

`addEdge`

- 특정 값 두개를 연결 하는 메소드

`removeEdge`

- 특정 노드간 연결되어 있는 edge를 삭제 하는 메소드

`forEachNode`

- 특정 노드의 값을 지정하였을 때 현재 그래프에 있는 모든 노드와 연결 시키기 위한 메소드

소스코드를 바로 보자

// Instantiate a new graph  
var Graph = function() {  
 this.node = {};  
 this.edge = {};  
};

// Add a node to the graph, passing in the node's value.  
Graph.prototype.addNode = function(node) {  
 this.node\[node\] = node;  
};

// Return a boolean value indicating if the value passed to contains is represented in the graph.  
Graph.prototype.contains = function(node) {  
 for ( var key in this.node){  
 if ( this.node\[key\] === node ) return true;  
 }  
 return false;  
};

// Removes a node from the graph.  
Graph.prototype.removeNode = function(node) {  
 for ( var key in this.edge ) {  
 if ( key == node.toString() ) {  
 this.removeEdge(node, this.edge\[key\]);  
 }  
 else if ( this.edge\[key\] === node ){  
 this.removeEdge(key, node);  
 }  
 }  
 delete this.node\[node\];  
};

// Returns a boolean indicating whether two specified nodes are connected. Pass in the values contained in each of the two nodes.  
Graph.prototype.hasEdge = function(fromNode, toNode) {  
 for ( var key in this.edge ) {  
 if ( (key == fromNode.toString()) && (this.edge\[key\] === toNode) || (key === toNode.toString() && this.edge\[key\] === fromNode) ){  
 return true;  
 }  
 }  
 return false;  
};

// Connects two nodes in a graph by adding an edge between them.  
Graph.prototype.addEdge = function(fromNode, toNode) {  
 this.edge\[fromNode\] = toNode;  
};

// Remove an edge between any two specified (by value) nodes.  
Graph.prototype.removeEdge = function(fromNode, toNode) {  
 for ( var key in this.edge ) {  
 if ( (key == fromNode.toString() && this.edge\[key\] === toNode) || (key === toNode.toString() && this.edge\[key\] === fromNode) ){  
 delete this.edge\[key\];  
 }  
 }  
};

// Pass in a callback which will be executed on each node of the graph.  
Graph.prototype.forEachNode = function(cb) {  
 for ( var key in this.node ){  
 cb(key);  
 }

var cb = function(item) {  
 graph.addEdge(item, 5);  
};};

### **Hash Table**

hash는 아직 심화문제를 풀지는 못했다. 작성된 것 까지만 일단 코드 공유

시간 복잡도는 일반적으로 O(1) 이다.

var HashTable = function() {  
 this.\_limit = 8;  
 this.\_storage = LimitedArray(this.\_limit);  
};

HashTable.prototype.insert = function(k, v) {  
 var index = getIndexBelowMaxForKey(k, this.\_limit);  
 var keyValuePair = { \[k\] : v };  
 var obj = this.\_storage.get( index ) || {} ;  
 obj\[k\] = v;  
 this.\_storage.set(index,obj);  
};

HashTable.prototype.retrieve = function(k) {  
 var index = getIndexBelowMaxForKey(k, this.\_limit);  
 return this.\_storage.get(index)\[k\];  
};

HashTable.prototype.remove = function(k) {  
 var index = getIndexBelowMaxForKey(k, this.\_limit);  
 delete this.\_storage.get(index)\[k\];  
};

마지막으로..

### Binary Search Tree

1개 또는 2개의 자식만을 가지는 Tree를 말한다.

최악의 경우 O(n)의 시간 복잡도를 가지지만 balancing 과정을 통해 O(logN)의 복잡도를 가질 수 있다.

var BinarySearchTree = function(value) {  
 var nTree = Object.create(tMethods);  
 nTree.value = value;  
 nTree.left = null;  
 nTree.right = null;  
 return nTree;  
};

var tMethods = {};

tMethods.insert = function (value){  
 var subTree = new BinarySearchTree(value);

function RecuForInsert ( currentNode ) {  
 if ( subTree.value <= currentNode.value ){  
 if ( currentNode.left ) {  
 RecuForInsert(currentNode.left);  
 }  
 else {  
 currentNode.left = subTree;  
 }  
 }  
 else {  
 if ( currentNode.right ) {  
 RecuForInsert(currentNode.right);  
 }  
 else {  
 currentNode.right = subTree;  
 }  
 }  
 }  
 return RecuForInsert ( this );  
}

tMethods.contains = function ( value ) {  
 var flag = false;  
 function RecuForContains(currentNode) {  
 if ( value === currentNode.value ){  
 flag = true;  
 }  
 else if ( value <= currentNode.value && !flag) {  
 if ( currentNode.left ) {  
 RecuForContains(currentNode.left);  
 }  
 }  
 else if ( value > currentNode.value && !flag) {  
 if ( currentNode.right ) {  
 RecuForContains(currentNode.right);  
 }

}  
 return flag;  
 }  
 return RecuForContains ( this );  
}  
tMethods.depthFirstLog = function ( fn ) { // function

function RecuForPush (current){  
 if ( current.value ){  
 fn(current.value);  
 if ( current.left ){  
 RecuForPush(current.left);  
 }  
 else if ( current.right ){  
 RecuForPush(current.right);  
 }  
 }

};  
 return RecuForPush(this);  
}
