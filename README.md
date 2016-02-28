# vim-ecmascript6

This repo provides some *simple* modifications to the default vim javascript syntax file so that it can recognize ecmascript 6 (javascript 2015/harmony) syntax. The modifications are intentionally left minimal to highlight the most critical changes to js. For a more robust es6 syntax highlighter, see [isRuslan/vim-es6][vim-es6].

### Installation
 
Just copy the `javascript.vim` file to your default vim syntax directory (ie. `/usr/share/vim/vim74/syntax/`), no need to create a bundle or use vundle.

If you need to revert back to the original, you can grab it from [here][vim-js]. If you update vim, you will need to re-copy the syntax file. You can use the `copy.sh` script for brevity.

### git diff **javascript.vim**

 
Supports [template][mdn-templates] string literals:
 
```diff
 syn region  javaScriptStringD	       start=+"+  skip=+\\\\\|\\"+  end=+"\|$+	contains=javaScriptSpecial,@htmlPreproc
 syn region  javaScriptStringS	       start=+'+  skip=+\\\\\|\\'+  end=+'\|$+	contains=javaScriptSpecial,@htmlPreproc
+syn region  javaScriptStringT	       start=+`+  skip=+\\\\\|\\`+  end=+`\|$+	contains=javaScriptSpecial,@htmlPreproc
```
```diff
   HiLink javaScriptStringS		String
   HiLink javaScriptStringD		String
+  HiLink javaScriptStringT		String

```

Supports [for..of][mdn-forof] loops:

```diff
-syn keyword javaScriptRepeat		while for do in
+syn keyword javaScriptRepeat		while for do in of
```

Supports [void][mdn-void] and [yield][mdn-yield] operators:

```diff
-syn keyword javaScriptOperator		new delete instanceof typeof
+syn keyword javaScriptOperator		new delete instanceof typeof void yield
```

Supports the [const][mdn-const] identifier:

```diff
-syn keyword javaScriptIdentifier	arguments this var let
+syn keyword javaScriptIdentifier	arguments this var let const
```

```diff
-syn keyword javaScriptReserved		abstract boolean byte char class const debugger double enum export extends final float goto implements import int interface long native package private protected public short static super synchronized throws transient volatile 
+syn keyword javaScriptReserved		abstract boolean byte char class debugger double enum export extends final float goto implements import int interface long native package private protected public short static super synchronized throws transient volatile
```


### Resources

- [javascript.vim][vim-js] - default javascript.vim file from the official vim repository
- [Ecmascript 6 specification][es6spec] - released June 2015
- [vim-es6][vim-es6] - vim ES6 syntax highlighting written from scratch


[vim-js]: https://github.com/vim/vim/blob/master/runtime/syntax/javascript.vim
[es6spec]: http://www.ecma-international.org/ecma-262/6.0/index.html
[vim-es6]: https://github.com/isRuslan/vim-es6

[mdn-templates]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/template_strings
[mdn-forof]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of
[mdn-void]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/void
[mdn-yield]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield
[mdn-const]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const
