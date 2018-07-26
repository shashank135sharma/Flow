Flow is a traffic modeling system that uses beacons, billboards, and parking lot lights to optimize traffic flow in venues such as sports stadiums, concerts, and malls.

## Inspiration
The inspiration for our project began when the three of us were tired of massive parking lot queues

What it does
Our app controls the entire user experience as soon as they drive onto the stadium campus. Right off the bat, the app is used for parking validation and entering the premises: The user is then prompted through signs on the road to an optimal parking spot, avoiding all avoidable traffic. Once the user parks, the app memorizes where the user Parks and prompts the user to a Gate. From there, the user can find their seat, find food, find restrooms, or get live stat updates about the venue from the app.

## How we built it
The front end is split into three user experiences: the mobile app, the signs that prompt them to their parking locations, and on-site on-the-ground parking lights that direct users to their parking spots.

The app itself is built on Xcode using Swift. The app communicates with beacons using bluetooth. We use our custom built metering algorithms, using signal strength as a function of distance.

The prompting screens are static html pages hosted through an express.js server on mongodb Atlas. The page is updated using socket.io, culling data from the database.

The ground lights are LEDs on a breadboard all connected to a central Arduino. This central Arduino hosts its own server to communicate to the database using flask and intel-edison.

The backend is built using node.js, mongoDB, and flask.

Each beacon is built with arduino 101s communicating

## Challenges we ran into
One challenge we ran into was a variable metering response from the beacons. Because we are not using dedicated beacons, the signals were inconsistent due to environmental factors such as outside bluetooth interference, physical obstacles, and the physical limitations of the board. So, we wrote a high-pass function on the raw distances and took the average of the surrounding five data points to determine distances.

Another challenge we ran into was trying to run a dynamic html page on Ruby on Rails. We needed to post a live page to instruct cars to turn, which had to be a single endpoint that would dynamically serve different images instructing the user.

Another challenge we ran into was trying to get MongoDB Stitch on iOS to work. But alas, It didn't.

