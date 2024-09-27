<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lesson Sharing Platform</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Share Your Lessons Learned</h1>
    </header>

    <section id="submit-section">
        <h2>Submit Your Lesson</h2>
        <form id="lesson-form">
            <input type="text" id="name" placeholder="Your Name" required>
            <select id="category" required>
                <option value="" disabled selected>Select a Category</option>
                <option value="business">Starting a Business</option>
                <option value="coding">Learning to Code</option>
                <option value="life">Life Lessons</option>
            </select>
            <textarea id="lesson" placeholder="Share your lesson..." required></textarea>
            <button type="submit">Submit</button>
        </form>
    </section>

    <section id="lessons">
        <h2>Lessons Learned</h2>
        <div class="category" id="business">
            <h3>Starting a Business</h3>
            <ul id="business-list"></ul>
        </div>
        <div class="category" id="coding">
            <h3>Learning to Code</h3>
            <ul id="coding-list"></ul>
        </div>
        <div class="category" id="life">
            <h3>Life Lessons</h3>
            <ul id="life-list"></ul>
        </div>
    </section>

    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
    color: #333;
}

header {
    background: #0073e6;
    color: white;
    padding: 10px 20px;
    text-align: center;
}

#submit-section {
    padding: 20px;
    background: #fff;
    margin: 20px;
    border-radius: 5px;
}

#lesson-form {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

input, select, textarea {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
}

button {
    padding: 10px;
    border: none;
    border-radius: 4px;
    background: #0073e6;
    color: white;
    cursor: pointer;
}

button:hover {
    background: #005bb5;
}

#lessons {
    padding: 20px;
}

.category {
    background: #fff;
    padding: 10px;
    margin: 10px 0;
    border-radius: 5px;
}

h3 {
    margin-bottom: 5px;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    background: #e9e9e9;
    padding: 10px;
    border-radius: 4px;
    margin-bottom: 5px;
}
document.getElementById('lesson-form').addEventListener('submit', function (event) {
    event.preventDefault();

    const name = document.getElementById('name').value;
    const category = document.getElementById('category').value;
    const lesson = document.getElementById('lesson').value;

    const lessonItem = document.createElement('li');
    lessonItem.textContent = `${name}: ${lesson}`;

    if (category === 'business') {
        document.getElementById('business-list').appendChild(lessonItem);
    } else if (category === 'coding') {
        document.getElementById('coding-list').appendChild(lessonItem);
    } else if (category === 'life') {
        document.getElementById('life-list').appendChild(lessonItem);
    }

    // Clear form
    document.getElementById('lesson-form').reset();
});
