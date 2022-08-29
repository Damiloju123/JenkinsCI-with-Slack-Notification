Step 1: Install Slack Notification Plug in 

![A](https://user-images.githubusercontent.com/52894481/187309099-d64b7b58-f470-4177-b33d-1e82eb027db3.JPG)

Step 2: Launch Slack and create new workspace profilecicd

![B](https://user-images.githubusercontent.com/52894481/187309195-1f6a3d5c-b4f0-487b-82f6-3467008966a8.JPG)

Step 3: Install Jenkins CI on Slack via Slack App Directory

![C](https://user-images.githubusercontent.com/52894481/187309327-63d1b90b-2818-4794-9334-0667d4251fd4.JPG)

Step 4: Configure Slack Notification on Jenkins 

![D](https://user-images.githubusercontent.com/52894481/187309411-41239c61-fc7a-48df-90d6-001c6d3b752c.JPG)

Step 5: Verify Connection on Slack

![E](https://user-images.githubusercontent.com/52894481/187309485-f40cbca2-b482-4dd7-973f-7fd38fc8ac56.JPG)

Step 6: Create a new pipeline on jenkins and include the below :

- For color status on Slack
def COLOR_MAP = [
    'SUCCESS': 'good', 
    'FAILURE': 'danger',
]

- Sending Message to slack channel
    post {
        always {
            echo 'Slack Notifications.'
            slackSend channel: '#jenkinscicd',
                color: COLOR_MAP[currentBuild.currentResult],
                message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} \n More info at: ${env.BUILD_URL}"
        }
    }
    
Step 7: Build Pipeline 

![h](https://user-images.githubusercontent.com/52894481/187309733-135dc104-c224-4c82-b1b6-08dec64143c7.JPG)

Step 8: Confirm Notification on Slack Workspace

![i](https://user-images.githubusercontent.com/52894481/187309789-e09431b7-b4e6-42b4-a528-e36fdef9e7e8.JPG)
