#
# k8s-cms
# Resource Usage Container
# 

FROM mrzzy/cms-base

# copy config
COPY config /cms/config

# run resource usage
EXPOSE 28000
CMD ["/cms/scripts/cmsResourceService", "0"]
