# Windows-Scheduled-Task-Parser
Windows Scheduled Task Parser - DFIR's tool parsing XML-based Windows Scheduled Tasks. This tool was created for all DFIR analysts that need to parse XML-based Windows Task that you can find in C:\Windows\System32\Tasks. Usually as a forensics analyst you will collect the most important data from the live machine and then analysis it on your lab machine. During my work I discovered that manuall attempt to parse these artifacts consumes a lot of time and it's very inefficent, so I decided to create GUI tool that will parse all task at once and give me the ability to easily analyze each of them in a very convient manner. 

# How does it work?
First of all, if you want to understand how this tool works, you need to understand the structure of Windows Scheduled Task. The entire structure is exmplained by Microsoft under this link: https://docs.microsoft.com/en-us/windows/win32/taskschd/task-scheduler-schema. And this is the documentaion that I was used creating that tool. 

# Attribution
"Icon made by Freepik from www.flaticon.com"

![alt text](https://github.com/gajos112/Windows-Scheduled-Task-Parser/blob/main/Images/Actions.png?raw=true)
