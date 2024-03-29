1. [Installation de Python-Django](../README.md)
2. [Création de l'app](creationappli.md)
3. [Structure](structure.md)
4. [Media](media.md)
5. [PostgreSQL](../postgresql.md)
6. [CSS](css.md)
7. [Formulaire](formulaire.md)
   
 


# les formulaires

Pour pouvoir ajoutez des éléments, il va falloir créer un formulaire. Django a prévu le coup, et il nous suffit de créer un nouveau fichier `forms.py` et d'y ajoutez 3 choses:

- un import du module forms de Django:

    from django import forms

- un import du modèle of course:

    from .models import Post

- et une classe qui se base sur un modèle du module forms:

```
class PostForm(forms.ModelForm):

    class Meta:
        model = Post
        title = forms.CharField(max_length=100)
        fields = ['cover', 'title']
```

Après ça, on crée le lien avec views.py en créant une autre classe. Mais d'abord, il faut encore importer quelques trucs!

- la classe PostForm qu'on vient de créer:

    from .forms import PostForm 

- le module reverse_lazy pour indiquer où se rediriger une fois que la requête est exécutée:

    from django.urls import reverse_lazy 

on peut maintenant créer la classe:

```
class CreatePostView(generic.CreateView): 
    model = Post
    form_class = PostForm
    template_name = 'post.html'
    success_url = reverse_lazy('gallery:index')
```

il faudra bien sûr editer l'url dans `urls.py` pour refleter la nouvelle classe:

    path('post/', views.CreatePostView.as_view(), name='add_post')

et éditer la template `post.html` pour y afficher le formulaire:

```
{% extends "base.html" %}

{% block title %} InstaClone | Image Upload {% endblock %}

{% load static %}

{% block content %}

<form method="post" enctype="multipart/form-data">
<h1> Ajoute une photo </h1>
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">OK</button>
</form>

{% endblock %}

```

Pour terminer, retournez sur le template `index.html` et ajoutez-y le lien vers la page d'upload sur l'icone:

```
{% block addPhoto %}

<a class="photoAdd" href="#">
    <img src="{% static '/img/addpic.png' %}">
</a>

{% endblock %}
```

Et voilà! 

Et voici un petit bonus pour ceux qui sont motivés: [ajouter des boutons like/dislike](bonus.md)
