twitter-friendmap
=================

creates a d3.js nodemap of your twitter friends' relationships 


##Roadmap

###SQL tables

```sql
followers
ID @NAME

following
ID @NAME

friends
ID @NAME

friends_following
ID FRIEND_NAME FOLLOWING_NAME
```
###Process/Pseudocode

1. gather `followers` per https://github.com/keaneingram/Twitter-Followers/blob/master/followers.php#L51-L55
2. truncate `followers`, fill with result 
3. repeat steps 1 and
4. 2 with `following` instead
5. get SELECT * FROM `followers` A INNER JOIN `following` B ON A.atname = B.atname
6. compare result of inner join with contents of friends per https://github.com/keaneingram/Twitter-Followers/blob/master/followers.php#L60-L73 d
7. delete lines from `friends_following`whose friend.atname matches output of L71
8. do 1 and
9. 2 again for each line of `friends`
10. delete lines from `friends_following` matching the friends.atname being operated on in 8
11. replace in friends_following with output of 9
12. output`friends_following.friend_name` and `friends_following.following_name` as "source" and "target" in json block per http://bl.ocks.org/mbostock/1153292 
13. there is no step 13
