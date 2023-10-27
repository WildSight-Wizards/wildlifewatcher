The wildlife.ai lists several requirements. However, to understand what the implementation of these requirements would look like, it is imperative
to understand if the implementation is manually executed from the mobile client, or on the camera.

# The following are user-initiated, and on the mobile app:

## REQ-001 - Users should be able to communicate with the camera using a mobile app (to set the cameras on/off and adjust settings without opening the cameras) <br />
## REQ-002 - Users should be able to analyse the videos using common camera trap labelling platforms (Wildlife Insights, TrapTagger or Trapper) <br />
## REQ-003 - Users should be able to publish frames from the videos to iNaturalist for experts to help with the identification of the species <br />
## REQ-005 Users should be able to publish the species occurrences to GBIF the Camtrap DP, data exchange format <br />

# The following is user-initiated, but managed in the cloud:

## REQ-004 Users should be able to easily train edge models. using their own labelled videos, and upload the models to the cameras (using third party services like Roboflow, Edge Impulse or TensorFlow Lite) <br />

# The following is initiated on the camera:

## REQ-006 Cameras should be able to process the footage on the device and send a small alert message to the users via LoraWan, 3G or satellite. <br />