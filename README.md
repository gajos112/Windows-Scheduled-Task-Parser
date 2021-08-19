# Windows-Scheduled-Task-Parser
Windows Scheduled Task Parser - DFIR's tool parsing XML-based Windows Scheduled Tasks. This tool was created for all DFIR analysts that need to parse XML-based Windows Task (you can find them in this location: C:\Windows\System32\Tasks). Usually as forensics analysts we collect the most important data from the live machine and then analyze them on our lab machines. But during my work, I discovered that manual attempt to parse these specific artifacts consumes a lot of time and it's very inefficient, therefore I decided to create a GUI tool that will parse all tasks at once and give me the ability to easily analyze each of them in a very convenient manner.

This is what the current version of the tool looks like, it can change in the future.
![alt text](https://github.com/gajos112/Windows-Scheduled-Task-Parser/blob/main/Images/Windows%20Scheduled%20Task%20Parser.png?raw=true)

```C#
string[] files = Directory.GetFiles(path, "*", SearchOption.AllDirectories);
foreach (var file in files)
  {
    try
    {
      using (FileStream fileStream = new FileStream(file, FileMode.Open, FileAccess.Read))
        {
          using (var fileReader = new BinaryReader(fileStream, new ASCIIEncoding()))
          {
            //FF FE 3C 00 3F 00 78 00 6D 00 6C Magic Header for Windows XML tasks
            //255 254 60 0 63 0 120 0 109 0 108
            byte[] buffer = new byte[10];
            buffer = fileReader.ReadBytes(10);
            
            if (buffer[0] == 255 && buffer[1] == 254 && buffer[2] == 60 && buffer[3] == 0 && buffer[4] == 63 && buffer[5] == 0 && buffer[6] == 120 && buffer[7] == 0 && buffer[8] == 109 && buffer[9] == 0 && buffer[10] == 108)
            {
                <parse>
            }
           }
         }
    }
 }
```

# How does it work?
First of all, if you want to understand how this tool works, you need to understand the structure of Windows Scheduled Task. The entire structure is explained by Microsoft under this link: https://docs.microsoft.com/en-us/windows/win32/taskschd/task-scheduler-schema. And this is the documentaion that I was used creating that tool.

## How can we create a task?
There are two main options that we can create a task. The first option is using a command line tool SCHTASKS, this is the option you'll probably see most often when dealing with security incidents. The second option is to use Windows GUI tool called Task Scheduler (taskschd.msc).



# Attribution
"Icon made by Freepik from www.flaticon.com"

![alt text](https://github.com/gajos112/Windows-Scheduled-Task-Parser/blob/main/Images/Actions.png?raw=true)
