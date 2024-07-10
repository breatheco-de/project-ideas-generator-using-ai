<!-- hide -->
# Create an Excuse Generator using AI
<!-- endhide -->

## 🌱 How to start this project?

Do not clone this repository because we are going to be using a different template.

We recommend opening the `flask template` or the `vanilla.js template` using a provisioning tool like [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recommended) or [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternatively, you can [clone the github repository](https://4geeks.com/how-to/github-clone-repository) on your local computer using the `git clone` command.

These are the repositories you need to open or clone:

```txt
🐍 For Python:
https://github.com/4GeeksAcademy/flask-rest-hello

👩🏽‍💻 For Javascript:
https://github.com/4GeeksAcademy/vanillajs-hello
```

> ⚠ You will need to have Node.js or Python 3.7+ installed if you do it locally, but all of that is already installed on Codespaces or Gitpod.

## 📝 Instructions

### Step 1: Set Up the Project

- [ ] Choose your preferred language and set up the boilerplate project from the provided templates.
   - For Python: Use the Flask template.
   - For JavaScript: Use the VanillaJS template.
   
- [ ] Follow the instructions in the README of the respective repositories to set up your development environment.

### Step 2: Get Access to ChatGPT's API

- [ ] Sign up for an account at [OpenAI](https://www.openai.com/).
- [ ] Navigate to the API section and obtain your API key for accessing the free version of ChatGPT.

### Step 3: Create an Input Form or use a prompt if building the project on the terminal

- [ ] Implement an input form in your chosen language where users can specify what the excuse should be for.
   - For Python (On the terminal): You might use the `prompt()` function to ask the user.
   - For JavaScript (): You might create an HTML form and handle form submission with JavaScript by manipulating the DOM.


### Step 4: Connect to ChatGPT's API

- [ ] Use the value from the input form to create a prompt for the ChatGPT API request.
- [ ] Send the request to the ChatGPT API and handle the response.

Example for Python:
```python
import requests

@app.route('/generate_excuse', methods=['POST'])
def generate_excuse():
    excuse_for = request.form['excuse_for']
    prompt = f"Give me an excuse for {excuse_for}:"
    
    response = requests.post('https://api.openai.com/v1/engines/davinci-codex/completions', 
                             headers={'Authorization': f'Bearer {api_key}'}, 
                             json={'prompt': prompt, 'max_tokens': 50})
    
    excuse = response.json()['choices'][0]['text']
    return render_template('result.html', excuse=excuse)
```

Example for JavaScript:
```javascript
document.getElementById('excuseForm').addEventListener('submit', async (event) => {
    event.preventDefault();
    const excuseFor = document.getElementById('excuseFor').value;
    const prompt = `Give me an excuse for ${excuseFor}:`;

    const response = await fetch('https://api.openai.com/v1/engines/davinci-codex/completions', {
        method: 'POST',
        headers: {
            'Authorization': `Bearer ${apiKey}`,
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({ prompt: prompt, max_tokens: 50 })
    });

    const data = await response.json();
    const excuse = data.choices[0].text;
    // Display the excuse to the user
});
```

### Step 5: Display the Generated Excuse

- [ ] Once you receive the response from ChatGPT's API, display the generated excuse to the user.
   - For Python (Flask): You might show the excuse in the terminal with a `print()`.
   - For JavaScript: You might update the DOM to show the excuse.

Example for JavaScript:
```javascript
document.getElementById('excuseForm').addEventListener('submit', async (event) => {
    event.preventDefault();
    const excuseFor = document.getElementById('excuseFor').value;
    const prompt = `Give me an excuse for ${excuseFor}:`;

    const response = await fetch('https://api.openai.com/v1/engines/davinci-codex/completions', {
        method: 'POST',
        headers: {
            'Authorization': `Bearer ${apiKey}`,
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({ prompt: prompt, max_tokens: 50 })
    });

    const data = await response.json();
    const excuse = data.choices[0].text;
    document.getElementById('result').innerText = `Your excuse is: ${excuse}`;
});
```

### Bonus Section

#### Additional Features to Practice and Improve the Project

1. **Styling:** Add CSS to style your web interface, making it more user-friendly and visually appealing.
2. **Customization:** Allow users to specify different types of excuses (e.g., work, school, family).
3. **History:** Store generated excuses in a database or local storage so users can view previously generated excuses.
4. **API Error Handling:** Add proper error handling for API requests to improve the user experience.

Feel free to explore and add more features to make your Excuse Generator even more robust and user-friendly!