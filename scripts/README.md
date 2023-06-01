# scripts

Extending kubectl

## How to use:

1. Make executable file "kubeplugin"
  ```
   sudo chmod +x ./kubeplugin
  ```

2. If you want to run from anywhere, place it in your PATH:
  ```
  sudo mv ./kubeplugin /usr/local/bin
  ```

3. Now you can run:
 
  kubeplugin [resource_type] [namespace]

   example:
  ```
   ./kubeplugin pod kube-system
  ```
