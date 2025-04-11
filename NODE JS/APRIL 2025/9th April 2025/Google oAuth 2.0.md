
```js
// app.js
const express = require("express");
const passport = require("passport");
const session = require("express-session");
require("./auth"); // Load the file

const app = express();
app.use(session({ secret: "cats" }));
app.use(passport.initialize()); // For passport to work with express
app.use(passport.session()); // For passport to work with express-session

function isLoggedIn(req, res, next) {
	req.user ? next() : res.sendStatus(401);
}

app.get("/", (req, res) => {
	res.send(
		"<a href = 'http://localhost:5000/auth/google'>Sign-in with Google</a>"
	);
});

app.get("/protected", isLoggedIn, (req, res) => {
	console.log("Successfully logged in");
	res.json(req.user);
});

app.get(
	"/auth/google",
	passport.authenticate("google", {
		scope: ["email", "profile", "openid"], // Which info we want to get
		prompt: "select_account", // This forces google to open a select account page for sign-in instead of directly choosing account
	})
);

app.get(
	"/google/callback",
	passport.authenticate("google", {
		successRedirect: "/protected",
		failureRedirect: "/auth/failure",
	})
);

app.get("/auth/failure", (req, res) => {
	res.send("Something went wrong");
});

app.get("/logout", (req, res) => {
	req.logout(function (err) {
		if (err) {
			return next(err);
		}
		req.session.destroy();
		res.redirect("/");
	});
});

app.listen(5000, () => {
	console.log("Server listening on http://localhost:5000");
});
```


```js
//auth.js
const passport = require("passport");
const
GoogleStrategy = require("passport-google-oauth20").Strategy;

const GOOGLE_CLIENT_ID =
	"1052482848311-ot7hb0tfq677fq45eq1evh0f3lt53408.apps.googleusercontent.com";
const GOOGLE_CLIENT_SECRET = "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";

passport.use(
	new GoogleStrategy(
		{
			clientID: GOOGLE_CLIENT_ID,
			clientSecret: GOOGLE_CLIENT_SECRET,
			callbackURL: "http://localhost:5000/google/callback", // which route to go when user selects the account
		},
		function (accessToken, refreshToken, profile, done) {
			console.log({ accessToken, refreshToken });
			return done(null, profile);
		}
	)
);

passport.serializeUser(function (user, done) {
	done(null, user);
});

// We have to serialize the user ? Ask sir !!!
passport.deserializeUser(function (user, done) {
	done(null, user);
});
```