---
tags:
  - Html
  - Tips
---

###### Datalist + option tag
```HTML
<body>
	<input list="browsers"/>
	<datalist id="browsers">
		<option value="Edge"></option>
		<option value="Firefox"></option>
		<option value="Chrome"></option>
		<option value="Opera"></option>
		<option value="Safari"></option>
	</datalist>
</body>
```

<input list="browsers"/>
<datalist id="browsers">
<option value="Edge"></option>
<option value="Firefox"></option>
<option value="Chrome"></option>
<option value="Opera"></option>
<option value="Safari"></option>
</datalist>

- **list** của *input* khi truyền vào id của *datalist* thì *input* có thể tạo ra drowbox
![[image-2 6.png]]


###### abbr
```HTML
<body>
	<p>
		<abbr title="lỏem">Lorem</abbr> ipsum dolor, sit amet consectetur adipisicing elit. Possimus odit earum assumenda et non nam voluptas quo ex necessitatibus illum reiciendis neque, ipsam ut cum laboriosam praesentium aspernatur molestiae delectus!
	</p>
</body>
```

<p><abbr title="lỏem">Lorem</abbr> ipsum dolor, sit amet consectetur adipisicing elit. Possimus odit earum assumenda et non nam voluptas quo ex necessitatibus illum reiciendis neque, ipsam ut cum laboriosam praesentium aspernatur molestiae delectus!</p>

- **abbr** tag có thể thêm sub cho text.
![[image-3 4.png]]



###### details tag
```html 
<body>
	<details>
		<summary>More</summary>
		<p>this is the end</p>
	</details>
</body>
```

<details><summary>More</summary><p>this is the end</p></details>

![[image-4 4.png]]
![[image-5 4.png]]



###### pre tag
```html 
<body>
	<pre>
		code here
	</pre>
</body>
```
<pre>code here</pre>

###### mark tag
```html 
<body>
	Lorem ipsum <mark>dolor</mark>, sit amet consectetur adipisicing elit. Sint deserunt aliquam quo tempore placeat sit debitis obcaecati rem repellat reprehenderit illum aperiam doloremque nam inventore, vitae ut facilis vero molestiae.
</body>
```
Lorem ipsum <mark>dolor</mark>, sit amet consectetur adipisicing elit. Sint deserunt aliquam quo tempore placeat sit debitis obcaecati rem repellat reprehenderit illum aperiam doloremque nam inventore, vitae ut facilis vero molestiae.



###### meter
```HTML
<body>
	<meter value="37" min="0" max="100"></meter>
</body>
```
<meter value="37" min="0" max="100"></meter>



###### progress
```HTML
<body>
	<progress value="43" max="100"></progress>
</body>
```
<progress value="43" max="100"></progress>


