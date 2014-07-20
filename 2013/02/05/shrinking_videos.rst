Shrinking Videos
================

.. highlight:: bash

My digital camera creates quite big video files. This weekend I wrote a script, that converts those large MOV files to small MKV files::

    #!/bin/sh

    VIDEOS=/path/to/videos
    
    find $VIDEOS -name '*.MOV' | while read file
    do
        newFile=${file%.*}.mkv
        echo $file '->' $newFile
        if [ ! -e "$newFile" ] 
        then
            avconv -y -i $file -c:v libx264 -preset medium -crf 22 $newFile
        fi
    done

This reduces the file size by 80%. There are two interesting parameters you can tweak:

``-preset preset``
    Conversion speed vs. quality. Some valid values are faster, fast, medium, slow or slower.
``-crf crf``
    File size vs. quality. Higher values reduce the quality and file size.

You should also read the `FFmpeg documentation`_.

.. _FFmpeg documentation: https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide

.. author:: default
.. categories:: none
.. tags:: ffmpeg
.. comments::
