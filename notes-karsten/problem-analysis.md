# Requirement Reading

## Notable key words and statements in text
Charity -> low costs, but possibility to crowd-source.

Existing prototype: camera triggered by movement, identifies species *on the device*,
reports observation (which format) *near real time*.

Objective -> efficient species conversation based on real data.

Users: hundreds, partly professional, partly teachers and pupils, global (localisation needed)

Requirement statements:
Communication mobile app with camera to set up and adjust settings.

Analyse videos and label/tah them with 3rdparty platforms:
  can the videos store on these platforms or do we need an own storage?
  
publish frames (images), get feedback from experts.

-> collaboration with different platforms needed.

train own models with videos.

publish occurrences, again to 3rd party services.

send alerts (does it mean the videos itself need not to be sended?)
via 3g, Lorawan or satellite 
-> Lorawan probably not usable for video upload, 3g and satellite might be expensive.

camera hardware: ultra low power microcontroller (512 kb)
  -> is it possible to run AI on this?
combined with a modules for camera and for communication that may be exchanged.  

## Notable in Video

IT was said that often there is no 3g network connection.

