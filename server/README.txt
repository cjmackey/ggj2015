
The endpoints, and what they do

The game client should randomly generate a user id string, preferably
containing simple characters like letters and/or numbers.

Posting to /lfg/:user_id will either respond with "wait" (indicating
that you should check again in a couple seconds), or with the game_id
of a game you've been assigned to.

Posting to /games/:game_id/sync/:player_id will respond with either
"wait" or the id of the other player.  This also clears any actions
you had previously sent, so is sensible to do before any game round
starts.

Posting to /games/:game_id/actions/:player_id with the url encoded
actions {"actions":"whatever my actions are"} will put them up on the
server.

Getting /games/:game_id/actions will respond with either "wait" or the
users and their actions, separated by pipes (|), like this:

user1|uddldd|user2|ddlddu

These can be seen in test_server.py
