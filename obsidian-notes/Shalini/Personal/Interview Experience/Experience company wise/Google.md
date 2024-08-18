
ROUND 1 : DSA
- Given stream of coordinates (x, y) in a 2d plane, we need to tell if with the latest coordinate can we make square or not.
- EG - (2, 1) (2, 4) (5, 1) (5, 6) (till here we cannot make square)  (5, 4) (now we can make square then return true other wise false).
- Used map and set. Map ->. XtoYMap and set to store all the y coordinates. -> unordered_map<string, set<String>> mp.
	- Time Complexity -> O(nlogn).

VERDICT -> NEGATIVE