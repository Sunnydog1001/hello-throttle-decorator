<html>
<head>
<meta charset='utf-8'>
</head>
<body>
<script>
function throttle(f, ms) {
	var prevthis;
	var prevargs;
	var isThrottled = false;
	return function wrapper () {
		if (isThrottled) {
			prevthis = this;
			prevargs = arguments;
			return;
		}
		f.apply (this, arguments);
		isThrottled = true;
		setTimeout (function timer () {
			isThrottled = false;
			if (prevargs) {
				wrapper.apply(prevthis, prevargs);
				prevargs = prevthis = null;
				};
			}, ms);
	};
}
</script> 
</body>
</html>
