Where structs give you a way of grouping together related fields and data, like a Rectangle with its width and height, enums give you a way of saying a value is one of a possible set of values. For example, we may want to say that Rectangle is one of a set of possible shapes that also includes Circle and Triangle.

enum Direction {
    North,
    East,
    South,
    West
}

fn main(){
    let my_direction = Direction::North;
    let new_direction = my_direction;
}