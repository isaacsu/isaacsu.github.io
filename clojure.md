# clj-time recipes

### Dependency

Add to ```project.clj```.

```clojure
(defproject project-name "0.1.0"
  ...
  :dependencies [[org.clojure/clojure "1.5.1"]
                [clj-time "0.6.0"]])
```

### Common require
```clojure
(require '[clj-time.core   :as ct-core])
(require '[clj-time.format :as ct-format])
```

#### Parse a date string to UTC time

Convert ```"2014-01-01"``` to a ```org.joda.time.DateTime``` object.

Assumes string refers to UTC timezone.

```clojure
(def my-formatter (ct-format/formatter "yyyy-MM-dd"))
(ct-format/parse my-formatter "2014-01-01")
; => #<DateTime 2014-01-01T00:00:00.000Z>
```
#### Parse a date string to local time
Convert ```"2014-01-01"``` to a ```org.joda.time.DateTime``` object.

Assumes string refers to local machine timezone.

```clojure
(def my-formatter (ct-format/formatter-local "yyyy-MM-dd"))
(ct-format/parse my-formatter "2014-01-01")
; => #<DateTime 2014-01-01T00:00:00.000+10:00>
```

#### DateTime object to string

Renders a ```org.joda.time.DateTime``` object as ```"dd/MM/yyyy"```.

```clojure
(def my-formatter (ct-format/formatter "dd/MM/yyyy"))
(def my-datetime (ct-core/date-time 2014 05 01)) 
; => #<DateTime 2014-05-01T00:00:00.000Z>

(ct-format/unparse my-formatter my-datetime)
; => "01/05/2014"
```

