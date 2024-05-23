# Guide: Running from Python

## Create a Virtual Environment
1. **Create a Python Virtual Environment in order to then install the required libraries:**

```python
python -m venv gpt4free
source gpt4free/bin/activate
pip install -U g4f[all]
````

## Install the required 
2. **Install using PyPI package:**
```
pip install -U g4f[all]
```
   - How do I install only parts or do disable parts?
   Use partial requirements: [/docs/requirements](https://github.com/pcastagnaro/gpt4free/blob/main/docs/requirements.md)

## Single prompt via CLI parameter
This will walk you through the process of using `gpt4free` from Python sending a single prompt via parameter in the command line.

3. **Create a new Python script:**
   - Create a new file called `gpt4free_python.py` and input the following content:
     ```python
     import argparse
     from g4f.client import Client


     def main():
       parser = argparse.ArgumentParser(description="Get chat completion with user prompt")
       parser.add_argument("prompt", type=str, help="The user prompt to complete")
       args = parser.parse_args()

       client = Client()
       response = client.chat.completions.create(
           model="gpt-3.5-turbo", # Use the model you want
           messages=[{"role": "user", "content": args.prompt}]
       )
       print(response.choices[0].message.content)


     if __name__ == "__main__":
       main()

     ````
     Replace `model="gpt-3.5-turbo"` with the model you want to use.

4. **Execute the Script:**
   - Run the script by `gpt4free_python.py "Here your prompt"`
