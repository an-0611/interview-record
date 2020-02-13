```markdown
Q1: 
var s = 'hello <hello> String here </hello> hehe <hello> Strineeeeg here </hello> hoho'
var from = 'hello'
var to = 'span'
var output list = [‘hello’, ‘<span> String here </span>’, ‘hehe’]

A:
function replaceTag(s, from, to) {
	return s.split(/(<hello>.*?<\/hello>)/).map(word => word.replace(/(<\/?)hello(>)/g, '$1' + to + '$2'))
}

replaceTag(s, from, to)
```

Q2:
linklist
solution: (1)hashmap (2)2 pointer
head -> 1 -> 2 -> 3 -> 4 -> null
node = {
	val: x,
	next: node
}
head -> 1 -> 2 -> 3 -> 1 -> 2 ->
head -> 1 -> 2 -> 3 -> 4 -> null => False
head -> 1 -> 2 …. => True

A2-hashmap:
function hasCycle(head) {
	var hash = {};
	var cur = head;
	if (head == null) return false;
	while (cur.next != null) {
		if (hash[head.val] === ‘undefined’ ) hash[head.val] = 0;
		else return true;
		cur = cur.next;
	}
	return false;
}

A2-2pointer:
function hasCycle(head) {
    let r = head;
    let t = head; // 記錄第一個元素
    while (r != null && r.next != null && r.next.next !=null) { // compare
       r = r.next.next; // 迴圈一直往後找下一個node是否有相同元素
       t = t.next;
       if (t == r) return true;
    }
    return false;
};

Q3:
what's different below promise
A3: // 永遠要回傳結果，否則 Callback 不會獲得前一個 Promise 的結果。
doSomething().then(function() { // 會等做完
  return doSomethingElse(); 
})

doSomething().then(function () {
  doSomethingElse();
});

doSomething().then(doSomethingElse());

doSomething().then(doSomethingElse);// 會等做完 dosomethindElse = successcallback

／／拿到結果有無回傳


Q4: Virtual DOM
A4: 以 JavaScript 物件模擬DOM結構產生的樹狀結構 不直接操作DOM
    待一段落後再將變更更新回真實DOM
    React: shouldComponentUpdate
    Vue: watch

Q5: React Vue 優缺
A5: 
React: 
	JSX開發
	學習曲線較高
	依賴生態系
	表單驗證困難
	deepEqual 較困難
	建立大型項目SPA  如需要UI庫 比較適合
	可開發多平台 react native
	為了減少渲染 出了shouldComponentUpdate 優化比較複雜
Vue: 
	模板開發
	學習曲線較低
	較不依賴生態系 方便與各種library兼容
	表單的驗證簡單
	內部已經進行deepEqual優化
	建立小型項目
	默認就是優化狀態減少渲染
	
Q6: 隱藏元素方法
A6: 
   opacity: 0;
	
   width: 0;
   height: 0;
   font-size: 0;
   overflow: hidden;
   
   visibility: hidden

   transform: scale(0, 0);
   transform: scaleY(0);

   display: none
   z-index: -1
   
   position: absolute; || fix
   top: -9999px;
   left: -9999px;

e.g. :



Q7: status code
A7:
   1XX
   2XX
   3XX
   4XX
   5XX
