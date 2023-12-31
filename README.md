<h1>Update a file through Python Algorithm</h1>

<br>

<h2>Description: </h2>

In this project, I will be explaining a step-by-step process about how I was able to open a file, read the contents within the file, write contents within the file, and create an algorithm that can update a file using Python.

<h2>Scenario</h2>

I am a security professional working at a health care company. My job is to regularly update a file that identifies the employees who can access restricted content.
The contents of the file are based on who is working with personal patient records. Employees are restricted access based on their IP address.
There is an `allow list` of IP addresses permitted to sign into the restricted subnetwork. There's also a `remove list` that identifies which employees I must remove from this `allow list`. 
I created an algorithm to automate updating the `"allow_list.txt"` file and remove these IP addresses that should no longer have access.

<br>

<h1>Walkthrough: </h1>


<h2>Step 1: Open the file that contains the allow list</h2>
<p>
  
  For the first part of the algorithm, I opened the `allow_list.txt` file. First, I assigned this file name as a string to the `import_file` variable:

  ```python
  # Create a variable 'import_file' which is assigned to the file location of the allowed list of users' IP addresses.
  import_file = "/home/kali/allow_list.txt"

  # A list of IP addresses that are no longer allowed to access restricted information. 
  remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

  ```

  Then, I used a `with` statement to open the file:

  ```python
  # Build `with` statement to read in the initial contents of the file
  with open(import_file, "r") as file:
  ```
</p>

The `with` statement is used with the `.open()` function in read mode so that it can open the `allow_list.txt` file and read the contents inside. There are two parameters that are happening inside the `.open()` function. One is the `import_file`, which identifies
the file to import, and then the second indicates what type of mode I want to do with the file. In this case, `"r"` means I want to read the file. The code also uses the keyword `as` which assign a variable named `file`. `file` stores the output
of the `.open()` function while I work within the `with` statement.

<p>
  
</p>

<br>
<h2>Step 2: Read the file contents</h2>

<p>
  
  In order to read the file contents, I used the `.read()` method to convert it into a string.

  ```python

  import_file = "/home/kali/allow_list.txt"

  with open(import_file, "r") as file:
  
    # Use `.read()` to read the important file and store it in a variable named `ip_addresses`
    ip_addresses = file.read()

  print(ip_addresses)

  ```

I am using the `.read()` function which is used in the body of the `with` statement. The `.read()` method converts the file into a string and allows me to read it. I applied the `.read()` method to the file variable
identified in the `with` statement. Then, I assigned the string output of this method to the variable `ip_addresses`.

Furthermore, this code reads the contents of the `"allow_list.txt` file into a string format that allows me to later use the string to organize and extract data in my Python program. Here's the output of what it is when I read the file.

```python
# Output for reading allow_list.txt
192.168.25.60
192.168.205.12
192.168.97.225
192.168.6.9
192.168.52.90
192.168.158.170
192.168.90.124
192.168.186.176
192.168.133.188
192.168.203.198
192.168.201.40
192.168.218.219
192.168.52.37
192.168.156.224
192.168.60.153
192.168.58.57
192.168.69.116
```

</p>

<br> 

<h2>Step 3: Convert the string into a list</h2>
<p>
  
  In order to remove individual IP addresses from the `allow list`, I need it to be in list format. Therefore, I next used the `.split()` method to convert the `ip_addresses` string into a list:

  ```python

  # Create a variable 'import_file' which is assigned to the file location of the allowed list of users' IP addresses.
  import_file = "/home/kali/allow_list.txt"

  # A list of IP addresses that are no longer allowed to access restricted information. 
  remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]
  
  # Build `with` statement to read in the initial contents of the file
  
  with open(import_file, "r") as file:
  
      # Use `.read()` to read the imported file and store it in a variable named `ip_addresses`
  
      ip_addresses = file.read()
  
  # Use `.split()` to convert `ip_addresses` from a string to a list
  
  ip_addresses = ip_addresses.split()
  
  # Display `ip_addresses`
  
  print(ip_addresses)
  
  ```

  The `.split()` function is called by appending it to a string variable. It works by converting the
  contents of a string to a list. The purpose of splitting `ip_addresses` into a list is to make it
  easier to remove IP addresses from the allow list. By default, the `.split()` function splits the
  text by whitespace into list elements. In this algorithm, the `.split()` function takes the data
  stored in the variable `ip_addresses`, which is a string of IP addresses that are each
  separated by a whitespace, and it converts this string into a list of IP addresses. To store this
  list, I reassigned it back to the variable `ip_addresses`.

  Here's what the output will be like when I convert a string into a list.

  ```python
  # Output

  ['192.168.25.60', '192.168.205.12', '192.168.97.225', '192.168.6.9', '192.168.52.90', '192.168.158.170', '192.168.90.124', '192.168.186.176', '192.168.133.188',
  '192.168.203.198', '192.168.201.40', '192.168.218.219', '192.168.52.37', '192.168.156.224', '192.168.60.153', '192.168.58.57', '192.168.69.116']

  ```
</p>

<br> 

<h2>Step 4: Iterate through the remove list</h2>

<p>

  The next step for me to do is to iterate through the IP addresses that are elements in the `remove_list`. To do this, I incorporated a `for` loop:

  ```python
  # Build iterative statement
  # Name loop variable `element`
  # Loop through `remove_list`

  for element in remove_list:
  
  ```

  The `for` loop in Python repeats code for a specified sequence. The overall purpose of the `for` loop in a Python algorithm like this is to apply specific code statements to all elements in a sequence. The keyword `element` will iterate through each of the ip_addresses `in` the `remove_list`.
</p>

<br>

<h2>Step 5: Remove IP addresses that are on the remove list </h2>

<p>
  
  In this step, I will create an `if` statement inside the `for` loop of the `remove_list`, which will check and see if the remove list has any matching pairs with the `allow_list`. If it does then it will remove those IP addresses with the `.remove()` method.
  
  . This will check if there are any `ip_addreses` from the `allow list` that match with the `remove_list`. If it does match, I will use the `.remove()` method which will remove any duplicate IP addresses.

</p>

  ```python
  for element in remove_list:
    
    # Create a conditional statement to evaluate if `element` is in `ip_addresses`

    if element in ip_addresses:
        
        ip_addresses.remove(element)


  # Display `ip_addresses`
  
  print(ip_addresses)
  ```

  Here's what the output looks like:

  ```python
  # List of IP addresses that need to be removed
  192.168.97.225
  192.168.158.170
  192.168.201.40
  192.168.58.57

  # List of IP addresses that are in allow_list and have been removed from the `remove_list`.
  ['192.168.25.60', '192.168.205.12', '192.168.6.9', '192.168.52.90', '192.168.90.124', '192.168.186.176', '192.168.133.188',
  '192.168.203.198', '192.168.218.219', '192.168.52.37', '192.168.156.224', '192.168.60.153', '192.168.69.116']

  ```

<br>

<h2>Step 6: Update the file with the revised list of IP addresses</h2>

<p>

  As a final step in my algorithm, I needed to update the allow list file with the revisited list of IP addresses. To do so, I first needed to convert the list back into a string. I used the `.join()` method for this.


  ```python
  # Convert `ip_addresses` back to a string so that it can be written into the text file

  ip_addresses = "\n".join(ip_addresses)

  ```

  Now it should return back into a column that lists each IP address as before, but revised.

  ```python
  192.168.25.60
  192.168.205.12
  192.168.6.9
  192.168.52.90
  192.168.90.124
  192.168.186.176
  192.168.133.188
  192.168.203.198
  192.168.218.219
  192.168.52.37
  192.168.156.224
  192.168.60.153
  192.168.69.116
  ```

  The `.join()` method combines all items in an iterable into a string. The `.join()` method is
  applied to a string containing characters that will separate the elements in the iterable once
  joined into a string. In this algorithm, I used the `.join()` method to create a string from the
  list `ip_addresses` so that I could pass it in as an argument to the `.write()` method when
  writing to the file `"allow_list.txt"`. I used the string `("\n")` as the separator to instruct
  Python to place each element on a new line.

  Here's where I update the file using the `.write()` method which will update this file:

  ```python
  # Build `with` statement to rewrite the original file

  with open(import_file, "w") as file:

    # Rewrite the file, replacing its contents with `ip_addresses`

    file.write(ip_addresses)
  ```

   This will make the file `allow_list.txt` into a newly reformed list of IP addresses that I have just overwritten with Python.
</p>

<br>
<h2>Step 7: Finalize code and create a function </h2>

<p>
  
  Now this is where I bring all the steps together into one function called, `update_file`. This function will be passed by two parameters: `import_file` and `remove_list`

  ```python
  # Create a variable 'import_file' which is assigned to the file location of the allowed list of users' IP addresses.
import_file = "/home/kali/allow_list.txt"

  # A list of IP addresses that are no longer allowed to access restricted information. 
  remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

  def update_file(import_file, remove_list):

    # Build `with` statement to read in the initial contents of the file

    with open(import_file, "r") as file:

        # Use `.read()` to read the imported file and store it in a variable named `ip_addresses`

        ip_addresses = file.read()

    # Use `.split()` to convert `ip_addresses` from a string to a list

    ip_addresses = ip_addresses.split()

    # Build iterative statement
    # Name loop variable `element`
    # Loop through `remove_list`

    for element in remove_list:
    
        # Create a conditional statement to evaluate if `element` is in `ip_addresses`

        if element in ip_addresses:

            # use the `.remove()` method to remove
            # elements from `ip_addresses`

            ip_addresses.remove(element)

    # Convert `ip_addresses` back to a string so that it can be written into the text file

    ip_addresses = "\n".join(ip_addresses)

    # Build `with` statement to rewrite the original file

    with open(import_file, "w") as file:

        # Rewrite the file, replacing its contents with `ip_addresses`

        file.write(ip_addresses)

    # Call `update_file()` and pass in "allow_list.txt" and a list of IP addresses to be removed
    
    update_file(import_file, remove_list)
    
    # Build `with` statement to read in the updated file
    
    with open("allow_list.txt", "r") as file:
    
        # Read in the updated file and store the contents in `text`
    
        text = file.read()
    
    # Display the contents of `text`
    
    print(text)
  ```
</p>

<br>

<h1>Summary</h1>

From the `"allow_list.txt"` file of authorized IP addresses, I developed an algorithm that eliminates IP addresses listed in a `remove_list` variable. 
This procedure comprised opening the file, reading the string it was converted into, and then transforming the list into the variable `ip_addresses`. 
I next went through the IP addresses in `remove_list` iteratively. I determined each time whether the entry was a part of the `ip_addresses` list. 
If so, I used the `.remove()` method to take the entry out of ip_addresses. Then, in order to replace the IP address list in the "allow_list.txt" file with the updated list, 
I used the `.join()` technique to turn the IP addresses back into strings.
