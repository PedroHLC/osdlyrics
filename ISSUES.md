Adopt a different release model
===============================

Currently, development seems to be stuck in two separate branches.
master is almost inactive but it extends the 0.4 series.
0.5 series is slowly being developed but without any roadmap.
Both series are quite stable but both have their bugs.

I think that the branch 0.5-series should become the new master. To make this
happen, I have renamed the current master to 0.4-enhanced. The next step is to
merge 0.5-series to master. When this is done, I would like osdlyrics 0.5 to
be released as a development version leading to a stable 0.6 version.

The above model of odd-numbered unstable, and even-numbered stable releases
is customary (Wine uses it, for instance) and nice when it comes to
pre-releases: instead of having e.g. a 0.4.99 version leading to a 0.5
milestone, or being stuck in a fairly stable 0.5 development branch without
any release, one can simply do a 0.5 release and improve it feature-wise
and with regards to stability before reaching a stable 0.6. Then 0.7 would
be branched for further development. 0.6 would only gain backports of fixes
or simple improvements.

OSD is not click-thru when started in "Lock Position" mode
==========================================================

On startup, the OSD is apparently not in the same state as if switched to
"Lock Position" mode during runtime. Error messages are output when the
window is clicked. The window should not be clickable at all.

When a mouse button is pressed:
(OSD Lyrics:8291): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion 'GDK_IS_WINDOW (window)' failed

(OSD Lyrics:8291): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

When the button is released::
(OSD Lyrics:8291): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

The messages do not originate from osdlyrics code, they come from inside Gtk.
I have some naive code that stops the messages but the window is still not
click-thru on startup.


MPRIS 1.0 doesn't seem to poll a player (e.g. MOC) for current time
===================================================================

When seeking occurs in a player only supporting MPRIS 1.0, osdlyrics doesn't
find out because it doesn't seem to send GetPosition messages (in 0.5-series).
