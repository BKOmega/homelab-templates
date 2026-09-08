# cAdvisor

Container resource metrics with the host filesystem and Docker data mounted read-only.
The unrelated Redis container in the private deployment was not retained because no
cAdvisor setting consumed it.

The mounts and `/dev/kmsg` device expose sensitive host information. Keep the web port on
a trusted address and remove mounts for metrics you do not need.
