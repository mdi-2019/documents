# CM + TP Vue.js

Module MDI 2018-2019 - ESIR 2 IS

__Durée :__ 4 heures

## Objectifs

* Comprendre quelles problématiques résolvent les frameworks comme Vue.js, Angular et React
* Expérimenter ces problématiques
* Obtenir un aperçu des problématiques principales du développement/de l'architecture frontend
* Ecrire une première application frontend avec Vue.js
* Prendre du recul sur son utilisation et sur le développement frontend en général

## Cours

### 1 - Développement en HTML / CSS / JS uniquement - 1h

Dans cette section, vous allez rapidement créer une "single page application" qui contient deux vues. Elle gèrera des todos et permettra de voir le détail d'un TODO.

Faites des copier/coller, vous avez une heure pour tout faire.

Créer un dossier dans lequel placer le code de cette section

#### 1 - Créer un fichier HTML très simple

* Dans le dossier précédemment créé, créer un fichier `index.html`

```html
<!DOCTYPE html>
<html>
    <head>
        <title>TODO App</title>
    </head>

    <body>
        Hello world!
    </body>
</html>
```

Ouvrir ce fichier dans son navigateur.

#### 2 - Ajouter Bootstrap pour avoir une page qui ressemblera rapidement à quelque chose

* Ajouter la ligne suivante juste après la première balise `<head>`

```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```

* Ajouter les lignes suivantes juste avant la balise fermant le body : `</body>`

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```

#### 3 - Ajouter une barre des menus

Juste en dessous de `body` :

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <a class="navbar-brand" href="#">TODO App</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
            <li class="nav-item">
                <a class="nav-link" href="#">Accueil</span></a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#/info">Info</a>
            </li>
        </ul>

        <ul class="navbar-nav flex-row ml-md-auto d-none d-md-flex">
            <li class="nav-item">
                <a class="nav-link" href="#" target="_blank" rel="noopener" aria-label="GitHub">
                    <svg xmlns="http://www.w3.org/2000/svg" class="navbar-nav-svg" viewBox="0 0 512 499.36" role="img" focusable="false"><title>GitHub</title><path fill="currentColor" fill-rule="evenodd" d="M256 0C114.64 0 0 114.61 0 256c0 113.09 73.34 209 175.08 242.9 12.8 2.35 17.47-5.56 17.47-12.34 0-6.08-.22-22.18-.35-43.54-71.2 15.49-86.2-34.34-86.2-34.34-11.64-29.57-28.42-37.45-28.42-37.45-23.27-15.84 1.73-15.55 1.73-15.55 25.69 1.81 39.21 26.38 39.21 26.38 22.84 39.12 59.92 27.82 74.5 21.27 2.33-16.54 8.94-27.82 16.25-34.22-56.84-6.43-116.6-28.43-116.6-126.49 0-27.95 10-50.8 26.35-68.69-2.63-6.48-11.42-32.5 2.51-67.75 0 0 21.49-6.88 70.4 26.24a242.65 242.65 0 0 1 128.18 0c48.87-33.13 70.33-26.24 70.33-26.24 14 35.25 5.18 61.27 2.55 67.75 16.41 17.9 26.31 40.75 26.31 68.69 0 98.35-59.85 120-116.88 126.32 9.19 7.9 17.38 23.53 17.38 47.41 0 34.22-.31 61.83-.31 70.23 0 6.85 4.61 14.81 17.6 12.31C438.72 464.97 512 369.08 512 256.02 512 114.62 397.37 0 256 0z"></path></svg>
                </a>
            </li>
        </ul>
    </div>
</nav>
```

#### 4 - Ajouter la liste des tâches et une première tâche

A la place de `Hello world!` placer le code suivant : 

```html
<section id="todos" class="container">
    <div class="row">
        <h1>Liste de tâches</h1>
    </div>
    <div class="row" id="todo-list">
        <div class="col-sm-4">
            <div class="card">
                <div class="card-body">
                    <p><input type="checkbox">Une première tâche</span></p>
                </div>
            </div>
        </div>
    </div>
</section>
```

#### 5 - Ajouter deux autres tâches

A vous sur ce coup là ! Ajouter deux tâches et vérifier que tout fonctionne bien.

#### 6 - Ajouter une section info, qui deviendra la page info par la suite

Copier ce code après la section todos : 

```html
<section id="info" class="container">
    <div class="row">
        <h1>Info</h1>
    </div>
    <div class="row flex-column">
        <p>Vous êtes sur la page info de ce site.</p>
        <p>Elle pourrait contenir plein d'informations sur ce qu'est une todo list, ou sur ce TP...</p>
    </div>
</section>
```

#### 7 - Ajouter une section qui détaille les informations d'une tâche

Après la section info, insérer ce code : 

```html
<section id="todo-detail" class="container">
    <div class="row">
        <h1>Détail d'une tâche</h1>
    </div>
    <div class="row flex-column">
        <div class="col-sm-4">
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title"><span data-target='task-title'>Titre de la tâche</span></h5>
                    <h6 class="card-subtitle mb-2 text-muted">Créée par <span data-target='task-created-by'>USER</span> le <span data-target='task-created-on'>01/01/1970</span></h6>
                    <p class="card-text"><span data-target='task-description'>Description</span></p>
                    <button class="btn btn-success todo-done-button">Terminate</button>
                    <button class="btn btn-danger todo-not-done-button">Remark as todo</button>
                </div>
            </div>
        </div>
    </div>
</section>
```

#### 8 - Afficher la liste des tâches avec du Javascript

1. Dans le fichier `index.html`, ajouter le template suivant en dessous de la dernière section : 

```html
<template id="todo-el">
    <div class="col-sm-4">
        <div class="card">
            <div class="card-body">
                <p><input type="checkbox"><span data-target="todo-label"></span></p>
            </div>
        </div>
    </div>
</template>
```

2. Supprimer les trois todos et remplacer par `<!-- Todos will be loaded over here with Javascript code -->`
3. Créer un fichier `main.js` et l'importer en ajoutant `<script src="main.js"></script>` en dessous des scripts important Bootstrap
4. Créer quelques todos dans le fichier `main.js`

```js
const todos = [
    { label: 'Commencer ce TP', checked: true},
    { label: 'Finir ce TP', checked: false },
    { label: 'Comprendre quelles problématiques résolvent les frameworks comme Vue.js, Angular et React', checked: false },
    { label: 'Expérimenter ces problématiques', checked: false },
    { label: 'Obtenir un aperçu des problématiques principales du développement/de l\'architecture frontend', checked: false },
    { label: 'Ecrire une première application frontend avec Vue.js', checked: false },
    { label: 'Prendre du recul sur son utilisation et sur le développement frontend en général', checked: false }
]
```

5. Créer une fonction qui crée un élément HTML à partir du nouveau template 

```js
function createTodoFromTemplate(todos, index, label, checked) {
    if ('content' in document.createElement('template')) {
        const template = document.getElementById('todo-el')
        const clone = document.importNode(template.content, true)

        const todoId = 'todo-el-' + index

        const inputElement = clone.querySelector('input')
        inputElement.id = todoId
        inputElement.checked = checked
        
        const labelElement = clone.querySelector('[data-target="todo-label"]')
        labelElement.textContent = label

        return clone 
    }
}
```

6. Créer une fonction qui insert des tâches dans le document

```js
function insertTodosIntoDocument(todos) {
    const todoList = document.getElementById('todo-list')
    todos.forEach((todo, index) => todoList.appendChild(
        createTodoFromTemplate(todos, index, todo.label, todo.checked)
    ))
}
```

7. Appeler la fonction d'insertion des tâches au chargement de la page

```js
window.onload = () => {
    insertTodosIntoDocument(todos)
}
```

#### 9 - Mettre à jour les tâches et mémoriser le nouvel état

1. Créer une fonction qui met à jour la valeur d'une tâche lorsque sa valeur change :

```js
function updateCheckedValueOfTask(todos, index) {
    return (event) => {
        todos[index].checked = event.target.checked
        insertTodosIntoDocument(todos)
    }
}
```

2. Appeler cette fonction lorsque l'utilisateur coche/decoche une tâche : 

Dans la fonction `createTodoFromTemplate`, ajouter : 

`inputElement.addEventListener('change', updateCheckedValueOfTask(todos, index))`

3. Dans la fonction `insertTodosIntoDocument` ajouter un morceau de code pour vider la liste des todos avant d'afficher les nouvelles valeurs

```js
while (todoList.hasChildNodes()) {   
    todoList.removeChild(todoList.firstChild);
}
```

#### 10 - Permettre à l'utilisateur d'ajouter une tâche

1. Ajouter un formulaire dans la page

Dans `index.html`, après la div dont l'id est `todo-list` et avant la fermeture de la section `</section>`

```html
<div class="row flex-column">
    <h2>Ajouter une tâche</h2>
    <form>
        <div class="form-group col-sm-6">
            <label for="todo-to-add">Nom de la tâche</label>
            <input type="text" class="form-control" id="todo-to-add" placeholder="Tâche à ajouter à la liste">
        </div>
        <button id="add-todo-button" type="submit" class="btn btn-primary" >Ajouter</button>
    </form>
</div>
```

2. Ajouter une fonction qui ajoute la todo lorsque le bouton est cliqué

Dans `main.js`

```js
function addTodoAndRenderThemAll(todos) {
    return (clickOnSubmitButtonEvent) => {
        clickOnSubmitButtonEvent.preventDefault()
        const newTodoInputEl = document.getElementById(TODO_TO_ADD_INPUT_FIELD_ID)
        const userEnteredTodo = newTodoInputEl.value
        if (userEnteredTodo !== "") {
            todos.push({ label: userEnteredTodo, checked: false })
            newTodoInputEl.value = ''
            insertTodosIntoDocument(todos)
        }
    }
}
```

Ajouter les constantes nécessaires, tout en haut de `main.js` : 

```js
const ADD_TODO_BUTTON_ID = 'add-todo-button'
const TODO_TO_ADD_INPUT_FIELD_ID = 'todo-to-add'
```

3. Au chargement de la page, lui dire d'appeler la fonction tout juste écrite lorsque le bouton est cliqué : 

Remplacer l'assignation de `window.onload` par la suivante :

```js
window.onload = () => {
    document.getElementById(ADD_TODO_BUTTON_ID).addEventListener('click', addTodoAndRenderThemAll(todos))
    insertTodosIntoDocument(todos)
}
```

#### 11 - Ajouter un bouton pour supprimer une tâche

1. Ajouter un bouton dans le template d'une tâche : 

```html 
<button class="btn btn-danger todo-remove-button">Remove</button>
```

2. Ajouter la fonction qui supprime une tâche

```js
function removeTask(todos, index) {
    return (event) => {
        todos.splice(index, 1)
        insertTodosIntoDocument(todos)
    }
}
```

3. Lier cette fonction au bouton

Dans la fonction `createTodoFromTemplate`, avant `return clone`.

```js
const removeButton = clone.querySelector('.todo-remove-button')
removeButton.addEventListener('click', removeTask(todos, index))
```

#### 12 - Faire de la liste des tâches, de Info et du détail d'une tâche des templates

En plus de ce qui est demander dans le titre, ajouter `<div id="app"></div>` dans le fichier `index.html` en dessous de la navbar.

A la fin de cette étape, `index.html` devrait avoir cette forme : 

```html
<!DOCTYPE html>
<html>
    <head>
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">

        <title>TODO App</title>
    </head>

    <body>
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
            <a class="navbar-brand" href="#">TODO App</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="#">Accueil</span></a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#/info">Info</a>
                    </li>
                </ul>

                <ul class="navbar-nav flex-row ml-md-auto d-none d-md-flex">
                    <li class="nav-item">
                        <a class="nav-link" href="#" target="_blank" rel="noopener" aria-label="GitHub">
                            <svg xmlns="http://www.w3.org/2000/svg" class="navbar-nav-svg" viewBox="0 0 512 499.36" role="img" focusable="false"><title>GitHub</title><path fill="currentColor" fill-rule="evenodd" d="M256 0C114.64 0 0 114.61 0 256c0 113.09 73.34 209 175.08 242.9 12.8 2.35 17.47-5.56 17.47-12.34 0-6.08-.22-22.18-.35-43.54-71.2 15.49-86.2-34.34-86.2-34.34-11.64-29.57-28.42-37.45-28.42-37.45-23.27-15.84 1.73-15.55 1.73-15.55 25.69 1.81 39.21 26.38 39.21 26.38 22.84 39.12 59.92 27.82 74.5 21.27 2.33-16.54 8.94-27.82 16.25-34.22-56.84-6.43-116.6-28.43-116.6-126.49 0-27.95 10-50.8 26.35-68.69-2.63-6.48-11.42-32.5 2.51-67.75 0 0 21.49-6.88 70.4 26.24a242.65 242.65 0 0 1 128.18 0c48.87-33.13 70.33-26.24 70.33-26.24 14 35.25 5.18 61.27 2.55 67.75 16.41 17.9 26.31 40.75 26.31 68.69 0 98.35-59.85 120-116.88 126.32 9.19 7.9 17.38 23.53 17.38 47.41 0 34.22-.31 61.83-.31 70.23 0 6.85 4.61 14.81 17.6 12.31C438.72 464.97 512 369.08 512 256.02 512 114.62 397.37 0 256 0z"></path></svg>
                        </a>
                    </li>
                </ul>
            </div>
        </nav>

        <div id="app"></div>

        <template id="todos">
            <div class="container">
                <div class="row">
                    <h1>Liste de tâches</h1>
                </div>
                <div class="row" id="todo-list">
                    <!-- Todos will be loaded over here with Javascript code -->
                </div>
                <div class="row flex-column">
                    <h2>Ajouter une tâche</h2>
                    <form>
                        <div class="form-group col-sm-6">
                            <label for="todo-to-add">Nom de la tâche</label>
                            <input type="text" class="form-control" id="todo-to-add" placeholder="Tâche à ajouter à la liste">
                        </div>
                        <button type="submit" class="btn btn-primary" id="add-todo-button">Ajouter</button>
                    </form>
                </div>
            </div>
        </template>

        <template id="info">        
            <div class="container">
                <div class="row">
                    <h1>Info</h1>
                </div>
                <div class="row flex-column">
                    <p>Vous êtes sur la page info de ce site.</p>
                    <p>Elle pourrait contenir plein d'informations sur ce qu'est une todo list, ou sur ce TP...</p>
                </div>
            </div>
        </template>

        <template id="todo-detail">
            <div class="container">
                <div class="row">
                    <h1>Détail d'une tâche</h1>
                </div>
                <div class="row flex-column">
                    <div class="col-sm-4">
                        <div class="card">
                            <div class="card-body">
                                <h5 class="card-title"><span data-target='task-title'></span></h5>
                                <h6 class="card-subtitle mb-2 text-muted">Créée par <span data-target='task-created-by'></span> le <span data-target='task-created-on'></span></h6>
                                <p class="card-text"><span data-target='task-description'></span></p>
                                <button class="btn btn-success todo-done-button">Terminate</button>
                                <button class="btn btn-danger todo-not-done-button">Remark as todo</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </template>

        <template id="todo-el">
            <div class="col-sm-4">
                <div class="card">
                    <div class="card-body">
                        <p>
                            <input type="checkbox"><span data-target="todo-label"></span>
                        </p>
                        <button class="btn btn-danger todo-remove-button">Remove</button>
                    </div>
                </div>
            </div>
        </template>

        <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
        <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>

        <!-- Custom scripts -->
        <script src="main.js"></script>
    </body>
</html>
```

#### 13 - Implémenter le routing de la page

Nous souhaitions avoir une Single Page Application, ce qui veut dire qu'il n'existe qu'un seul fichier HTML pour toute l'application. C'est donc avec du javascript que nous gérerons les demandes de changement de page de l'utilisateur. 

Pour cela, nous utiliserons l'API History du navigateur.

1. Créer une fonction pour router l'utilisateur :

```js 
function routeUser() {
    const userRequestedRoute = window.location.hash.startsWith('#')
      ? window.location.hash.substring(1)
      : window.location.hash

    if (userRequestedRoute === '' || userRequestedRoute === '/home') {
        displayTodoListPage()
    } else if (userRequestedRoute === '/info') {
        displayInfoPage()
    } else if (userRequestedRoute.startsWith('/todo-detail')) {
        const todoId = userRequestedRoute.substring('/todo-detail/'.length)
        displayTodoDetailsPage(todoId)
    } else {
        display404()
    }
}
```

2. Ecrire la fonction qui affiche chaque page :

```js
function displayTodoListPage() {
    emptyAppAndDisplayTemplateFromId(TODO_PAGE_TEMPLATE_ID)

    document.getElementById(ADD_TODO_BUTTON_ID).addEventListener('click', addTodoAndRenderThemAll(todos))
    insertTodosIntoDocument(todos)
}

function displayInfoPage() {
    emptyAppAndDisplayTemplateFromId(INFO_PAGE_TEMPLATE_ID)
}

function displayTodoDetailsPage(todoId) {
    console.log('Todo to display:' + todoId)
    emptyAppAndDisplayTemplateFromId(TODO_DETAIL_PAGE_TEMPLATE_ID)
}

function display404() {
    const app = getCleanedAppElement()
    const element = document.createElement('p')
    element.textContent = '404 - Page not found.'
    app.appendChild(element)
}

function emptyAppAndDisplayTemplateFromId(id) {
    const template = document.getElementById(id)
    const clone = document.importNode(template.content, true)

    const app = getCleanedAppElement()
    app.appendChild(clone)
}

function emptyDiv(divElement) {
    while (divElement.hasChildNodes()) {   
        divElement.removeChild(divElement.firstChild);
    }
}

function getCleanedAppElement() {
    const app = document.getElementById('app')
    emptyDiv(app)
    return app
}
```

3. Ecrire une fonction qui affiche un message d'erreur si le navigateur est trop vieux :

```js
function router() {
    if ('content' in document.createElement('template')) {
        routeUser()
    } else {
        alert('ERROR: this website is not compatible with your browser. Please download a modern one.')
    }
}
```

4. Remplacer `window.onload` par la valeur suivante, et assigner la même fonction à `window.onpopstate` : 

```js
window.onload = () => router()
window.onpopstate = () => router()
```

5. Ajouter les constantes utilisées dans ce code

A placer en haut du fichier `main.js`.

```js
const TODO_PAGE_TEMPLATE_ID = 'todos'
const INFO_PAGE_TEMPLATE_ID = 'info'
const TODO_DETAIL_PAGE_TEMPLATE_ID = 'todo-detail'
```

#### 14 - Afficher le détail d'une tâche

1. Ajouter un bouton sur les tâches pour rediriger vers la page présentant leur détail.

Dans `index.html` sur le template des tâches, ajouter : 

```html
<a class="btn btn-info todo-detail-button">Détail</a>
```

2. Augmenter les todos pour qu'elles contiennent la donnée à afficher :

```js
const todos = [
    { label: 'Commencer ce TP', checked: true, createdBy: 'foo', createdOn: '2019-01-01', description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed leo erat, iaculis eu nibh a, cursus semper libero. Proin at.'},
    { label: 'Finir ce TP', checked: false, createdBy: 'foo', createdOn: '2019-01-01', description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed leo erat, iaculis eu nibh a, cursus semper libero. Proin at.'},
    { label: 'Comprendre quelles problématiques résolvent les frameworks comme Vue.js, Angular et React', checked: false, createdBy: 'foo', createdOn: '2019-01-01', description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed leo erat, iaculis eu nibh a, cursus semper libero. Proin at.'},
    { label: 'Expérimenter ces problématiques', checked: false, createdBy: 'foo', createdOn: '2019-01-01', description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed leo erat, iaculis eu nibh a, cursus semper libero. Proin at.'},
    { label: 'Obtenir un aperçu des problématiques principales du développement/de l\'architecture frontend', checked: false, createdBy: 'foo', createdOn: '2019-01-01', description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed leo erat, iaculis eu nibh a, cursus semper libero. Proin at.'},
    { label: 'Ecrire une première application frontend avec Vue.js', checked: false, createdBy: 'foo', createdOn: '2019-01-01', description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed leo erat, iaculis eu nibh a, cursus semper libero. Proin at.'},
    { label: 'Prendre du recul sur son utilisation et sur le développement frontend en général', checked: false, createdBy: 'foo', createdOn: '2019-01-01', description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed leo erat, iaculis eu nibh a, cursus semper libero. Proin at.'}
]
```

3. Remplacer le contenu de la fonction `displayTodoDetailsPage(todoId)` par :

```js
function displayTodoDetailsPage(todoId) {
    const app = getCleanedAppElement()
    if (todos[todoId]) {
        app.appendChild(createTodoDetailFromTemplate(todos, todoId))
    } else {
        display404()
    }
}
```

4. Créer une fonction pour remplir le template du détail d'une tâche : 

```js
function createTodoDetailFromTemplate(todos, index) {
    const template = document.getElementById(TODO_DETAIL_PAGE_TEMPLATE_ID)
    const clone = document.importNode(template.content, true)
    const task = todos[index]

    clone.querySelector('[data-target="task-title"]').textContent = task.label
    clone.querySelector('[data-target="task-created-by"]').textContent = task.createdBy
    clone.querySelector('[data-target="task-created-on"]').textContent = task.createdOn
    clone.querySelector('[data-target="task-description"]').textContent = task.description

    const todoDoneButton = clone.querySelector('.todo-done-button')
    const todoNotDoneButton = clone.querySelector('.todo-not-done-button')
    if (task.checked) {
        todoNotDoneButton.addEventListener('click', () => changeTodoCheckedStateAndReloadTodoDetailPage(todos, index, false))
        todoDoneButton.style.display = 'none'
    } else {
        todoDoneButton.addEventListener('click', () => changeTodoCheckedStateAndReloadTodoDetailPage(todos, index, true))
        todoNotDoneButton.style.display = 'none'
    }

    return clone
}

function changeTodoCheckedStateAndReloadTodoDetailPage(todos, index, value) {
    todos[index].checked = value
    displayTodoDetailsPage(index)   
}
```

5. Ajouter au bouton "detail" de chaque tâche la bonne URL de redirection

Dans la fonction `createTodoFromTemplate` du fichier `main.js` ajouter le code suivant :

```js
const detailButton = clone.querySelector('.todo-detail-button')
detailButton.href = '#/todo-detail/' + index
```

### 2 - Prise de recul sur ce code - 20 minutes

* Bilan de l'architecture et du fonctionnement du code -> quelqu'un vient faire un schéma au tableau
* Qu'est-ce qui vous semble lourd, pénible ou frustrant ?
* Qu'est-ce qui est répétitif ?
* Qu'est-ce qui vous semble compliqué ou risqué (en termes de developpement logiciel) ?

### 3 - Problématiques générales du développement Web sur le modèle client-serveur - 10 minutes

* Par quoi commencer pour faire un site web ?
    * `#besoin_client`
    * `#designer`
    * `#user_centric`
* Qu'est-ce qu'un bon site web ?
    * Quels enjeux ? (compatibilité cross-browser et responsive)
    * Voir [doc Google sur la performance d'un site web](https://developers.google.com/web/fundamentals/)
    * `#responsive`
    * `#cross_browser_compatibility`
    * `#performant`
    * `#fluid`
    * `#light`
    * `#lazy-loading-offscreen-images`
    * `#responsive-images`
    * `#use-images-cdn`
    * `#defer-third-party-js`
    * `#defer-dependencies-with-service-workers`
    * `#code-splitting`
    * `#PRPL-pattern`
    * `#critical-CSS`

### 4 - Prise en main de Vue.js - 2h

#### Introduction

* Qu'est-ce que [Vue.js](https://vuejs.org/) et à quoi ça sert ?

#### Pratique

Si après 1h30 vous n'avez pas fini les tutoriels 1 à 9, sauter directement au 10.

1. Faire [cette introduction](https://vuejs.org/v2/guide/) dans un nouveau dossier
2. Utiliser ce qui a été appris dans le tutoriel précédent pour refaire la même application que celle copiée/collée plus tôt, autant que possible. Implémentez que ce que ce tutoriel vous permet d'implémenter.
3. Lire rapidement [The Vue Instance](https://vuejs.org/v2/guide/instance.html)
4. Lire rapidement et appliquer [Template Syntax](https://vuejs.org/v2/guide/syntax.html)
5. Lire et appliquer [Computed Properties and Watchers](https://vuejs.org/v2/guide/computed.html#Computed-Properties), uniquement la première section "Basic Example"
6. Lire rapidement et appliquer [Class and Style Bindings](https://vuejs.org/v2/guide/class-and-style.html)
7. Lire et appliquer [Conditional Rendering](https://vuejs.org/v2/guide/conditional.html)
8. Lire rapidement et appliquer [Event Handling](https://vuejs.org/v2/guide/events.html)
9. Lire et appliquer [Components Basics](https://vuejs.org/v2/guide/components.html)


10. [Introduction à VueRouter](https://router.vuejs.org/guide/#javascript)
11. [Dynamic Route Matching](https://router.vuejs.org/guide/essentials/dynamic-matching.html#reacting-to-params-changes)


* Regarder et être capable de venir expliquer à toute la classe :
    * Qu'est-ce que VueX ?
    * Comment se composent Vue, VueRouter et VueX ? Quel rôle à chacun de ces composants ?
    * Quels sont les équivalents dans le monde de React ?
    * Quels sont les équivalents dans le monde d'Angular ?

* Quelles différences entre React, Angular et Vue.js ?

### 5 - Prise de recul : problématiques générales du développement Web sur le modèle client-serveur - 20 minutes

* Quels rôles à le frontend ?
* Comment est faite l'architecture interne d'une application Web ? Du plus simple au plus complexe.
* Quand mettre en place quelle architecture ?
* Quelles sont les technologies modernes ?
* Quand est-ce qu'on a besoin d'un frontend qui est une application à part entière ?
* Site très dynamique : quelles technos ? Si relativement statique: quelles technos ?
* Qui a déjà fait un site web en PHP ? -> Comment se déroule l'exécution d'un programme PHP ?
* Quelle différence majeure avec les Single Page Application qui sont devenues très courantes ?
* Comparons client-side et server-side rendering -> performances, appropriés à quels contextes ? etc...
* Quelles architectures dans un modèle client-serveur ?

* Qu'est-ce que Web Assembly ?

### 6 - Retour sur le format de ce cours - 5 à 10 minutes

* Que pensez-vous du format de ce cours ?

## Pour aller plus loin

* [Speed at Scale: Web Performance Tips and Tricks from the Trenches (Google I/O'19)](https://www.youtube.com/watch?v=YJGCZCaIZkQ&feature=youtu.be)