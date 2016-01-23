FROM suchja/wine
MAINTAINER supermomonga

USER root
RUN apt-get update \
    && apt-get install -y p7zip-full
COPY waitonprocess.sh /scripts/
RUN chmod +x /scripts/waitonprocess.sh

USER xclient
RUN wine wineboot --init \
    && /scripts/waitonprocess.sh wineserver

# RUN curl -sL https://ci.appveyor.com/api/buildjobs/jjaj5u12rkvn8j78/artifacts/Roswell-x86_64.zip -o roswell.zip \
#     && unzip roswell.zip \
#     && rm roswell.zip

RUN curl -sL https://ci.appveyor.com/api/buildjobs/0h3edjy1uajwqhwl/artifacts/Roswell-i686.zip -o roswell.zip \
    && unzip roswell.zip \
    && rm roswell.zip

WORKDIR /home/xclient/roswell

RUN mkdir -p ~/.wine/drive_c/users/xclient/.roswell/archives \
    && curl http://netix.dl.sourceforge.net/project/sbcl/sbcl/1.3.1/sbcl-1.3.1-x86-windows-binary.msi -o ~/.wine/drive_c/users/xclient/.roswell/archives/sbcl-bin-1.3.1-x86-windows.msi

RUN cp ~/.wine/drive_c/users/xclient/.roswell/archives/sbcl-bin-1.3.1-x86-windows.msi ./sbcl-bin-1.3.1-x86-windows.msi \
    && 7z x sbcl-bin-1.3.1-x86-windows.msi -osbcl \
    && rm sbcl-bin-1.3.1-x86-windows.msi

RUN wine ros version \
    && /scripts/waitonprocess.sh wineserver

RUN mkdir -p ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/bin \
    && mkdir -p ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib \
    && cp ./sbcl/sbcl.exe ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/bin/ \
    && cp ./sbcl/sbcl.core ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/ \
    && cp ./sbcl/sbcl.core ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/ \
    && cp ./sbcl/File_obj_sbcl.home_contrib_asdf.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/asdf.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.aclrepl.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-aclrepl.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.aclrepl.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-aclrepl.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.bsd.sockets.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-bsd-sockets.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.bsd.sockets.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-bsd-sockets.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.cltl2.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-cltl2.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.cltl2.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-cltl2.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.concurrency.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-concurrency.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.concurrency.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-concurrency.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.cover.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-cover.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.cover.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-cover.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.executable.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-executable.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.executable.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-executable.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.gmp.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-gmp.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.gmp.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-gmp.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.grovel.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-grovel.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.grovel.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-grovel.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.introspect.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-introspect.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.introspect.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-introspect.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.md5.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-md5.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.md5.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-md5.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.mpfr.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-mpfr.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.mpfr.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-mpfr.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.posix.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-posix.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.posix.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-posix.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.queue.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-queue.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.queue.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-queue.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.rotate.byte.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-rotate-byte.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.rotate.byte.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-rotate-byte.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.rt.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-rt.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.rt.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-rt.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.simple.streams.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-simple-streams.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.simple.streams.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-simple-streams.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.sprof.asd ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-sprof.asd \
    && cp ./sbcl/File_obj_sbcl.home_contrib_sb.sprof.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/sb-sprof.fasl \
    && cp ./sbcl/File_obj_sbcl.home_contrib_uiop.fasl ~/.wine/drive_c/users/xclient/.roswell/impls/x86/windows/sbcl-bin/1.3.1/lib/sbcl/contrib/uiop.fasl \
    && echo "sbcl-bin.version	0	1.3.1\ndefault.lisp	0	sbcl-bin" > ~/.wine/drive_c/users/xclient/.roswell/config

RUN wine ros setup -v \
    && /scripts/waitonprocess.sh wineserver

VOLUME /app
WORKDIR /app

ENTRYPOINT ["/usr/bin/wine", "/home/xclient/roswell/ros"]
CMD ["--help"]
