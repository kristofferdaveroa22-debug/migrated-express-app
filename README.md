**1. How many lines of code did you eliminate by migrating to Express?**
Approximately 30–50 lines of code, since Express removes the need to manually handle routing, headers, and responses.

**2. What was the most surprising thing that Express handled automatically?**
Express automatically handled routing, JSON parsing (with express.json()), and sending responses, making the code much simpler than using the built-in http module.

**3. Why is express.static() better than manually using fs.readFile()?**
express.static() is better because it automatically serves static files (HTML, CSS, JavaScript, images, etc.) without writing separate fs.readFile() logic for each file. It is simpler, faster, and easier to maintain.

**4. If you had to add a PUT route to update a task, how would you write it in Express? (Write a short code snippet.)**

app.put('/api/tasks/:id', (req, res) => {
    const id = parseInt(req.params.id);
    const task = tasks.find(t => t.id === id);

    if (!task) {
        return res.status(404).json({ message: 'Task not found' });
    }

    task.name = req.body.name || task.name;
    task.completed = req.body.completed ?? task.completed;

    res.json(task);
});

**5. What is one disadvantage of using a framework like Express?**
One disadvantage is that it adds an external dependency to your project. You also need to learn the framework's conventions, and updates to the framework may require changes to your code.
