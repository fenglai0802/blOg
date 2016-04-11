#### 两类空格引起的bug

* The non-breaking space (U+00A0 Unicode, 160 decimal, &nbsp;) is not the same as the space character (U+0020 Unicode, 32 decimal). Well, both of them seems to be a "space", but they are absolutely different characters.
* unicode码为160的的插入空格和unicode码为32的常规的空格是不同的。
* 将数据存放在dom上，有可能经过了转义处理，从而导致空格类型的改变，这就会造成一些bug，比如**搜索**时两类空格无法匹配。可以使用正则替换。

		var s = ' ' // 假设这里是一个160的空格。
		var reg = new RegExp(String.fromCharCode(160),"gm");
		var 32sp = String.fromCharCode(32)
		s = s.replace(reg, 32sp);