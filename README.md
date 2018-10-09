# How to start with Clojurescript?

(Note: there is an alternative https://figwheel.org/, which has the project based on [figwheel-main](https://github.com/bhauman/figwheel-main)) - WIP creating a project based on `figwheel.main`. To do this, follow 
- https://rigsomelight.com/figwheel-main-template/
- https://cider.readthedocs.io/en/latest/clojurescript/#using-figwheel-main

Figwheel Main is a complete re-write of Figwheel and represents the latest and greatest version of Figwheel. It works great with Leiningen or the new Clojure CLI Tools.

So head over to Figwheel Main to give it a try.

Setup the environment for Clojurescript working environment with Emacs, CIDER and figwheel

## Setup from terminal

To get an interactive development environment run:

    lein figwheel

and open your browser at [localhost:3449](http://localhost:3449/).
This will auto compile and send all changes to the browser without the
need to reload. After the compilation process is complete, you will
get a Browser Connected REPL. An easy way to try it is:

    (js/alert "Am I connected?")

and you should see an alert in the browser window.

To clean all compiled files:

    lein clean

To create a production build run:

    lein do clean, cljsbuild once min

And open your browser in `resources/public/index.html`. You will not
get live reloading, nor a REPL. 

## Emacs setup

- Setup the project with `lein new figwheel hello-world`

- Clean up `project.clj`

- `~/.lein/profiles.clj` should look like [this](https://gist.github.com/sivakon/cba425ee1b2809d47c1e43001e1f1e63). `lein rebl` will always start `rebel-readline` mode in any project Clj/CLJS

- Install CIDER (> 0.18.0)

- `~/.emacs` should look like [this](https://gist.github.com/sivakon/8ce7e20f44f6c85f46714b61549080bd)
Need to change how CIDER starts a `cljs-lein-repl`. Look at the `.emacs` above to add necessary configuration

- Start the REPL with cider-jack-in-cljs `(C-c C-x (C-)j (C-)s)`. Select `figwheel-main` when prompted about the ClojureScript REPL type

- Select the Figwheel build to run *when* prompted for it. (e.g. `:dev`)

- Look at the `dev/user.clj` to see the list of the tasks to execute in the nREPL

- `M-x cider-jack-in-cljs RET`. This will startup the nREPL server. `(fig-start)` will start with figwheel. After it is started up, we can use `(cljs-repl)` to enable clojurescript repl, and interactively play with the code from Emacs

## Additional optional setup

- `~/.clojure/deps.edn` looks like [this](https://gist.github.com/sivakon/49443c243109c8398e79a32d0d5b45f8). I added `rebel-readline` to the deps.

```
	$ clojure -A:rebel
```
Taken from [here](https://github.com/bhauman/rebel-readline)

## License

Copyright © 2018 Sivaram Konanki

Distributed under the Eclipse Public License either version 1.0 or (at your option) any later version.
