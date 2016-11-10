When you want to find an object an check it present like:
`User.find(params[:id]).present?`, it is slower than using:
`User.exists? id: 1` because the second way doesn't load user, it just check in
database.
