# Python + nginx + uWSGI

Basic configuration to get nginx and uwsgi working with a couple Python apps.


## Cast of Characters

* Python
  * and whatever Python WebApps you want that support wUSGI (Django, Flask...)
* uWSGI
  * This is responsible for adapting HTTP requests to Python
* nginx
  * Plugs port 80 into whatever sockets you have available

## Act 1 - Install

Install the things

## Act 2 - Plugging in things

Replace nginx's config with the `nginx.config` file (perhaps via symlink...)

    sudo rm /etc/nginx/sites-available/default
    sudo ln -s /vagrant/nginx.config /etc/nginx/sites-available/default
    sudo service nginx restart


## Act 3 - Showtime

> Rehearsal: run `sudo uwsgi --emperor emperor.ini`

...todo: upstart it...

## Some Caveats

uWSGI is usually built to accomodate one version of Python as a plugin. To
sing koombyah, check out how to [bake multiple Python's into the same uWSGI
binary][multibin]


## References

* [this guide](https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uwsgi-and-nginx-on-ubuntu-14-04)
* [this page](https://uwsgi-docs.readthedocs.org/en/latest/WSGIquickstart.html)
* [and this one](https://uwsgi-docs.readthedocs.org/en/latest/Emperor.html)

[multibin]: https://uwsgi-docs.readthedocs.org/en/latest/WSGIquickstart.html#bonus-multiple-python-versions-for-the-same-uwsgi-binary
