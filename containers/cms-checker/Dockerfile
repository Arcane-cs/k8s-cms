#
# k8s-cms
# Health Checker Container
# 

FROM mrzzy/cms-base

# copy config
COPY config /cms/config

# run scoring service
EXPOSE 28500
CMD ["/cms/scripts/cmsChecker", "0"]
