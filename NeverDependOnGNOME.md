# Never Depend on GNOME

https://gitlab.gnome.org/GNOME/gnome-build-meta/-/issues/749

My slack post:

Bit of a nightmare scenario for linux.  A few weeks ago the linux app was completely broken by an update to the GNOME flatpak runtime.  They updated their version of WebkitGTK to a new version that uses APIs incompatible with NVIDIA drivers.  This caused our app to come up to a blank canvas with no way that I can see of even detecting that an issue had occurred (thanks linux API developers for thinking about error handling).

We found out there was an environment variable we could set that would modify Webkit to not use this new API, so we added a patch in Tuple to set this environment variable.  This worked for a month or so until a few weeks ago Tuple started coming up to a blank canvas again.  Well I just tested not adding that environment variable and without out it now Tuple is fixed again !?!  wtf!?!
GNOME has taken an extreme stance here, here's how they responded to my report of this regression: https://gitlab.gnome.org/GNOME/gnome-build-meta/-/issues/749

> Hi, WebKitGTK updates are included because they are API/ABI compatible and contain important security updates. Regressions are inevitable and do not block updates.
> Unfortunately NVIDIA is indeed no longer supported. Even if this is eventually resolved, you should expect the future to be extremely rough going for NVIDIA users unless somebody with NVIDIA graphics volunteers to investigate and fix the issues.
7:42

In other words, "We're not going to hold up a release/update even keep an issue open just because it doesn't work on NVIDIA.  But we'll accept patches from you to fix things."  So, we reserve the right to break your application for NVIDIA users at any point with no notice and the best you can do is wait for any users you might have left to report problems and retroactively fix them until the next release.
