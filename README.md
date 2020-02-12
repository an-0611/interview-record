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
