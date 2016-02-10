.. _class_IP:

IP
==

**Inherits:** :ref:`Object<class_object>`

**Inherited By:** :ref:`IP_Unix<class_ip_unix>`

**Category:** Core

Brief Description
-----------------

IP Protocol support functions.

Member Functions
----------------

+------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| :ref:`String<class_string>`  | :ref:`resolve_hostname<class_IP_resolve_hostname>`  **(** :ref:`String<class_string>` host  **)**                       |
+------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| :ref:`int<class_int>`        | :ref:`resolve_hostname_queue_item<class_IP_resolve_hostname_queue_item>`  **(** :ref:`String<class_string>` host  **)** |
+------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| :ref:`int<class_int>`        | :ref:`get_resolve_item_status<class_IP_get_resolve_item_status>`  **(** :ref:`int<class_int>` id  **)** const           |
+------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| :ref:`String<class_string>`  | :ref:`get_resolve_item_address<class_IP_get_resolve_item_address>`  **(** :ref:`int<class_int>` id  **)** const         |
+------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| void                         | :ref:`erase_resolve_item<class_IP_erase_resolve_item>`  **(** :ref:`int<class_int>` id  **)**                           |
+------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| :ref:`Array<class_array>`    | :ref:`get_local_addresses<class_IP_get_local_addresses>`  **(** **)** const                                             |
+------------------------------+-------------------------------------------------------------------------------------------------------------------------+

Numeric Constants
-----------------

- **RESOLVER_STATUS_NONE** = **0**
- **RESOLVER_STATUS_WAITING** = **1**
- **RESOLVER_STATUS_DONE** = **2**
- **RESOLVER_STATUS_ERROR** = **3**
- **RESOLVER_MAX_QUERIES** = **32**
- **RESOLVER_INVALID_ID** = **-1**

Description
-----------

IP contains some support functions for the IPv4 protocol. TCP/IP support is in different classes (see :ref:`TCP_Client<class_tcp_client>`, :ref:`TCP_Server<class_tcp_server>`). IP provides hostname resolution support, both blocking and threaded.

Member Function Description
---------------------------

.. _class_IP_resolve_hostname:

- :ref:`String<class_string>`  **resolve_hostname**  **(** :ref:`String<class_string>` host  **)**

Resolve a given hostname, blocking. Resolved hostname is returned as an IP.

.. _class_IP_resolve_hostname_queue_item:

- :ref:`int<class_int>`  **resolve_hostname_queue_item**  **(** :ref:`String<class_string>` host  **)**

Create a queue item for resolving a given hostname. The queue ID is returned, or RESOLVER_INVALID_ID on error.

.. _class_IP_get_resolve_item_status:

- :ref:`int<class_int>`  **get_resolve_item_status**  **(** :ref:`int<class_int>` id  **)** const

Return the status of hostname queued for resolving, given it's queue ID. Returned status can be any of the RESOLVER_STATUS\_\* enumeration.

.. _class_IP_get_resolve_item_address:

- :ref:`String<class_string>`  **get_resolve_item_address**  **(** :ref:`int<class_int>` id  **)** const

Return a resolved item address, or an empty string if an error happened or resolution didn't happen yet (see :ref:`get_resolve_item_status<class_IP_get_resolve_item_status>`).

.. _class_IP_erase_resolve_item:

- void  **erase_resolve_item**  **(** :ref:`int<class_int>` id  **)**

Erase a queue ID, removing it from the queue if needed. This should be used after a queue is completed to free it and enable more queries to happen.

.. _class_IP_get_local_addresses:

- :ref:`Array<class_array>`  **get_local_addresses**  **(** **)** const

