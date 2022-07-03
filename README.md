# Django--API-with-RESTFramework

[Working with APIs]
 

Create a new GitHub repository with a README.md, and Python .gitignore file.

Clone it to your machine/computer, that will create a new folder on your computer with your repository’s content.

Create a new virtual environment in that folder named venv. 

Activate it and install the Django python package (Hint: `pip install django`).

Also install the django rest framework (pip install djangorestframework)

Create a new django project (Hint: `django-admin startproject <project_name>`). 

Use your Zuriboard Student ID as the name of the project.

 

We’ll be creating the beginnings of a URL shortener service.

 

Create a new application using the django startapp command. The app should be called links.

Add the links and rest_framework app to INSTALLED_APPS.

 

Create a new file, utils.py in your links app folder. Replace the content of links/utils.py with this starter file https://github.com/TobeTek/Zuri/blob/main/starter-files/Working%20With%20APIs/utils.py . 


 

In links/models.py , create a new model Link. It should have the following attributes:

 Link

--------

target_url : A url path of maxlength 200, use Django’s models.URLField

 

description : A string of maxlength 200, use Django’s models.CharField

 

identifier: A string of maxlength 20, use Django’s models.SlugField. Set blank=True and unique=True for the field.

 

author : A Foreign Key to the current user model. Make use of Django’s get_user_model function.

 

created_date : A date-time column, use Django’s models.DateTimeField.

 

active :  A boolean (True or False), determining if the shortened URL is publicly accessible. Make use of Django’s BooleanField. The default should be True.


 

We should now have a Link model in links/models.py with a custom save method.

Create migrations for your new model using the makemigrations django command. 

Run all migrations using, migrate django command.

To make our Link model accessible from the admin site, register the Link model in links/admin.py . 

Go ahead to create a superuser, and create some Links from the admin dashboard.

 

Now for the serializers. 

Create a new file serizliers.py in the links app. It will hold all the logic for our serializers.
Create a new serializer, LinkSerializer, which inherits DRF’s 

serializers.ModelSerializer. It should have the following attributes:
class Meta:

model = Link

fields = “__all__”

 

On to the views. We will only allow users to interact with active/public urls through our API.


In blog/views.py,  create a new view/class PostListApi, which inherits DRF’s generic ListAPIView,  it’s config/attributes should be:

queryset = Link.objects.filter(active=True)

serializer_class = LinkSerializer

 

Create another view, PostCreateApi, which inherits DRF’s generic CreateAPIView, with attributes:

queryset = Link.objects.filter(active=True)

serializer_class = LinkSerializer

 

Create another view, PostDetailApi which inherits DRF’s generic RetrieveAPIView, with attributes:

queryset = Link.objects.filter(active=True)

serializer_class = LinkSerializer

 

Create another view PostUpdateApi, which inherits DRF’s generic UpdateAPIView, with attributes:

queryset = Link.object.filter(active=True)

serializer_class = LinkSerializer


 

Create another view PostDeleteApi, which inherits django’s generic DestroyAPIView, with attributes:

queryset= Link.objects.filter(active=True)

serializer_class = LinkSerializer


 

Create a file, links/urls.py, if it doesn’t already exist.

Replace the content of links/urls.py with the content of https://github.com/TobeTek/Zuri/blob/main/starter-files/Working%20With%20APIs/urls.py 

 

Go to your project_app/urls.py and add a new url pattern with the following content:

path("api/links/", include("links.urls"))


 

Stage and Commit your Django project and push your changes to your GitHub repository. 

Ensure your final code/submission is on the default branch of your GitHub repository.

Submit the link to your Github repository e.g https://github.com/github_username/repo_name