## Usage

```
$ autoreconf --install
$ mkdir build
$ cd build
$ ../configure
$ make
$ cd application
$ ./bulletopengl
$ git clean -x -f -d
```

## Developer NOTEs
* Creation of Objects can be done only by `ObjectTemplateManager::createObject()`.

* During Object creation neither Object nor its Components are made available 
to other threads before `ObjectTemplateManager::createObject()` are returned.

* Addition of a Component to an Objects can be done only by `ObjectTemplateManager::addComponentToObject().`

* Thread safeness. After an Object and its Components are created, to avoid 
deadlock rules are as follow:
	> a. Component method could call its owner Object's methods (so it possibly lock first its mutex and then the Object's one)

	> b. no Object method call its Components' methods

	> c. no ObjectTemplateManager methods are called by Object or Components' methods

	 
