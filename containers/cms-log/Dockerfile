#
# k8s-cms
# Log Service Container
# 

FROM mrzzy/cms-base

# copy config
COPY config /cms/config

# run log service
EXPOSE 29000
CMD [ "./scripts/cmsLogService", "0" ]
