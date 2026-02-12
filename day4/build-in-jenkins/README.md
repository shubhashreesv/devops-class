### Summary:

- This Project demonstrates basic CI automation.
- This workflow helps understand automated build execution and continuous integration basics.

1. `Login` Jenkins
    
    (Authentication required)
    
2. Create a new CI/CD Workflow: 
    - `Select Add Item from side panel`
    - Each item  = one automated process
3. `Add new item > Item Name > Free Style Project` 
4.  `Create Item`
5. Configure Automation steps
    - Inside `Item’s Configure > Build Steps > Execute Shell >` Type the below
        
        ```docker
        echo "sample run" > HelloWorld.txt
        ```
        
    - The above command prints text and redirects output to HelloWorld.txt (created)
6. Now Apply & Save
7. Now in `Side Panel > Build Now` 
    - Now, Jenkins allocates workspace
    - Runs shell script
    - Executes command
    - Generate Output
8. Check Console Output inside Builds
    - Jenkins holds logs of every step
    - Shows command execution details
9. See your Build Status
    - Jenkins marks build:
        - SUCCESS → if script runs properly
        - FAILURE → if error occurs

![jenkins-console-output.png]

Note the line workspace: copy `/var/lib/jenkins/workspace/HelloWorld`

Check below image

![local-vm-output.png]



