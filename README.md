A Clojerl library for reading and writing comma (and other) separated values.

Credit goes to https://github.com/testdouble/clojurescript.csv, as this is a trivial port.

## Installation

Assuming, you are familiar with Clojerl projects using Rebar3, here is how you add the latest version as a dependency to your project's rebar.config:
```erlang
  {deps, [
          {clojerl, "0.6.0"}
         ,{data_csv, {git, "https://github.com/laczoka/data.csv.git", {branch, "master"}}}
         ]}.
```

## Usage

```clojure
(ns my.domain.core
  (:require [clojure.data.csv :as csv]))

;; Basic usage
(csv/write-csv [[1 2 3] [4 5 6]])
;;=> "1,2,3\n4,5,6"

;; Define your own separator
(csv/write-csv [[1 2 3] [4 5 6]] :separator "|")
;;=> "1|2|3\n4|5|6"

;; Use either :lf (default) or :cr+lf as the newline character
(csv/write-csv [[1 2 3] [4 5 6]] :newline :cr+lf)
;;=> "1,2,3\r\n4,5,6"

;; Quote fields
(csv/write-csv [["1,000" "2" "3"] ["4" "5,000" "6"]] :quote? true)
;;=> ""1,000","2","3"\n"4","5,000","6""
```

## Development

Get the source code and compile it

```bash
  git clone https://github.com/laczoka/data.csv.git
  cd data.csv
  rebar3 clojerl compile
```

Run the tests

```bash
  rebar3 clojerl run tests --ns clojure.data.csv-test
```

## Contributing

We welcome all contributors to the project. Please submit an [Issue](https://github.com/laczoka/data.csv/issues)
and a
[Pull Request](https://github.com/laczoka/data.csv/pulls)
if you have one.

## License

Copyright © 2014 Test Double

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
