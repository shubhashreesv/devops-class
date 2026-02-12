1. Start Jenkins & Login
    
    `sudo systemctl start jenkins`
    
2. Create Multiple Jenkins Jobs (Refer Doc1)
    - Job A → Build Application
    - Job B → Deploy Application
3. Configure Trigger
    - Open Job B > Click Configure > Go to Build Triggers > Select : Build after other projects are built > Enter Job A name
    
    ## 👉 What Happens:
    
    - Job A runs first.
    - If Job A completes successfully:
        - Job B automatically starts.
    
    ![configure-jobA.png]
    
    ![configure-jobB-1.png]
    
    ![configure-jobB-2.png]
    

![jenkins-home.png]

# Upstream vs Downstream

## Upstream:

- The project that runs first and triggers another project.
- Eg: Job A builds code → Triggers deployment
- Thus Job A =  Upstream

## Downstream:

- Project triggered after upstream job completes
- Eg: Deployment job after build
- Thus Job B = Downstream

**Upstream = First job (trigger source)**

**Downstream = Next job (triggered job)**