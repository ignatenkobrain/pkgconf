
libpkgconf `client` module
==========================

The libpkgconf `client` module implements the `pkgconf_client_t` "client" object.
Client objects store all necessary state for libpkgconf allowing for multiple instances to run
in parallel.

Client objects are not thread safe, in other words, a client object should not be shared across
thread boundaries.

.. c:function:: void pkgconf_client_init(pkgconf_client_t *client, pkgconf_error_handler_func_t error_handler)

   Initialise a pkgconf client object.

   :param pkgconf_client_t* client: The client to initialise.
   :param pkgconf_error_handler_func_t error_handler: An optional error handler to use for logging errors.
   :return: nothing

.. c:function:: pkgconf_client_t* pkgconf_client_new(pkgconf_error_handler_func_t error_handler)

   Allocate and initialise a pkgconf client object.

   :param pkgconf_error_handler_func_t error_handler: An optional error handler to use for logging errors.
   :return: A pkgconf client object.
   :rtype: pkgconf_client_t*

.. c:function:: void pkgconf_client_deinit(pkgconf_client_t *client)

   Release resources belonging to a pkgconf client object.

   :param pkgconf_client_t* client: The client to deinitialise.
   :return: nothing

.. c:function:: void pkgconf_client_free(pkgconf_client_t *client)

   Release resources belonging to a pkgconf client object and then free the client object itself.

   :param pkgconf_client_t* client: The client to deinitialise and free.
   :return: nothing

.. c:function:: const char *pkgconf_client_get_sysroot_dir(const pkgconf_client_t *client)

   Retrieves the client's sysroot directory (if any).

   :param pkgconf_client_t* client: The client object being accessed.
   :return: A string containing the sysroot directory or NULL.
   :rtype: const char *

.. c:function:: void pkgconf_client_set_sysroot_dir(pkgconf_client_t *client, const char *sysroot_dir)

   Sets or clears the sysroot directory on a client object.  Any previous sysroot directory setting is
   automatically released if one was previously set.

   Additionally, the global tuple ``$(pc_sysrootdir)`` is set as appropriate based on the new setting.

   :param pkgconf_client_t* client: The client object being modified.
   :param char* sysroot_dir: The sysroot directory to set or NULL to unset.
   :return: nothing

.. c:function:: const char *pkgconf_client_get_buildroot_dir(const pkgconf_client_t *client)

   Retrieves the client's buildroot directory (if any).

   :param pkgconf_client_t* client: The client object being accessed.
   :return: A string containing the buildroot directory or NULL.
   :rtype: const char *

.. c:function:: void pkgconf_client_set_buildroot_dir(pkgconf_client_t *client, const char *buildroot_dir)

   Sets or clears the buildroot directory on a client object.  Any previous buildroot directory setting is
   automatically released if one was previously set.

   Additionally, the global tuple ``$(pc_top_builddir)`` is set as appropriate based on the new setting.

   :param pkgconf_client_t* client: The client object being modified.
   :param char* buildroot_dir: The buildroot directory to set or NULL to unset.
   :return: nothing