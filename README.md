# Application Deployment & VIP CLI
 Deployments on WordPress VIP are fully automated and depend on the code merge in the respective branch. Deployment starts when updates pushed to an environment’s repository were detected.
# Deployment is divided into 3 steps:
# Prepare

        . Detect merge event to ‘develop’,  'preprod' or 'production' branch.
        . Build queue.
        . Initializing build environment.
        . Cloning git repository.

 # Build

        . Build starts.
        . Run all the scripts defined in package.json 
        . Build complete successfully (exit with 0).

# Deployment

        . Deployment starts.
        . The application deployed successfully.   

VIP uses the dependencies and scripts defined in package.json to install, build, and start an application. Make sure all necessary packages needed for an application to run are publicly accessible and are added as dependencies and not devDependencies.
        
 Only production dependencies are installed:
 
             1. npm install --production
               
 The build script allows an app to be compiled or perform any necessary tasks before being started. Even if an app does not require a build step, it is still expected that this script to be present. Use "build": "echo 'No build'" or equivalent to fulfil this requirement. The build script must complete successfully (exit with 0).

              1. npm run build
# After a successful build, VIP will start an app using the start script. Not all frameworks supply a start script, so an app may need to define one manually.
#         1. npm start
# Reference Documents:
     
