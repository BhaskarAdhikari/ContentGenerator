Content Generator using OpenAI API

Overview:
This Python project demonstrates how to build a Content Generator using the OpenAI API. It allows users to input prompts and get detailed and relevant content based on their input. The project includes functions for generating content using OpenAI's GPT-4 model and handles API connections and errors gracefully.

Features:
API Integration: Connects to OpenAI's API using an API key stored in environment variables.
Content Generation: Accepts user prompts and returns well-structured content.
Customizable Models: Supports different models, with GPT-4 as the default.
Error Handling: Catches and displays errors without crashing.
Requirements
Python 3.12.7 or later
OpenAI Python library
Install the OpenAI library if you haven’t already:

bash
Copy
Edit
pip install openai
Setup
Obtain an API key from OpenAI.
Set your API key as an environment variable:
bash
Copy
Edit
export OPENAI_API_KEY='your_api_key_here'
Ensure the openai library is installed.
Usage
1. Getting a Standard Response
This part of the code sends a prompt to the GPT-4 model and prints the response.

python
Copy
Edit
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "user", "content": "Say this is a test"},
    ]
)
print(response.choices[0].message.content)
Example Output:

bash
Copy
Edit
This is a test.
2. Custom Content Generation
The get_chat_completion function takes a user prompt and generates content based on it.

python
Copy
Edit
def get_chat_completion(prompt, model="gpt-4"):
    try:
        response = client.chat.completions.create(
            messages=[
                {"role": "user", "content": prompt}
            ],
            model=model
        )
        completion_message = response.choices[0].message
        return completion_message.content.strip()
    except Exception as e:
        print(f"An error occurred: {e}")
        return None
3. Interactive Content Generation
This section of the code allows users to input prompts and receive generated content:

python
Copy
Edit
def main():
    prompt = input("Enter your prompt: ")
    content = get_chat_completion(prompt)
    if content:
        print("\nGenerated Content:\n")
        print(content)

if __name__ == "__main__":
    client = OpenAI(api_key=os.environ.get("OPENAI_API_KEY"))
    main()
Example Usage:

vbnet
Copy
Edit
Enter your prompt: Tell me an interesting fact about Cristiano Ronaldo
Example Output:

css
Copy
Edit
Generated Content:

Cristiano Ronaldo has his own museum in his hometown of Funchal, Portugal, called the Museu CR7. The museum showcases his awards, memorabilia, and personal items, reflecting his successful football career.
Customization
Model Selection: Change "gpt-4" to another model if needed.
API Key: Ensure the API key is set correctly in environment variables.
Error Handling
If an error occurs during API calls, the function prints an error message instead of crashing:

vbnet
Copy
Edit
An error occurred: [Error details]
Notes
Make sure your API key is valid and has enough quota.
Customize the model or parameters as needed for different use cases.
This project provides a simple yet effective way to generate content using OpenAI's API. Feel free to expand or modify it for more advanced use cases!
