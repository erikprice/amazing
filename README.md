# Amazing Algorithms

Framework for playing with maze generation and solving algorithms.

Right now the focus is on creating a maze solving algorithm, see below for examples. The results are displayed on a central server that solvers connect to which allows everyone to develop and test on their own laptops beforehand.

## Testing a solver

Unit test your solver before submitting it.

### Node.js

Node uses [Jamine](http://jasmine.github.io/1.3/introduction.html) for testing.

```
npm install
npm test
```

### Java

Java uses [JUnit](http://junit.org/) and [PowerMock](https://code.google.com/p/powermock/) for testing.

```
mvn test
```

### Ruby

Ruby uses [RSpec](http://rspec.info/) for testing.

```
bundle install
bundle exec rspec src/test/ruby
```

## Register a solver

Once a solver is complete you can register it with the central server for all to play with. NOTE: localhost is used as an example, the projected central server shows the IP to connect to.

### Node.js

```
npm install
./node.sh ws://localhost:3000 src/main/node/randomWalk.js
```

### Java

```
./java.sh ws://localhost:3000 com.neophi.amazing.solver.RandomWalkSolverFactory
```

### Ruby

```
bundle install
./ruby.sh ws://localhost:3000 src/main/ruby/random_walk.rb
```

## Central server

The central server maintains the list of maze generators and solvers and coordinates sending a generated maze to a solver and displaying the solution.

```
npm install
npm start
open http://localhost:3000/
```

## Maze solving algorithms

### Random Walk

Randomly pick an exit.

### Wall Follower

Use either left-hand rule or right-hand rule. 

Keep one hand in contact with one wall of the maze and pick the exit which follows that rule.

## JSON

### Location

A location is a hash with x, y, and z properties:

```
{
  x: 0,
  y: 0,
  z: 0
}
```

### Solver output

Maze solver next() output is the next location to visit, which must be one of the valid exits for the room.

### Generator output

Maze generation output is a hash with start and finish locations and an array of rooms each with a location and list of exit locations.

```
{
  start: {
    x: 0,
    y: 0,
    z: 0
  },
  finish: {
    x: 1,
    y: 1,
    z: 0
  },
  rooms: [
    {
      x: 0,
      y: 0,
      z: 0,
      exits: [
        {
          x: 1,
          y: 0,
          z: 0
        },
        {
          x: 0,
          y: 1,
          z: 0
        }
      ]
    },
    {
      x: 1,
      y: 0,
      z: 0,
      exits: [
        {
          x: 0,
          y: 0,
          z: 0
        },
        {
          x: 1,
          y: 1,
          z: 0
        }
      ]
    },
    {
      x: 0,
      y: 1,
      z: 0,
      exits: [
        {
          x: 0,
          y: 0,
          z: 0
        }
      ]
    },
    {
      x: 0,
      y: 0,
      z: 0,
      exits: [
        {
          x: 1,
          y: 0,
          z: 0
        }
      ]
    }
  ]
}
```

## Resources

[http://en.wikipedia.org/wiki/Maze_generation_algorithm](http://en.wikipedia.org/wiki/Maze_generation_algorithm)

[http://en.wikipedia.org/wiki/Maze_solving_algorithm](http://en.wikipedia.org/wiki/Maze_solving_algorithm)

[http://weblog.jamisbuck.org/under-the-hood](http://weblog.jamisbuck.org/under-the-hood)

[http://www.astrolog.org/labyrnth/algrithm.htm](http://www.astrolog.org/labyrnth/algrithm.htm)

## Notes

Newer version of Ruby on Mac OS X when running bundle install you might need:

```
ARCHFLAGS=-Wno-error=unused-command-line-argument-hard-error-in-future bundle install
```

## License

Copyright (c) 2013 Daniel Rinehart. This software is licensed under the MIT License.
