Stop Saying "Docker"
====================

Docker Inc. is a commercial company
with a trademark on the term
"Docker".
It is possible to install the
open source Docker server,
the open source Docker client,
or the closed source
Docker Desktop.

Those things are properly called "Docker".
But people use the word for a lot of things it does not apply to.

A reasonably modern
:code:`dockerd`
(the docker server)
is a front-end to
:code`containerd`.
In other words,
the things it runs are not
"Docker containers".
It runs
"OCI containers".

The images from which OCI containers are run are not
"docker images".
They are OCI container images.
Container images are not stored in a
"docker registry".
Container images are stored in an
OCI distribution registry.

The default registry,
for historical reasons,
is
:code:`registry.hub.docker.com`.
It is appropriate to call
*that*
"Docker Registry",
since it is an
OCI distribution registry controlled by
Docker Inc.

This might sound pednatic,
or even annoyingly prescriptive.
But this confusion is responsible for real problems.

When Docker Inc.,
the company,
does something that upsets people,
they might decide not to use
"docker containers".
It is useful to distance the containers,
a technoloy standardized by
the Open Container Initiative,
from the company.

Another problem was the kerfuffle when Kubernetes announced that it is
deprecating support for Docker.
This deprecation was a much smaller problem than most people assumed:
by default,
Kubernetes has *not* been using Docker for a while already.

Instead of
:code:`kubelet`
communicating with
:code:`dockerd`
which would tell
:code:`containerd`
to run images,
it cut out the middle-person
and communicated directly with
:code:`containerd`.
This simplified the architecture,
removing one component that could possibly fail.

It also led people to believe that to run
"docker containers"
on their desktop,
they had to use
Docker Desktop,
and potentially pay licensing fees.
Docker Desktop is perfectly functional software
that can run containers on a desktop.
It is not the only way.

Projects like
`Lima`_
or even
`Minikube`_
(when using
its own virtual machine)
are also ways to run containers on a desktop machine.

.. _Lima: https://github.com/lima-vm/lima
.. _Minikube: https://minikube.sigs.k8s.io/docs/

Using terms like
"Docker container",
"Docker container image",
or a
"Docker container registry"
is misleading.
It is a form of free marketing for a commercial company,
and can lead people to incorrect conclusions.
Please stop.


