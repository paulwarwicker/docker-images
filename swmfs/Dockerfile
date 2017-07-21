FROM centos:latest
LABEL org.freenas.interactive="false" 		\
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
              \"name\": \"/opt/sw/config\",				\
              \"descr\": \"swmfs configuration directory\"		\
          } 						\
      ]"							\
      org.freenas.settings="[ 					\
          {							\
              \"env\": \"TZ\",					\
              \"descr\": \"smfs container Timezone\",		\
              \"optional\": true				\
          },						\
          {							\
              \"env\": \"SW_MDB_AUTH\",			\
              \"descr\": \"/opt/sw/config/swmfs.auth\",	\
              \"optional\": false				\
          },						\
          {							\
              \"env\": \"SW_MDB_PATHS\",			\
              \"descr\": \"/opt/sw/config/swmfs.paths\",	\
              \"optional\": false				\
          },						\
          {							\
              \"env\": \"SW_MDB_UDP_PORTS\",			\
              \"descr\": \"30000,30100\",	\
              \"optional\": false				\
          } 							\
      ]"

ADD swmfs-5.22.9-1.x86_64.rpm /tmp
RUN rpm -i /tmp/swmfs-5.22.9-1.x86_64.rpm
#RUN sed -i 's/\$auth //g' /etc/init.d/smallworld_GIS
RUN sed -i 's/\$auth/-nodaemon/g' /etc/init.d/smallworld_GIS
RUN sed -i 's/30000,30100/\$SW_MDB_UDP_PORTS/g' /etc/init.d/smallworld_GIS

CMD ["/etc/init.d/smallworld_GIS","start"]