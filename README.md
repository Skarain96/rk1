<!DOCTYPE html>
<html lang="ru">
<head>
	<meta charset="UTF-8">
	<title>РК-1</title>
	
</head>
<body>
	<h1>Рубежный контроль №1</h1>
	<h2>
		Задание 1. С помощью алгоритма Брезенхема построить отрезок прямой с координатами: A(100, 0) и B(i+10, 100), где i - номер по журналу
	</h2>
	<canvas id="canvas1" height="400" width="400"></canvas>
	<script>
		var canva = document.getElementById("canvas1");
		var canv = canva.getContext("2d");

		var x1=100;
		var y1=0;
		var variant=8;
		var x2=10+variant;
		var y2=100;
		
		var dx = (x2 - x1 >= 0 ? 1 : -1);
		var dy = (y2 - y1 >= 0 ? 1 : -1);
		var lengthX = Math.abs(x2 - x1);
		var lengthY = Math.abs(y2 - y1);
		var length = Math.max(lengthX, lengthY);
		if (length == 0) {
			canv.fillRect(x1, y1, 1, 1);
		}

		if (lengthY <= lengthX) {
			// Начальные значения
			var x = x1;
			var y = y1;
			var d = -lengthX;
			// Основной цикл
			length++;
			while (length--) {
				canv.fillRect(x, y, 1, 1);
				x += dx;
				d += 2 * lengthY;
				if (d > 0) {
					d -= 2 * lengthX;
					y += dy;
				}
			}
		} else {
			// Начальные значения
			var x = x1;
			var y = y1;
			var d = -lengthY;
			// Основной цикл
			length++;
			while (length--) {
				canv.fillRect(x, y, 1, 1);
				y += dy;
				d += 2 * lengthX;
				if (d > 0) {
					d -= 2 * lengthY;
					x += dx;
				}
			}
		}

	</script>
	<h2>
		Задание 2. Задан массив в переменной array. Необходимо построить отрезки прямых.
	</h2>
	<canvas id="canvas2" height="400" width="400"></canvas>
	<script>
		var canva = document.getElementById("canvas2");
		var canv = canva.getContext("2d");

		var array=[	[2,20,40,55],
			        [2,19,41,55],
					[2,15,20,25,45,55],
					[2,13,20,25,45,55],
					[2,13,20,25,46,55],
					[2,13,20,25,47,55],
					[2,13,20,25,48,55],	];
		var nn=0;
for (var row=0; row<array.length; row++) {
		nn=0;
		for (var i=0; i<array[row].length-1; i++){
			if (array[row][i+1]-array[row][i]>1) {
				if ((nn % 2)==0) {
					for (var j=array[row][i]; j<=array[row][i+1]; j++) {
						canv.fillRect(j, 10+row, 1, 1);
					}
				}
				nn++;
			}
		}
	}
	</script>
</body>
</html>
