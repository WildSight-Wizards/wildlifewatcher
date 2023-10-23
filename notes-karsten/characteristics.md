# Architectural Characteristics

Based on the list in Chapter 4 of "Fundamentals of Software Architecture" by Mark Richards, Neal Ford.

## Operational Characteristics

| Characteristics | Assessment |
|-----------------|----------------|
| Availability | 24/7, but non stop not needed |
| Continuity | In case of a deaster, it is tolerable to be offline for a week |
| Performance | Machine Learning, Video manipulation and upload need to be performant, the rest need to be "usable" |
| Recoverability | Data captured need to be able to be restored, as they are not easily reconstructable |
| Reliability/Safety | Lower requirements. No life at risk. Occasional dropouts are tolerable |
| Robustness | Camera is in harsh environment, networks are unstable |
| Scalability | most parts are single user. when we have central storage for videos, this must be scalable |


## Structural Architecture Characteristics

| Characteristics | Assessment |
|-----------------|----------------|
| Configurability | In the field module need to be configurable to hardware level, ML Module needs to be configurable |
| Extensibility | New sensor options or networking option need to be integrable |
| Intstallability | important for the device, also if we may want for server if we like it to be self-hostable |
| Leverage/resuse | unclear |
| Localization | Important as it will be global used and for example school children have not much english knowledge |
| Maintainability | unclear |
| Portability | both mobile platforms, also in future other micro-controllers need to be supported |
| Upgradeability | Important as it is tricky for the hardware |

## Cross Cutting Characteristics

| Characteristics | Assessment |
|-----------------|----------------|
| Accessibility   | nice to have |
| Archivability   | Important for scientific studies, unclear if all videos need to archived |
| Authentication | normal, (prevent misuses of resources) |
| Authorization | normal |
| Legal | no personal data (except account) but the data may be used in court to decide over big infrastructure projects |
| Privacy | normal |
| Security | Videos are not secret, but should not be able to be manipulated, and accounts need to be secure |
| Supportability | this is again important and tricky for then hardware in the field |
| Usability/achievability | Important |

## Special for this use case

| Characteristics | Assessment |
|-----------------|----------------|
| Affordability | non profit, therefore should be cheap. But development work might be done with crowdsourcing |
| Hackability | The project should inspire coders and makers to enhance it. |
| Energy Efficency | Very important for the camera device, normal for other systems |




