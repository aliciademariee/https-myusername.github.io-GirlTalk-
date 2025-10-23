<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>GirlTalk 💕</title>
  <style>
    body {
      margin: 0;
      font-family: "Poppins", "Nunito", sans-serif;
      background: linear-gradient(180deg, #fff7f8 0%, #ffeef5 100%);
      color: #55263b;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    .logo {
      width: 120px;
      height: 120px;
      background: #ffd9e1;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 10px 25px rgba(255, 200, 210, 0.5);
    }

    .logo::before {
      content: "💬";
      font-size: 64px;
    }

    h1 {
      font-family: "Pacifico", cursive;
      color: #ff5c8a;
      margin-top: 20px;
      font-size: 36px;
    }

    p {
      font-size: 16px;
      color: #8a6b7a;
      margin: 10px 0 30px;
    }

    button {
      background-color: #ffd9e1;
      border: none;
      padding: 12px 24px;
      border-radius: 25px;
      font-weight: bold;
      color: #7a294b;
      cursor: pointer;
      box-shadow: 0 6px 16px rgba(255, 180, 200, 0.4);
      transition: transform 0.2s ease;
    }

    button:hover {
      transform: scale(1.05);
    }

    footer {
      position: absolute;
      bottom: 20px;
      font-size: 12px;
      color: #a27d8a;
    }
  </style>
</head>
<body>
  <div class="logo"></div>
  <h1>GirlTalk</h1>
  <p>A cozy corner for every girl 🌸</p>
<button id="joinBtn">Join Now</button>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>GirlTalk 💕</title>
  <style>
    body {
      margin: 0;
      font-family: "Poppins", "Nunito", sans-serif;
      background: linear-gradient(180deg, #fff7f8 0%, #ffeef5 100%);
      color: #55263b;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    .logo {
      width: 120px;
      height: 120px;
      background: #ffd9e1;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 10px 25px rgba(255, 200, 210, 0.5);
    }

    .logo::before {
      content: "💬";
      font-size: 64px;
    }

    h1 {
      font-family: "Pacifico", cursive;
      color: #ff5c8a;
      margin-top: 20px;
      font-size: 36px;
    }

    p {
      font-size: 16px;
      color: #8a6b7a;
      margin: 10px 0 30px;
    }

    button {
      background-color: #ffd9e1;
      border: none;
      padding: 12px 24px;
      border-radius: 25px;
      font-weight: bold;
      color: #7a294b;
      cursor: pointer;
      box-shadow: 0 6px 16px rgba(255, 180, 200, 0.4);
      transition: transform 0.2s ease;
    }

    button:hover {
      transform: scale(1.05);
    }

    footer {
      position: absolute;
      bottom: 20px;
      font-size: 12px;
      color: #a27d8a;
    }
  </style>
</head>
<body>
<script>
document.addEventListener("DOMContentLoaded", function() {
  let currentUser = "";

  const joinBtn = document.getElementById("joinBtn");

  // --- Feed container ---
  const feedContainer = document.createElement("div");
  feedContainer.id = "feed";
  Object.assign(feedContainer.style, {
    width: "100%",
    maxWidth: "400px",
    height: "80vh",
    overflowY: "auto",
    padding: "20px",
    display: "none",
    margin: "20px auto",
    boxSizing: "border-box"
  });
  document.body.appendChild(feedContainer);

  // --- Floating + button ---
  const addPostBtn = document.createElement("button");
  addPostBtn.innerText = "+";
  Object.assign(addPostBtn.style, {
    position: "fixed",
    bottom: "30px",
    right: "30px",
    width: "60px",
    height: "60px",
    borderRadius: "50%",
    fontSize: "36px",
    backgroundColor: "#ffb6c1",
    color: "#fff",
    border: "none",
    cursor: "pointer",
    boxShadow: "0 4px 10px rgba(255,182,193,0.5)",
    display: "none"
  });
  document.body.appendChild(addPostBtn);

  // --- Verification modal ---
  const verifyModal = document.createElement("div");
  Object.assign(verifyModal.style, {
    position: "fixed",
    top: "0",
    left: "0",
    width: "100%",
    height: "100%",
    display: "none",
    justifyContent: "center",
    alignItems: "center",
    background: "rgba(0,0,0,0.3)"
  });
  const verifyContent = document.createElement("div");
  Object.assign(verifyContent.style, {
    background: "#ffeef5",
    borderRadius: "25px",
    padding: "20px",
    textAlign: "center"
  });
  verifyContent.innerHTML = `
    <h3>🌸 Girl Verification</h3>
    <p>Answer this to join:</p>
    <p>What item do most girls carry in their purse?</p>
    <input type="text" id="verifyAnswer" placeholder="Your answer here" style="padding:10px; border-radius:10px; border:1px solid #ffc0cb; width:80%; margin:10px 0;">
    <br>
    <button id="submitVerifyBtn">Submit</button>
  `;
  verifyModal.appendChild(verifyContent);
  document.body.appendChild(verifyModal);

  const verifyAnswer = document.getElementById("verifyAnswer");
  const submitVerifyBtn = document.getElementById("submitVerifyBtn");

  // --- Username modal ---
  const usernameModal = document.createElement("div");
  Object.assign(usernameModal.style, {
    position: "fixed",
    top: "0",
    left: "0",
    width: "100%",
    height: "100%",
    display: "none",
    justifyContent: "center",
    alignItems: "center",
    background: "rgba(0,0,0,0.3)"
  });
  const usernameContent = document.createElement("div");
  Object.assign(usernameContent.style, {
    background: "#ffeef5",
    padding: "20px",
    borderRadius: "25px",
    textAlign: "center"
  });
  usernameContent.innerHTML = `
    <h3>Choose your GirlTalk username 💕</h3>
    <input type="text" id="usernameInput" placeholder="Doesn't have to be real" style="padding:10px; border-radius:10px; border:1px solid #ffc0cb; width:80%; margin:10px 0;">
    <br>
    <button id="confirmUsernameBtn">Join 🌸</button>
  `;
  usernameModal.appendChild(usernameContent);
  document.body.appendChild(usernameModal);

  const usernameInput = document.getElementById("usernameInput");
  const confirmUsernameBtn = document.getElementById("confirmUsernameBtn");

  // --- Create Post modal ---
  const postModal = document.createElement("div");
  Object.assign(postModal.style, {
    display: "none",
    position: "fixed",
    top: "0",
    left: "0",
    width: "100%",
    height: "100%",
    background: "rgba(0,0,0,0.3)",
    justifyContent: "center",
    alignItems: "center"
  });
  const postContent = document.createElement("div");
  Object.assign(postContent.style, {
    background: "#fff0f5",
    padding: "20px",
    borderRadius: "15px",
    width: "80%",
    maxWidth: "400px",
    textAlign: "center"
  });
  postContent.innerHTML = `
    <h3>Create a post 💕</h3>
    <select id="postCategory">
      <option value="Advice">Advice</option>
      <option value="Vent">Vent</option>
      <option value="Share">Share</option>
    </select>
    <textarea id="postText" placeholder="Write your post here..." style="width:100%;border-radius:10px;padding:10px;margin:10px 0;border:1px solid #ffc0cb;"></textarea>
    <input type="file" id="postImage" accept="image/*" style="margin:10px 0;">
    <br/>
    <button id="submitPostBtn">Post 🌸</button>
    <button id="closeModalBtn">Cancel</button>
  `;
  postModal.appendChild(postContent);
  document.body.appendChild(postModal);

  const postText = postContent.querySelector("#postText");
  const postCategory = postContent.querySelector("#postCategory");
  const postImage = postContent.querySelector("#postImage");
  const submitPostBtn = postContent.querySelector("#submitPostBtn");
  const closeModalBtn = postContent.querySelector("#closeModalBtn");

  // --- Join button click ---
  joinBtn.addEventListener("click", () => verifyModal.style.display = "flex");

  // --- Verification submit ---
  submitVerifyBtn.addEventListener("click", () => {
    const answer = verifyAnswer.value.trim().toLowerCase();
    const correctAnswers = ["wallet", "phone", "keys", "makeup", "lipstick", "hand sanitizer"];
    if (!answer) return alert("Please answer the question!");
    if (!correctAnswers.includes(answer)) return alert("Hmm, that doesn't seem right. Try again!");
    verifyModal.style.display = "none";
    usernameModal.style.display = "flex";
  });

  // --- Confirm username ---
  confirmUsernameBtn.addEventListener("click", () => {
    const username = usernameInput.value.trim();
    if (username) {
      currentUser = username;
      document.querySelector(".logo")?.remove();
      document.querySelector("h1")?.remove();
      document.querySelector("p")?.remove();
      joinBtn.style.display = "none";
      feedContainer.style.display = "block";
      addPostBtn.style.display = "block";

      const welcomeText = document.createElement("h2");
      welcomeText.innerText = `Welcome to GirlTalk 💕`;
      welcomeText.style.textAlign = "center";
      welcomeText.style.color = "#ff5c8a";
      welcomeText.style.marginBottom = "15px";
      feedContainer.prepend(welcomeText);

      usernameModal.style.display = "none";
    } else alert("Please enter a username!");
  });

  // --- Create post modal ---
  addPostBtn.addEventListener("click", () => postModal.style.display = "flex");
  closeModalBtn.addEventListener("click", () => postModal.style.display = "none");

  // --- Submit post ---
  submitPostBtn.addEventListener("click", () => {
    const text = postText.value.trim();
    const file = postImage.files[0];
    if (!text && !file) return alert("Add text or image!");

    const card = document.createElement("div");
    card.className = "postCard";
    Object.assign(card.style, {
      background: "#ffeef5",
      borderRadius: "20px",
      padding: "15px",
      margin: "10px 0",
      boxShadow: "0 4px 8px rgba(255,182,193,0.4)",
      position: "relative"
    });

    card.innerHTML = `<strong>${currentUser}</strong> • <em>${postCategory.value}</em><p style="margin-top:5px;">${text}</p>`;

    if (file) {
      const reader = new FileReader();
      reader.onload = function(e) {
        const img = document.createElement("img");
        img.src = e.target.result;
        img.style.maxWidth = "100%";
        img.style.borderRadius = "15px";
        img.style.marginTop = "10px";
        card.appendChild(img);
      }
      reader.readAsDataURL(file);
    }

    // Delete button for owner
    const deleteBtn = document.createElement("button");
    deleteBtn.innerText = "🗑️";
    Object.assign(deleteBtn.style, {
      position: "absolute",
      top: "10px",
      right: "10px",
      border: "none",
      background: "transparent",
      cursor: "pointer",
      fontSize: "18px"
    });
    deleteBtn.addEventListener("click", e => { e.stopPropagation(); card.remove(); });
    card.appendChild(deleteBtn);

    // --- Comment/advice section ---
    const commentContainer = document.createElement("div");
    commentContainer.style.marginTop = "10px";

    const commentList = document.createElement("div");
    commentList.style.marginBottom = "5px";
    commentContainer.appendChild(commentList);

    const commentInput = document.createElement("input");
    commentInput.type = "text";
    commentInput.placeholder = "Give advice or comment...";
    Object.assign(commentInput.style, {
      width: "100%",
      borderRadius: "10px",
      border: "1px solid #ffc0cb",
      padding: "5px"
    });

    commentInput.addEventListener("keydown", e => {
      if (e.key === "Enter" && commentInput.value.trim() !== "") {
        const commentText = document.createElement("p");
        commentText.innerHTML = `<strong>${currentUser}:</strong> ${commentInput.value}`;
        commentText.style.background = "#fff0f5";
        commentText.style.padding = "5px";
        commentText.style.borderRadius = "10px";
        commentText.style.margin = "3px 0";
        commentList.appendChild(commentText);
        commentInput.value = "";
      }
    });

    commentContainer.appendChild(commentInput);
    card.appendChild(commentContainer);

    feedContainer.appendChild(card);

    postText.value = "";
    postImage.value = "";
    postModal.style.display = "none";
  });
});
</script>
  <footer>💕 Be kind, be cozy, be real 💕</footer>
</body>
</html>
