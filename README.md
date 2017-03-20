<!--
    This file is part of slack.

    slack is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    slack is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with slack.  If not, see <http://www.gnu.org/licenses/>.
-->

# slack

This dockerization of slack is unusable as is.

If you use at as

```
docker \
    run \
    --interactive \
    --tty \
    --rm \
    --env DISPLAY \
    --volume /tmp/.X11-unix:/tmp/.X11-unix:ro \
    tidyrailroad/slack:0.0.0
```

then it will open up a window where nothing seems to work.

However if you do

```
docker \
    run \
    --interactive \
    --tty \
    --rm \
    --env DISPLAY \
    --volume /tmp/.X11-unix:/tmp/.X11-unix:ro \
    --entrypoint bash \
    tidyrailroad/slack:0.0.0
    
            dnf update --assumeyes &&
            dnf groupinstall --assumeyes "Fedora Workstation" &&
            slack
```

then it seems to work OK (not thoroughly tested).

This suggests to me that some of the packages the the "Fedora Workstation" group are needed, but I don't know which specific ones.
It seems wasteful to install the entire group to make the app work.