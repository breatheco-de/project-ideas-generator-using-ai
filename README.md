<!-- hide -->
# Project Ideas Generator using AI and React
<!-- endhide -->

<onlyfor saas="true" withBanner="false">
## 🌱 How to start this project?

Do not clone this repository because we will be using a different template.

We recommend opening the `react template` using a provisioning tool like [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recommended) or [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternatively, you can [clone the GitHub repository](https://4geeks.com/how-to/github-clone-repository) on your local computer using the `git clone` command.

This is the repository you need to open or clone:

```
https://github.com/4GeeksAcademy/react-hello
```

> ⚠ You will need to have Node.js installed if you do it locally, but all of that is already installed on Codespaces or Gitpod!
</onlyfor>

## 📝 Instructions:

### Step 1: Set Up the Project

- [ ] Set up the boilerplate project from the provided React template.
  
- [ ] Follow the instructions in the README of the repository to set up your development environment.

### Step 2: Get Access to ChatGPT's API

- [ ] Sign up for an account at [OpenAI](https://www.openai.com/).
- [ ] Navigate to the API section and obtain your API key for accessing ChatGPT.

### Step 3: Create an Input Form

- [ ] In your React app, create a form where users can specify the topic or area they are interested in for project ideas.

### Step 4: Connect to ChatGPT's API

- [ ] Use the user's input to create a prompt for the ChatGPT API.
- [ ] Make a request to the ChatGPT API when the form is submitted.

Example:

```js
const handleGenerateIdeas = async (topic) => {
 const prompt = `Provide me with three project ideas in the field of ${topic}.`;

 try {
   const response = await fetch('https://api.openai.com/v1/engines/text-davinci-003/completions', {
     method: 'POST',
     headers: {
       'Authorization': `Bearer YOUR_OPENAI_API_KEY`,
       'Content-Type': 'application/json',
     },
     body: JSON.stringify({
       prompt: prompt,
       max_tokens: 150,
       n: 1,
       stop: null,
       temperature: 0.7,
     }),
   });

   const data = await response.json();
   const generatedText = data.choices[0].text.trim();
   const ideaList = generatedText.split('\n').filter(idea => idea.trim() !== '');
 } catch (error) {
   console.error('Error generating ideas:', error);
 }
};
```

> **Note:** Remember to replace `'YOUR_OPENAI_API_KEY'` with your actual OpenAI API key.

### Step 5: Display the Generated Project Ideas

- [ ] Display the list of project ideas returned from the API to the user in your React app.
- [ ] Ensure the ideas are presented in a readable format, possibly with styling to enhance user experience.

### Step 6: Bonus - Enhance the User Experience

- [ ] Allow users to specify additional parameters, such as the number of ideas to generate or the level of complexity.
- [ ] Implement loading indicators while the API request is being processed.
- [ ] Add error handling to notify users if something goes wrong with the API request.

### Bonus Section

#### Additional Features to Practice and Improve the Project

1. **Save Ideas:** Implement functionality to save or bookmark generated ideas for future reference.
2. **Share Ideas:** Add a feature to share generated ideas via email or social media.
3. **History:** Keep a history of generated ideas so users can revisit them without regenerating.
4. **Custom Prompts:** Allow advanced users to input their own custom prompts to the AI.
5. **Styling:** Enhance the app's appearance using CSS or styling libraries like [Bootstrap](https://getbootstrap.com/) or [Material-UI](https://material-ui.com/).
6. **User Authentication:** Implement user accounts so users can save and access their ideas across devices.

Explore different enhancements to make your Project Ideas Generator more interactive and user-friendly!
