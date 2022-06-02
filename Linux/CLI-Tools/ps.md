- # `ps`

  ps returns a list of running processes based on a scope set by the arguments provided to the program.

  - `ps <no args>` will return only the processes attached to the current session
  - `ps a` shows all processes belonging to the current user
  - `ps aux` shows all processes running on the machine

  Examples:

  - This is a useful way to get information about a running process: <br> `ps aux | grep <program name>`
  - Return all the process owned be a specific user: <br> `ps aux | grep $USER`
  - This does the same as above but without the pipe or grep: <br> `ps -f -U $USER`
  - Sort processes by memory use: <br> `ps aux --sort size`