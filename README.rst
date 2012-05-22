About
=====

An Extensible class based Contact Form.

Fork of https://github.com/madisona/django-contact-form which is itself 
a fork of James Bennett's django-contact-form: 
https://bitbucket.org/ubernostrum/django-contact-form/


Installation
============

Add `contact_form` to `INSTALLED_APPS` in `settings.py`


Usage
=====

There is two way to use this app. You can either use the urls and views shipped with it or use your own.

Using bundled urls and views
----------------------------

Add contact_form urls to your project urls.py::

    from django.conf.urls.defaults import *
    from django.contrib import admin

    admin.autodiscover()

    urlpatterns = patterns('',
        (r'^admin/',     include(admin.site.urls)),
        (r'^contact/',   include('contact_form.urls')),
    )

Using your own urls and views
-----------------------------

Create your contact views subclassing the `ContactFormView`::

    from django.core.urlresolvers import reverse
    from contact_form import views, forms

    class ContactFormView(views.ContactFormView):
        template_name="my_site/contact.html",
        form_class = forms.BasicContactForm
        
        # If you want to change the success URL, just
        # override the get_success_url method
        def get_success_url(self):
            return reverse("my_site:contact_completed")


Settings
========

All settings are optional.::

    CONTACT_FORM_FROM_EMAIL         default: settings.DEFAULT_FROM_EMAIL
    CONTACT_FORM_RECIPIENTS         default: settings.MANAGERS
    CONTACT_FORM_FAIL_SILENTLY      default: False


Changelog
=========

2012-05-22
----------

* Added Russian translations

2012-02-02
----------

* Added conf/settings.py
* Added CONTACT_FORM_FROM_EMAIL, CONTACT_FORM_RECIPIENTS and CONTACT_FORM_FAIL_SILENTLY settings
* A bit of code cleanup & documentation
* Added site to email template context
* Added French translations

