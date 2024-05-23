# Guide: Running from Python

## Create a Virtual Environment
1. **Create a Python Virtual Environment in order to then install the required libraries:**

```
python -m venv gpt4free
source gpt4free/bin/activate
pip install -U g4f[all]
```

## Install the required 
2. **Install using PyPI package:**
```
pip install -U g4f[all]
```
   - How do I install only parts or do disable parts?
   Use partial requirements: [/docs/requirements](https://github.com/pcastagnaro/gpt4free/blob/main/docs/requirements.md)

## Single prompt via CLI parameter

This tutorial will walk you through the process of using `gpt4free` from Python sending a single prompt via parameter in the command line.

1. **Install Pydroid from the Google Play Store:**
   - Navigate to the Google Play Store and search for "Pydroid 3 - IDE for Python 3" or use the following link: [Pydroid 3 - IDE for Python 3](https://play.google.com/store/apps/details/Pydroid_3_IDE_for_Python_3).

2. **Install the Pydroid Repository Plugin:**
   - To enhance functionality, install the Pydroid repository plugin. Find it on the Google Play Store or use this link: [Pydroid Repository Plugin](https://play.google.com/store/apps/details?id=ru.iiec.pydroid3.quickinstallrepo).

3. **Adjust App Settings:**
   - In the app settings for Pydroid, disable power-saving mode and ensure that the option to pause when not in use is also disabled. This ensures uninterrupted operation of your Python scripts.

4. **Install Required Packages:**
   - Open Pip within the Pydroid app and install these necessary packages:
     ```
      g4f flask pillow beautifulsoup4
     ```

5. **Create a New Python Script:**
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

     ```
     Replace `model="gpt-3.5-turbo"` with the model you want to use.

6. **Execute the Script:**
   - Run the script by `gpt4free_python.py "Here your prompt"`
