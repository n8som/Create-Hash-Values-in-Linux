# Create-Hash-Values-in-Linux

<h2>Activity overview</h2>

As a security analyst, I’ll need to implement security controls to protect organizations against a range of threats.

That’s where hashing comes in. Previously, I learned that a hash function is an algorithm that produces a code that can’t be decrypted. Hash functions are used to uniquely identify the contents of a file so that I can check whether it has been modified. This code provides a unique identifier known as a hash value or digest.

For example, a malicious program may mimic an original program. If one code line is different from the original program, it produces a different hash value. Security teams can then identify the malicious program and work to mitigate the risk.

Many tools are available to compare hashes for various scenarios. But for a security analyst it’s important to know how to manually compare hashes.

In this lab activity, I’ll create hash values for two files and use Linux commands to manually examine the differences.

<h2>Scenario</h2>

In this scenario, we need to investigate whether two files are identical or different.

Here’s how I'll do this task: First, I’ll display the contents of two files and create hashes for each file. Next, I’ll examine the hashes and compare them.

<h2>Task 1. Generate hashes for files</h2>

The lab starts in the home directory, /home/analyst, as the current working directory. This directory contains two files file1.txt and file2.txt, which contain different data.

In this task, I need to display the contents of each of these files. I’ll then generate a hash value for each of these files and send the values to new files, which I’ll use to examine the differences in these values later.

1. Use the ```ls``` command to list the contents of the directory.

Two files, file1.txt and file2.txt, are listed.

2. Use the ```cat``` command to display the contents of the file1.txt file:

```cat file1.txt```

3. Use the ```cat``` command to display the contents of the file2.txt file:

```cat file2.txt```

4. Review the output of the two file contents:

![image](https://github.com/n8som/Create-Hash-Values-in-Linux/assets/110139109/424398d7-9343-4e56-87ed-5ba2b538649e)

The contents of the two files appear identical when using this command.

Although the contents of both files appear identical when I use the ```cat``` command, I need to generate the hash for each file to determine if the files are actually different.

5. Use the ```sha256sum``` command to generate the hash of the file1.txt file:

```sha256sum file1.txt```

I now need to follow the same step for the file2.txt file.

6. Use the ```sha256sum``` command to generate the hash of the file2.txt file:

```sha256sum file2.txt```

Review the generated hashes of the contents of the two files:

![image](https://github.com/n8som/Create-Hash-Values-in-Linux/assets/110139109/08bce119-2a04-4393-87aa-d46a3559fcaf)

They don’t produce the same generated hash value.

<h2>Task 2. Compare hashes</h2>

In this task, I’ll write the hashes to two separate files and then compare them to find the difference.

1. Use the ```sha256sum``` command to generate the hash of the file1.txt file, and send the output to a new file called file1hash:

```sha256sum file1.txt >> file1hash```

I now need to complete the same step for the file2.txt file.

2. Use the ```sha256sum``` command to generate the hash of the file2.txt file, and send the output to a new file called file2hash:

```sha256sum file2.txt >> file2hash```

Now, I should have two hashes written to separate files. The first hash was written to the file1hash file, and the second hash was written to the file2hash file.

I can manually display and compare the differences.

3. Use the ```cat``` command to display the hash values in the file1hash and file2hash files.

4. Inspect the output and note the difference in the hash values.

![image](https://github.com/n8som/Create-Hash-Values-in-Linux/assets/110139109/f0a262a1-bfe6-420c-bdbf-1b1dbdf93a8e)

Note: Although the content in file1.txt and file2.txt previously appeared identical, the hashes written to the file1hash and file2hash files are completely different.

Now, I can use the ```cmp``` command to compare the two files byte by byte. If a difference is found, the command reports the byte and line number where the first difference is found.

5. Use the ```cmp``` command to highlight the differences in the file1hash and file2hash files:

```cmp file1hash file2hash```

6. Review the output, which reports the first difference between the two files:

![image](https://github.com/n8som/Create-Hash-Values-in-Linux/assets/110139109/d1a4115c-81b1-4880-a484-7d08fd1ef433)

Note: The output of the ```cmp``` command indicates that the hashes differ at the first character in the first line.

Based on the hash values, file1.txt is different from file2.txt

<h2>Conclusion</h2>

I practiced how to

- compute hashes using ```sha256sum```,
- display hashes using the ```cat``` command, and
- compare hashes using the ```cmp``` command.

These are valuable tools I can use to validate data integrity as I contribute to the control of my organization’s security.
