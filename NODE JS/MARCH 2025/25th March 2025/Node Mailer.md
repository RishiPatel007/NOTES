Node mailer can be used to send emails with node

First we have to create a transporter

```js
const transporter = nodemailer.createTransport({
	host: "smtp.gmail.com", // Which email service we are using
	port: 465, // which port we are using , 465 is used because it automatically encryt our email
	secure: true, // This tells email to use SSL
	auth: {
		user: "rishi8124007@gmail.com", // From which email we want to send mail
		pass: "**** **** **** ****", // App password of that email
	},
});
```

Then we can send dynamic emails using ejs like this : 

```js
function sendDynamicMail(templateFilePath, data, sendTo, subject) {
	return new Promise((resolve, reject) => {
		ejs.renderFile(templateFilePath, data)
			.then(async (html) => {
				console.log("Sending Mail...");
				try {
					const info = await transporter.sendMail({
						from: '"Rishi 👻" <rishi8124007@gmail.com>',
						to: sendTo,
						subject: subject,
						html,
					});
					console.log("Message sent: %s", info.messageId);
					resolve("Message sent");
				} catch (err) {
					console.log(err);
					reject("Message not sent");
				}
			})
			.catch((err) => {
				reject("File Not Found");
			});
	});
}
```

