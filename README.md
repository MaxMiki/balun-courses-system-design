# Travel social network - System Design

It is an educational project for a course on system design.
Travel social network is a system when people can share their trip with different people.

### Functionl requirements:

- Users can share their posts with photos and geo location
- Users can rate and comment people's posts
- Users can follow other people
- Users can search popular travel places and view popular posts from those places
- Users can converse with other people using personal text messages
- Users can view feed with other people's posts

### Non-functional requirements:

- 10 000 000 DAU
- Each user publishes one post per week on average (1 500 000 write operations per day)
- Each user send 10 messages to other users per day on average (100 000 000 write operations per day)
- Each user views their feed 5 times per day (50 000 000 read operations per day)
- Each user views their chat 10 times per day (50 000 000 write operations per day)
- One post can have maximum 10 pictures and 1 000 symbols of text
- The maximum size of one photo is 2 megabytes
- The maximum size of a personal message and a comment is 200 symbols
- Geo distribution is not needed
- The number of requests in summer is twice as high as in winter

## Basic calculations

Required memory:

    Replication factor = 3
    Post metadata size: id(8 bytes) + userId(8 bytes) + geo_point(32 bytes) + text(2 kilobytes) = 2 kilobytes *3 + 1 extra for index = 8 kilobytes
    Post media size: 5 in one post on average each 1 megabyte in average = 5 megabytes * 3 = 15 megabytes
    Required memory for 1 year ~= 10 petabytes
    Throughput ~= 600MB/s