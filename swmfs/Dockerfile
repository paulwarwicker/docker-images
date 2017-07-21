FROM centos:latest
LABEL org.freenas.interactive="true" 		\
      org.freenas.version="5.22.9"		\
      org.freenas.upgradeable="false"		\
      org.freenas.expose-ports-at-host="true"	\
      org.freenas.autostart="true"		\
      org.freenas.port-mappings="1590:1590/tcp,30000:30000/udp,30001:30001/udp,30002:30002/udp"			\
      org.freenas.volumes="[					\
          {							\
              \"name\": \"/data\",				\
              \"descr\": \"Datastore storage space\"		\
          },						\
          {							\
              \"name\": \"/opt/sw/swmfs.auth\",				\
              \"descr\": \"swmfs authorisation config file\"		\
          },						\
          {							\
              \"name\": \"/opt/sw/swmfs.paths\",				\
              \"descr\": \"swmfs path resolution config file\"		\
          }                         \
      ]"							\
      org.freenas.settings="[ 					\
          {							\
              \"env\": \"TZ\",					\
              \"descr\": \"smfs container Timezone\",		\
              \"optional\": true				\
          },							\
          {							\
              \"env\": \"SW_MDB_PATHS\",			\
              \"descr\": \"/opt/sw/swmfs.paths\",	\
              \"optional\": true				\
          } 							\
      ]"
ADD swmfs-5.22.9-1.x86_64.rpm /tmp
RUN rpm -i /tmp/swmfs-5.22.9-1.x86_64.rpm