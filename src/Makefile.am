MAINTAINERCLEANFILES = Makefile.in config.h config.h.in
DISTCLEANFILES = Makefile
CLEANFILES = core.* *~ 
AM_CFLAGS = -Wall -fpie
AM_LDFLAGS = -pie
sexec_CPPFLAGS = -DSYSCONFDIR=\"$(sysconfdir)\" -DLOCALSTATEDIR=\"$(localstatedir)\" -DLIBEXECDIR=\"$(libexecdir)\" $(SINGULARITY_DEFINES) $(NO_SETNS)
sexec_nosuid_CPPFLAGS = -DSINGULARITY_NOSUID=1 -DSYSCONFDIR=\"$(sysconfdir)\" -DLOCALSTATEDIR=\"$(localstatedir)\" -DLIBEXECDIR=\"$(libexecdir)\" $(SINGULARITY_DEFINES) $(NO_SETNS)
bootstrap_CPPFLAGS = -DLIBEXECDIR=\"$(libexecdir)\"
ftrace_CPPFLAGS = -DARCH_$(SINGULARITY_ARCH)

dist_suidPROGRAM_INSTALL = ${INSTALL} -m 640

install-exec-hook:
	@if test `id -ru` = "0"; then \
		echo " /bin/chown root:root $(DESTDIR)$(libexecdir)/singularity/sexec"; \
		/bin/chown root:root $(DESTDIR)$(libexecdir)/singularity/sexec; \
		echo " /bin/chmod 4755 $(DESTDIR)$(libexecdir)/singularity/sexec"; \
		/bin/chmod 4755 $(DESTDIR)$(libexecdir)/singularity/sexec; \
	fi

bindir = $(libexecdir)/singularity
bin_PROGRAMS = sexec image-create image-expand image-mount image-bind sexec_nosuid

ftrace_SOURCES = ftrace.c file.c util.c message.c
ftype_SOURCES = ftype.c util.c file.c message.c
sexec_SOURCES = sexec.c util.c loop-control.c mounts.c container_files.c file.c image.c config_parser.c container_actions.c privilege.c message.c namespaces.c signal_handlers.c
sexec_nosuid_SOURCES = sexec.c util.c loop-control.c mounts.c container_files.c file.c image.c config_parser.c container_actions.c privilege.c message.c namespaces.c signal_handlers.c
image_create_SOURCES = image-create.c file.c util.c image.c message.c privilege.c
image_expand_SOURCES = image-expand.c file.c util.c image.c message.c privilege.c
image_mount_SOURCES = image-mount.c util.c loop-control.c mounts.c file.c image.c message.c config_parser.c privilege.c
image_bind_SOURCES = image-bind.c util.c loop-control.c mounts.c file.c image.c message.c config_parser.c privilege.c

EXTRA_DIST = config.h config_parser.h container_actions.h file.h image.h loop-control.h mounts.h container_files.h util.h privilege.h message.h namespaces.h signal_handlers.h
