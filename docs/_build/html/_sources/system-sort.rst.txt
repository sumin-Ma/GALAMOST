Memory sorting
==============

.. py:class:: Sort(all_info)

   initializes a memory sort object with system information.
 
   :param AllInfo all_info: The system information
   
   Example::

      sort_method = galamost.Sort(all_info)
      sort_method.setPeriod(300)
      app.add(sort_method)
