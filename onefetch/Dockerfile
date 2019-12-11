# DESCRIPTION:	  Runs onefetch in a container
# AUTHOR:		  Colin Nelson <colin@orthros.dev>
# COMMENTS:
#	This file describes how to build the onefetch application in a container.
#	Onefetch Upstream: https://github.com/o2sh/onefetch
#	Tested on Arch.
# USAGE:
#	# Download onefetch Dockerfile
#	wget https://raw.githubusercontent.com/orthros/dockerfiles/master/onefetch/Dockerfile
#
#	# Build onefetch image
#	docker build -t onefetch .
#
#	docker run -d \
#        -v $(pwd):/target:ro \
#        onefetch -d /target
#

FROM rust:1-slim-stretch as BASE

RUN apt update && \
    apt install --no-install-recommends -y \
	    git && \
	rm -rf /var/lib/apt/lists*

FROM BASE as BUILDER

RUN git clone https://github.com/o2sh/onefetch

WORKDIR onefetch

RUN cargo build --release

FROM BASE as FINAL

COPY --from=BUILDER /onefetch/target/release/onefetch ./bin/onefetch

ENTRYPOINT ["onefetch"]
