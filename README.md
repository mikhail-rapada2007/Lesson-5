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

12. Next topic is create view



July 27, 2026
1. We can do submissions either HTML form or Django form.
in HTML, you can do <form method="post"></form> to make a form section and <input type="text" name="content placeholder=
also make a button <button type="submit">submit</button>

addd {% csrf_token %} whenever making forms 

make a new URL rout for this submission form which is def ______(request)

add tweet.objects.create(content=request.POST.get('CONTENT'))


2. In template inheritance, not only can u use extends but also {includes }
you can use includes to make unique layout for each user


3. DJANGO forms
forms.py inside the tweets
from django import forms

class TweetForm(forms.Form):
   content = forms.CharField(
5. 


SEARCH FUNCTION
https://www.google.com/search?q=wordgoeshere
?q comes together, q stands for query 

this can be class based or function based 

*in views.py*

class TweetListView(ListView):
   queryset = Tweet.objects.all()
   template_name = 'tweets/list.html'

   def get_queryset(self. *args, **kwargs):
      qs = Tweet.objects.all()
      query = self.request.GET.get('query', none)
      print(query) <- proves that we are getting something
      if query is not None:
         qs = qs.filter(content.icontains=query)
      return qs

   def get_context_data(self. *args, **kwargs):
      context = super(TweetListView, self).get_context
      

    
or just use 
use it in views.py

from django.db.models import Q
class TweetListView(ListView):
   queryset = Tweet.objects.all()
   template_name = 'tweets/list.html'

   def get_queryset(self. *args, **kwargs):
      qs = Tweet.objects.all()
      query = self.request.GET.get('query', none)
      print(query) <- proves that we are getting something
      if query is not None:
         qs = qs.filter(
            Q(content__icontains=query) | 
            Q(tags__icontains=query)
         )
      return qs

   def get_context_data(self. *args, **kwargs):
      context = super(TweetListView, self).get_context
      
fixnow in html add the {% empty %} 
to show that no tweets are found or if no tweets are found from the database

{% if get_query %}

something like that



