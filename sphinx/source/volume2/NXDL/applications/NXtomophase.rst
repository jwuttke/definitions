..  _NXtomophase:

###########
NXtomophase
###########

.. index::  ! . NXDL applications; NXtomophase

category:
    applications

NXDL source:
    NXtomophase
    
    (http://svn.nexusformat.org/definitions/trunk/applications/NXtomophase.nxdl.xml)

version:
    1.0b

SVN Id:
    $Id$

extends class:
    :ref:`NXobject`

other classes included:
    :ref:`NXdata`, :ref:`NXdetector`, :ref:`NXentry`, :ref:`NXinstrument`, :ref:`NXmonitor`, :ref:`NXsample`, :ref:`NXsource`

documentation:
    This is the application definition for x-ray or neutron tomography raw data with phase contrast variation at each point. In tomography first
    some dark field images are measured, some bright field images and, of course the sample. In order
    to properly sort the order of the images taken, a sequence number is stored with each image.
    


.. rubric:: Basic Structure of **NXtomophase**

.. code-block:: text
    :linenos:
    
    NXtomophase (application definition, version 1.0b)
      (overlays NXentry)
      entry:NXentry
        definition:NX_CHAR
        end_time:NX_DATE_TIME
        start_time:NX_DATE_TIME
        title:NX_CHAR
        data:NXdata
          data --> /NXentry/NXinstrument/sample:NXdetector/data
          rotation_angle --> /NXentry/NXsample/rotation_angle
        instrument:NXinstrument
          bright_field:NXdetector
            data:NX_INT[nBrightFrames,xsize,ysize]
            sequence_number:NX_INT[nBrightFrames]
          dark_field:NXdetector
            data:NX_INT[nDarkFrames,xsize,ysize]
            sequence_number:NX_INT[nDarkFrames]
          sample:NXdetector
            data:NX_INT[nSampleFrames,nPhase,xsize,ysize]
            distance:NX_FLOAT
            sequence_number:NX_INT[nSampleFrames,nPhase]
            x_pixel_size:NX_FLOAT
            y_pixel_size:NX_FLOAT
          NXsource
            name:NX_CHAR
            probe:NX_CHAR
            type:NX_CHAR
        control:NXmonitor
          integral:NX_FLOAT[nDarkFrames + nBrightFrames + nSampleFrame]
        sample:NXsample
          name:NX_CHAR
          rotation_angle:NX_FLOAT[nSampleFrames]
          x_translation:NX_FLOAT[nSampleFrames]
          y_translation:NX_FLOAT[nSampleFrames]
          z_translation:NX_FLOAT[nSampleFrames]
    

.. rubric:: Symbols used in definition of **NXtomophase**

These symbols will be used below to coordinate datasets with the same shape.

+-------------------+---------------------------------+
| Symbol            | Description                     |
+===================+=================================+
| ``nBrightFrames`` | number of bright frames         |
+-------------------+---------------------------------+
| ``nDarkFrames``   | number of dark frames           |
+-------------------+---------------------------------+
| ``nSampleFrames`` | number of image (sample) frames |
+-------------------+---------------------------------+
| ``nPhase``        | number of phase settings        |
+-------------------+---------------------------------+
| ``xsize``         | number of pixels in X direction |
+-------------------+---------------------------------+
| ``ysize``         | number of pixels in Y direction |
+-------------------+---------------------------------+




.. rubric:: Comprehensive Structure of **NXtomophase**

+---------------------+----------+-------+-------------------------------+
| Name and Attributes | Type     | Units | Description (and Occurrences) |
+=====================+==========+=======+===============================+
| class               | NX_FLOAT | ..    | ..                            |
+---------------------+----------+-------+-------------------------------+
