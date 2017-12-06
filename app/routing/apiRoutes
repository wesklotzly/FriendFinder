// Routes
var friends = require("../data/friends");

// friend JSON
module.exports = function (app) {
    app.get("/api/friends", function(req, res) {
    res.json(friends);
});
  
// add friends
app.post("/api/friends", function(req, res) {
    var bestie = {
        name: "",
        photo: "",
        difference: 1000
    };

    var userData = req.body;
    var userScores = userData.scores;

    // store friend's choice differences
    var totalDiff;

    // loop through friends
    for (var i = 0; i < friends.length; i++) {
        var currentFriend = friends[i];
        totalDiff = 0;

        // loop through friend's results
        for (var j = 0; j < currentFriend.scores.length; j++) {
            var currentFriendScore = currentFriend.scores[j];
            var currentUserScore = userScores[j];

            totalDiff += Math.abs(parseInt(currentFriendScore) - parseInt(currentUserScore));
        }

        if (totalDiff <= bestie.difference) {
            bestie.name = currentFriend.name;
            bestie.photo = currentFriend.photo;
            bestie.difference = totalDiff;
        }
    }

    friends.push(userData);

    res.json(bestMatch);
});
}
