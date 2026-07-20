# Lesson-5

SERVING YOUR OWN CDN

1. What we will store in object storage
   Static files such as texts and company pics (company pics are not changed by common users)

2. In settings.py add

STATICFILES_DIRS = {
    BASE_DIR / "static_my_project",
}

STATIC_ROOT = os.path.join(BASE_DIR, "static", "static_root")

MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, "static", "media_root")


3. static becomes the local server, img, css, js, and the main.css are there. just run python manage.py collectstatic
4.in urls.py add

from djangp.conf add settings 
if settings.DEBUG:
from django.conf.urls.static import static
urlpatterns += static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)

5. Use bootstrap as a backup.
   download CSS AND JS in bootstrap website and copy paste CSS and JS to the static_my_project
   dont forget to run collect static again (is there a admin folder or do we have to add that?)

6. now you can call the static in the local server by doing {% load static %}
7. and now you can href in the html link href="{% static 'css.botstrap.min.css' %}" rel="stylesheet"
8. template inheritance <- this makes it so that you dont have to put {% load static %} in every html
