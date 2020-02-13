```markdown
2/12 record
improve: 
字串處理要熟
priority : 資料結構(Linked list, binary tree, map, set) => regexp
白板先想思路
介紹重點簡短
```

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

```markdown
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
```

```markdown
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
```

```markdown
Q4: Virtual DOM
A4: 以 JavaScript 物件模擬DOM結構產生的樹狀結構 不直接操作DOM
    待一段落後再將變更更新回真實DOM
```
```markdown
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
```

```markdown
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
```

```markdown
Q7: status code !!!記所有status code
HTTP 204 No Content 成功狀態碼表明請求成功，但客戶端不需要更新目前的頁面。204 回應預設是可被快取的，此類回應中會包含 ETag 標頭。
回傳 204 的常見情況是作為 PUT 請求的回應，更新一個資源且沒有更動目前顯示給使用者的頁面內容。若是有資源被建立，201 Created 則應該被回傳。而若頁面應該更新為新的頁面，則應使用 200 。


A7:
   1XX(資訊回應)
   2XX(成功回應)
   - 200 =>
   - 201 Created => 
   - 204 No Content => 成功請求但不需更新，reponse可快取，包含ETag，常常發生在PUT請求，更新資料但用戶端沒有要呈現
   3XX(重定向)
   - 301 Moved Permanently：已永久移動到新位置。
   - 302 Found（Moved Temporarily）：暫時移到新位置。
   - 304 Not Modified：東西跟之前長一樣，可以從快取拿就好。
   4XX(用戶端錯誤)
   - 400 Bad Request：明顯的用戶端錯誤，伺服器無法處理這個 Request。e.g. fetch error url
   - 401 Unauthorized：未認證，可能需要登入或 Token。
   - 403 Forbidden：沒有訪問權限。
   - 404 Not Found：找不到資源。
   5XX(伺服器端錯誤)
   - 500 Internal Server Error：伺服器端錯誤。
   - 502 Bad Gateway：通常是伺服器的某個服務沒有正確執行。
   - 503 Service Unavailable：伺服器臨時維護或是快掛了，暫時無法處理請求。
   - 504 Gateway Timeout：伺服器上的服務沒有回應。
```
```markdown
Q8: async sync diff
A8: async no block thread, save to task queue, instead of sync
    sync block thread, one line exec. 
```


