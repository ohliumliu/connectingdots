If a page needs to load several images, sometimes it makes sense to load the combined image. 
This reduces the number of requests. For example, "home", "forward" and "backward" icons can
be grouped together and loaded in one shot. When using them, crop the combined image to select
only the appropriate one. For example, in a css block, use ``background: url('my_image.gif') -50 px 0``
