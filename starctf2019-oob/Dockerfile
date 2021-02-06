FROM mrh929/v8_source:latest

EXPOSE 8000

WORKDIR /root/v8

COPY oob.diff .

RUN git reset --hard 6dc88c191f5ecc5389dc26efa3ca0907faef3598 \
	&& git apply ./oob.diff \
	&& gclient sync \
	&& ./tools/dev/v8gen.py x64.release \
	&& ninja -C ./out.gn/x64.release \
	&& ./tools/dev/v8gen.py x64.debug \
	&& ninja -C ./out.gn/x64.debug \
	&& tar cvf ./out.gn/debug.tar ./out.gn/x64.debug \
	&& tar cvf ./out.gn/release.tar ./out.gn/x64.release \
	&& mv ./out.gn /root \
	&& rm -rf /root/v8 /root/depot_tools /root/out.gn/x64.*
	
WORKDIR /root/out.gn


CMD ["python2", "-m", "SimpleHTTPServer", "8000"]