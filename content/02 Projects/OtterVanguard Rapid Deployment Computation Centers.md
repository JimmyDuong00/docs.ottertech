This post is part of the OtterVanguard series .

## Overview
In order to  Rapid Response Centers, OtterVanguard opted to use Terraform to be able to rapidly deploy infrastructure nearest to the affected region. By utilizing AWS's broad regions, we are able to deploy tracking resources in a matter of minutes to allow for response member tracking. 

- **AWS IoT Core**: Tracks the location of first responders.
- **AWS Lambda**: Processes location data and triggers alerts when necessary.
- **AWS SNS**: Sends real-time SMS notifications to responders if they enter a hazardous area.
- **AWS Location Service**: Tracks and visualizes responder movements on a map.

### Benefits:

- **Real-time Insights**: Command centers have live visibility of responder positions.
- **Safety Alerts**: Automated notifications help keep responders out of danger zones.
- **Scalable Solution**: The system scales up as needed during larger disasters without manual intervention.