AC_PREREQ(2.60)
AC_INIT(nrfd, 0.0)

AC_CONFIG_HEADERS(config.h)

AM_INIT_AUTOMAKE([subdir-objects foreign color-tests silent-rules])

m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])

AM_MAINTAINER_MODE

AC_PREFIX_DEFAULT(/usr/local)

PKG_PROG_PKG_CONFIG

COMPILER_FLAGS

AC_LANG_C

AC_PROG_CC
AC_PROG_CC_PIE
AC_PROG_INSTALL
AC_PROG_MKDIR_P
AC_PROG_LN_S

LT_PREREQ(2.2)
LT_INIT([disable-static])

PKG_CHECK_MODULES(GLIB, glib-2.0 >= 2.52, dummy=no,
				AC_MSG_ERROR(required glib >= 2.52))
AC_SUBST(GLIB_CFLAGS)
AC_SUBST(GLIB_LIBS)

PKG_CHECK_MODULES(GIO_UNIX, gio-2.0 >= 2.48)
AC_SUBST(GIO_UNIX_CFLAGS)
AC_SUBST(GIO_UNIX_LIBS)


PKG_CHECK_MODULES(JSON, json-c,
  [AC_DEFINE([HAVE_JSON],[1],[Use JSON])],
  [AC_MSG_ERROR("json-c missing")])
AC_SUBST(JSON_CFLAGS)
AC_SUBST(JSON_LIBS)

AC_ARG_ENABLE(optimization, AC_HELP_STRING([--disable-optimization],
			[disable code optimization through compiler]), [
	if (test "${enableval}" = "no"); then
		CFLAGS="$CFLAGS -U_FORTIFY_SOURCE -O0"
	fi
])

AC_ARG_ENABLE(debug, AC_HELP_STRING([--enable-debug],
			[enable compiling with debugging information]), [
	if (test "${enableval}" = "yes" &&
				test "${ac_cv_prog_cc_g}" = "yes"); then
		CFLAGS="$CFLAGS -g"
	fi
])

AC_ARG_ENABLE(pie, AC_HELP_STRING([--enable-pie],
			[enable position independent executables flag]), [
	if (test "${enableval}" = "yes" &&
				test "${ac_cv_prog_cc_pie}" = "yes"); then
		CFLAGS="$CFLAGS -fPIE"
		LDFLAGS="$LDFLAGS -pie"
	fi
])

AC_CONFIG_FILES(Makefile)

AC_OUTPUT
