Enums are not mutually exclusive
https://stackoverflow.com/questions/33607284/control-reaches-end-of-non-void-function-with-fully-handled-case-switch-over-a

Generics have no constraints (fixed in c++ 20 with concepts)

Try doing old_path.size() - 1... even checking for out of bounds might segfault!
```c++
//Toolhead movement logic 
std::vector<Point> path; //initialized to something in the real code 
if (index < path.size() - 1) { 
	Point p1 = path.at(index); 
	Point p2 = path.at(index + 1); 
	float dist = sqrt(powf(p1.x - p2.x, 2.0f) + powf(p1.y - p2.y, 2.0f)); 
}
```