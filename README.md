## Application Deployment & VIP CLI
 Deployments on WordPress VIP are fully automated and depend on the code merge in the respective branch. Deployment starts when updates pushed to an environment’s repository were detected.
### Deployment is divided into 3 steps:
###   Prepare

        . Detect merge event to ‘develop’,  'preprod' or 'production' branch.
        . Build queue.
        . Initializing build environment.
        . Cloning git repository.

 ###   Build

        . Build starts.
        . Run all the scripts defined in package.json 
        . Build complete successfully (exit with 0).

###   Deployment

        . Deployment starts.
        . The application deployed successfully.   

VIP uses the dependencies and scripts defined in package.json to install, build, and start an application. Make sure all necessary packages needed for an application to run are publicly accessible and are added as dependencies and not devDependencies.
        
 Only production dependencies are installed using the command:
 
             1. npm install --production
               

The build script allows an app to be compiled or perform any necessary tasks before being started. Even if an app does not require a build step, it is still expected that this script to be present. Use "build": "echo 'No build'" or equivalent to fulfil this requirement. The build script must complete successfully (exit with 0) using the command.


              1. npm run build
              

After a successful build, VIP will start an app using the start script. Not all frameworks supply a start script, so an app may need to define one manually using the command.


              1. npm start
              
### Reference Documents:

  [Deployments](https://docs.wpvip.com/technical-references/vip-dashboard/deployments-panel/)
              
  [Node.js on VIP](https://docs.wpvip.com/technical-references/node-js/#h-exposing-a-health-check-endpoint)
              
## Manage or set the environment variables:

   We can set the environment variables using VIP-CLI. To install VIP-CLI on local machine follow the steps given in VIP-CLI document. Once the        [VPI CLI](https://docs.wpvip.com/technical-references/vip-cli/installing-vip-cli/) is install we can use following commands to set and manage the environment variable.
     
             vip app list
            
             e.g. #$ vip app list
             ┌──────┬───────────────────┬─────────────────────────────┐
             │ id   │ name              │ repo                        │
             ├──────┼───────────────────┼─────────────────────────────┤
             │ 6958 │ node-presidio-gov │ wpcomvip/node-presidio-gov  │
             ├──────┼───────────────────┼─────────────────────────────┤
             │ 6767 │ wpvip-presidio    │ wpcomvip/wpvip-presidio-gov │
             └──────┴───────────────────┴─────────────────────────────┘
       
             vip app list command will provide the list & details of all applications.

             
             vip @{application_name}.{environment} config envvar get-all 
             e.g. #$ vip @node-presidio-gov.develop config envvar get-all
             ┌────────────────────────────────┬───────────────────────────────────────────────┐
             │ name                           │ value                                         │
             ├────────────────────────────────┼───────────────────────────────────────────────┤
             │ NEXT_PUBLIC_WORDPRESS_ENDPOINT │ https://wpvip-presidio-gov-develop.go-vip.net │
             ├────────────────────────────────┼───────────────────────────────────────────────┤
             │ NEXT_PUBLIC_SERVER_URL         │ https://node-presidio-gov-develop.go-vip.net  │
             └────────────────────────────────┴───────────────────────────────────────────────┘
             
             vip @{application_name}.{environment} config envvar get-all : gives the list of all previously set 
             environment variables.

       
             vip @{application_name}.{environment} config envvar set {variable_name} :To add or update the environment
             variables 
             

             e.g. #$ vip @node-presidio-gov.develop config envvar set NEXT_PUBLIC_SERVER_URL 
             For multiline input, use the --from-file option.

            ? Enter the value for NEXT_PUBLIC_SERVER_URL: https://node-presidio-gov-develop.go-vip.net
            ✔ Please confirm the input value above (y/N) · true
            Successfully set environment variable "NEXT_PUBLIC_SERVER_URL"
            Important: Updates to environment variables will not be available until the application’s next deploy.
            
            
            
For more details follow the instructions or guidelines provided by WordPress VIP
           
 ### Reference Documents:
        
   <img src="https://user-images.githubusercontent.com/109987485/229742289-545372ea-a297-4700-a60d-b89563dfc5ef.png" width="18" height="18">[Manage Environmental Varaible](https://docs.wpvip.com/how-tos/manage-environment-variables/#managing-environment-variables-with-vip-cli)
  
   <img src="https://user-images.githubusercontent.com/109987485/229742289-545372ea-a297-4700-a60d-b89563dfc5ef.png" width="18" height="18">[VIP Config Envvar Set](https://docs.wpvip.com/vip/config/envvar/set/)
  
  <img src="https://user-images.githubusercontent.com/109987485/229742289-545372ea-a297-4700-a60d-b89563dfc5ef.png" width="18" height="18">[VIP Config Envvar list](https://docs.wpvip.com/vip/config/envvar/list/)
       
       
       
              
              
              
              
              
              
              
              
              
              
              
              
              
              
              
              
              
              
    
     
