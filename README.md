```markdown
var s = 'hello <hello> String here </hello> hehe <hello> Strineeeeg here </hello> hoho'
var from = 'hello'
var to = 'span'

// output list = [‘hello’, ‘<span> String here </span>’, ‘hehe’]

function replaceTag(s, from, to) {
	// console.log(s.split(/(<hello>.*?<\/hello>)/))
	// return s.split(/(<hello>.*?<\/hello>)/).map(word => word.replace(/<\/?hello>/g, '</' + to + '>'))
	return s.split(/(<hello>.*?<\/hello>)/).map(word => word.replace(/(<\/?)hello(>)/g, '$1' + to + '$2'))
}

replaceTag(s, from, to)
```


linklist

solution: (1)hashmap (2)2 pointer
https://yohey66.wordpress.com/2018/08/28/leetcode-141-linked-list-cycle/

head -> 1 -> 2 -> 3 -> 4 -> null
node = {
	val: x,
	next: node
}

head -> 1 -> 2 -> 3 -> 1 -> 2 ->
head -> 1 -> 2 -> 3 -> 4 -> null => False
head -> 1 -> 2 …. => True

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


data structure

https://medium.com/change-or-die/%E6%BC%94%E7%AE%97%E6%B3%95%E5%9C%96%E9%91%91-%E7%AC%AC%E4%B8%80%E7%AB%A0-%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B-10d5a6337be5
https://www.slideshare.net/ccckmit/ss-56891871
https://www.youtube.com/watch?v=3503j2L6qNA
https://www.youtube.com/watch?v=bum_19loj9A
