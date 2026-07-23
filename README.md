# Lesson-5

SERVING YOUR OWN CDN

1. What we will store in object storage
   Static files such as texts and company pics (company pics are not changed by common users)

2. In settings.py add
STATICFILES_DIRS = [
    BASE_DIR / "static_my_project",
]

STATIC_ROOT = os.path.join(BASE_DIR, "static", "static_root")

MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, "static", "media_root")

3. static becomes the local server, img, css, js, and the main.css are there. just run python manage.py collectstatic
4.in urls.py add

from django.conf add settings 
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

Continuation (July 23, 2026)
9. WE have two types of views, function based and class based view. Find the difference, one can be userd lazily and one is not.
We have generic views in django. One required is the list view which can be found in their website. 
Class based is shorter in code. But function based is more detailed, more customizable.

10. to use generic views, in views.py
from django.views.generic.list import ListView

class TweetListView(ListView):
    queryset = Tweet.objects.all()
    template_name = 'tweets/list.html' (there are some incorrect syntax here)

*remember that CRUD has a template from django*

*bevareful as database or sqlite3, if you delete an object in its database, it will start at (3) now when you delete the (2).)

11. pk and id. LEarn how django can call the ID of the database.

12. NExt topic is create view4
   
    



