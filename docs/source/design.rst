Design-time considerations
==========================

.. note::
    Try to make your robot assembly mostly based on sub pre-assembled components (avoid to have a lot of
    constraints that are not relevant for the export). In this main assembly, do not use features
    such as sub-assemblies network.

Specifying degrees of freedom
-----------------------------

* Degree of freedoms should be slider, cylindrical or revolute mate connectors named ``dof_something``, where
  ``something`` will be used to name the joint in the final document
  * If the mate connector is **cylindrical** or **revolute**, a ``revolute`` joint will be issued
  * If the mate connector is a **slider**, a ``prismatic`` joint will be issued
  * If the mate connector is **fastened**, a ``floating`` joint will be issued
* When doing this connection, click the children joint first. This will be used to find the trunk of the robot (part with children but no parent)

.. image:: _static/img/smalls/design.png
    :align: center

Inverting axis orientation
--------------------------

It is possible to invert the axis for convenience by adding ``_inv`` at the end of the name. For instance
``dof_head_pitch_inv`` will result in a joint named ``head_pitch`` having the axis inverted with the one
from the OnShape assembly.

Naming links
------------

If you create a mate connector and name it ``link_something``, the link corresponding to the part
on which it is attached will be named ``something`` in the resulting URDF.

.. _custom-frames:

Adding custom frames in your model
----------------------------------

If you want to track some frames on your robot, you can do the following:

* Connect any part to your robot using mate relations in OnShape
* Name one of these relations ``frame_something``, when ``something`` will be the name of
  the frame (a link) in the resulting ``sdf`` or ``urdf``

.. image:: _static/img/smalls/frame.png
    :align: center

If you want to give it a try, you can use the ``onshape-to-robot-bullet`` in ``urdf`` mode, it will output the
frames on standard output.

Joint frames
------------

Joint frames are positionned wherever you positionned the mate connector itself, and oriented in
the frame of the child link.