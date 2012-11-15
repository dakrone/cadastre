# [Cadastre](https://en.wikipedia.org/wiki/Cadastre)

A Clojure library designed to survey your clojure project and extract
meta information about it.

## Usage

This project is primarily used for
[lein-clojuredocs](https://github.com/dakrone/lein-clojuredocs). If
you want to use it from leiningen:

```clojure
[cadastre "0.1.1"]
```

To use Cadastre as a library:

```clojure
(ns foo
  (:require [cadastre.analyzer :refer :all]))

;; generate a map of clojure var metadata
(gen-clojure "/Users/hinmanm/src/clojure")

;; encode the map to json, filename is optional
(gen-clojure-json "/Users/hinmanm/src/clojure" "foo.json.gz")

;; generate a map of your project's var metadata
(gen-project-docs {:name "foo"
                   :group "org.bar"
                   :url "http://example.com"
                   :description "My thing"
                   :scm "http://github.com/foo/bar"
                   :license {:name "Eclipse Public License"
                             :url "http://www.eclipse.org/legal/epl-v10.html"}
                   :version "1.0"})

;; encode the map to json, filename is optional again
(gen-project-docs-json {...} "bar-1.0.json.gz")

;; read metadata from a file
(read-namespace (clojure.java.io/file "/Users/hinmanm/src/clj/cadastre/src/cadastre/analyzer.clj"))

;; serialize a map to a file, filename is optional
(serialize-project-info {...} "myfile.json.gz")

;; You can bind *verbose* to println status:
(binding [*verbose* true]
  (gen-clojure-json "/Users/hinmanm/src/clojure"))
;; [+] Processing clojure.core...
;; [+] Processing clojure.core.protocols...
;; [+] Processing clojure.core.reducers...
;; [+] Processing clojure.data...
;; [+] Processing clojure.inspector...
;; [+] Processing clojure.instant...
;; [+] Processing clojure.java.browse...
;; [+] Processing clojure.java.browse-ui...
;; [+] Processing clojure.java.io...
;; [+] Processing clojure.java.javadoc...
;; [+] Processing clojure.java.shell...
;; [+] Processing clojure.main...
;; [+] Processing clojure.parallel...
;; [+] Processing clojure.pprint...
;; [+] Processing clojure.reflect...
;; [+] Processing clojure.repl...
;; [+] Processing clojure.set...
;; [+] Processing clojure.stacktrace...
;; [+] Processing clojure.string...
;; [+] Processing clojure.template...
;; [+] Processing clojure.test...
;; [+] Processing clojure.test.junit...
;; [+] Processing clojure.test.tap...
;; [+] Processing clojure.uuid...
;; [+] Processing clojure.walk...
;; [+] Processing clojure.xml...
;; [+] Processing clojure.zip...
;; [-] Writing output to clojure-1.5.0-alpha6.json.gz
;; [=] Done generating clojure json.gz file.
```

Example json output can be found [here (for cheshire)](https://gist.github.com/3880616)

## See Also

- [lein-clojuredocs](http://github.com/dakrone/lein-clojuredocs)
- [eisago](http://github.com/dakrone/eisago)

## License

Copyright © 2012 Lee Hinman

Distributed under the Eclipse Public License, the same as Clojure.
