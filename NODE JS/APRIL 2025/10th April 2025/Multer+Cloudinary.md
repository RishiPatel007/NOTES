```js
// multer.js
const multer = require("multer");

const storage = multer.diskStorage({
	destination: function (req, file, cb) {
		cb(null, "uploads/");
	},
	filename: function (req, file, cb) {
		cb(null, file.originalname);
	},
});
const upload = multer({ storage });

module.exports = { upload };

```

```js
//cloudinary.js
const cloudinary = require("cloudinary").v2;
const path = require("path");
require("dotenv").config();

cloudinary.config({
	cloud_name: process.env.CLOUDINARY_CLOUD_NAME,
	api_key: process.env.CLOUDINARY_API_KEY,
	api_secret: process.env.CLOUDINARY_API_SECRET,
});

async function uploadOnCloudinary(filePath) {
	const uploadResult = await cloudinary.uploader
		.upload(filePath, {
			public_id: path.basename(filePath),
			folder: process.env.CLOUDINARY_CLOUD_UPLOAD_FOLDER,
		})
		.catch((error) => {
			console.log(error);
		});

	return uploadResult;
}

module.exports = { uploadOnCloudinary };

```

```js
//app.js
const express = require("express");
const path = require("path");
const fs = require("fs");
const { uploadOnCloudinary } = require("./cloudinary");
const { upload } = require("./multer");

const app = express();

app.post("/upload", upload.single("file"), async (req, res) => {
	const result = await uploadOnCloudinary(
		path.join(__dirname, "uploads", req.file.filename)
	);
	console.log(result);
	fs.unlinkSync(path.join(__dirname, "uploads", req.file.filename));
	res.json(req.file);
});

const PORT = process.env.PORT || 5000;
app.listen(PORT, (err) => {
	if (err) {
		console.log("Some error happened");
		return;
	}
	console.log(`Server listening on http://localhost:${PORT}`);
});

```