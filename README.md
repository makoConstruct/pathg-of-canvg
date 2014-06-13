##pathg

Sometimes you want to render a path you've specified in the svg format to a canvas, but you don't need or want the full functionality of an svg renderer, just the ability to draw a single shape.

pathg is a standalone distribution of the path drawing code of [canvg](https://code.google.com/p/canvg/), a svg to canvas render.

Why bother with pathg when you can just use canvg? Pathg is about a tenth of the size, and gets straight to the point. Drawing paths. That's what matters. Why would you want to do anything more than drawing paths? Pathg has it right.

	//usage example:
	var canv = document.createElement('canvas');

	var path = new CanvablePath('M 82.679734,0 C 36.88892,0 0,36.88892 0,82.67973 c 0,45.79082 36.88892,83.19648 82.679734,83.19648 45.790816,0 83.196486,-37.40566 83.196486,-83.19648 C 165.87622,36.88892 128.47055,0 82.679734,0 z m 0,9.3014696 c 40.594696,0 73.895016,32.7835694 73.895016,73.3782604 0,24.19762 -11.81543,45.55139 -29.97141,58.90932 5.80848,-14.41118 9.8804,-46.430166 5.16748,-76.995513 0.82286,-1.151279 1.32175,-2.627288 1.55026,-4.133986 0.90914,-5.993589 -2.79114,-10.976144 -8.78474,-11.885209 -5.99359,-0.909065 -11.49289,2.791128 -12.40195,8.78472 -0.26409,1.74138 0.009,3.08171 0.51675,4.650736 l 13.43545,2.066994 -1.03348,0.516754 c 6.69143,32.501226 0.0314,70.142614 -8.78472,83.196484 -10.15309,5.21345 -21.42685,8.26797 -33.588644,8.26797 -40.594692,0 -73.378264,-32.78357 -73.378264,-73.378263 0,-40.59469 32.783572,-73.3782599 73.378264,-73.3782599 z M 31.004901,40.823116 c -6.062144,0 -10.851715,5.30632 -10.851715,11.368463 0,1.114353 0.208028,2.087094 0.516754,3.10049 l 20.669932,0 c 0.332877,-1.048726 1.033495,-1.941551 1.033495,-3.10049 0,-6.062143 -5.306319,-11.368463 -11.368465,-11.368463 z m 35.138887,8.784721 c -9.544962,-0.455268 -17.630925,6.474244 -18.086194,16.0192 l -2.06699,44.957103 c -0.455237,9.54496 6.474234,17.63092 16.019197,18.08619 l 22.736926,1.03349 c 9.544962,0.45528 17.630923,-6.99098 18.086193,-16.53594 l 2.06699,-44.440356 C 105.35518,59.18257 98.425676,51.096604 88.880714,50.641335 L 66.143788,49.607837 z m 23.770425,61.493053 c 4.80d1062,-0.16009 8.78472,0 8.78472,0 -0.464667,6.50458 -5.544687,13.38414 -11.885212,13.43545 l -26.354165,0 c 2.323051,-5.57535 8.706126,-9.57197 16.535946,-11.88521 2.726894,-0.80563 8.117648,-1.39016 12.918711,-1.55024 z');

	var bounds = path.bounds(); //:DDD
	canv.width = Math.ceil(bounds.x2 - bounds.x1);
	canv.height = Math.ceil(bounds.y2 - bounds.y1);

	var con = canv.getContext('2d');
	con.fillStyle = 'rgb(0,0,0)';
	con.translate(bounds.x1, bounds.y1); //not necessary in this case, but this will ensure that your graphic ends up at 0,0 even if your svg editor has a penchant for weird absolute positioning.
	path.draw(con);
	con.fill();

	document.body.appendChild(canv);

##view it live

http://makopool.com/pathgExample.html

#Licence

[MIT](http://opensource.org/licenses/mit-license.php)