<!DOCTYPE html>
<html>
<head>
    <title>Data Entry Form</title>
</head>
<body>
    <h1>Data Entry Form</h1>
    <form id="entryForm">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required><br><br>

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>

        <label for="comments">Comments:</label>
        <textarea id="comments" name="comments" required></textarea><br><br>

        <button type="button" onclick="submitData()">Submit</button>
    </form>

    <script>
        async function submitData() {
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const comments = document.getElementById('comments').value;

            const response = await fetch('https://script.google.com/macros/s/AKfycbzSZ0L2en1blMJx2nnWlGxosZg_PbHMPhHZOaJYP9prP5yPs-D4Fg1I34JyexDGRuPp0w/exec', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({ name, email, comments }),
            });

            const result = await response.json();
            if (result.status === 'success') {
                alert('Data submitted successfully!');
                document.getElementById('entryForm').reset();
            } else {
                alert('Data submission failed.');
            }
        }
    </script>
</body>
</html>
