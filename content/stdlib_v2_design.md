# Design Principles For Stdlib 2.0

## Design Goals
* Create a more user-friendly, modern interface for OCaml's stdlib.
* Keep data structure compatibility.
* Lay out good principles for API design.
* Apply useful lessons from other stdlibs (Containers, Base, Batteries)
* Keep the underlying machinery for OS interaction stable.
* Controversial: avoid polymorphic comparison (see Containers, Core)

## Ideas
These are ideas that may not be doable, but are worth considering:

### Redesigning channels
(suggested by @companion-cube)
Channels as they are right now are simple file handles.
While these could remain as low level entities, it would be nice to have a more flexible
abstraction for a stream, as exists in other languages.
These streams could wrap each other, allowing for additional capabilities,
such as compression, buffering, etc.

## Hypothetical Module List

This is a hypothetical list of modules that would be included in the V2 stdlib:

### Data Structures

* List
* Array
* BigArray
* String
* Bytes
* Buffer
* BigString?
* Set
* Map
* Hashtbl
* Hashtrie?
* Stack
* Heap
* Queue
* Dequeue? (see Containers.Data.Dequeue)
* FQueue (functional queue)?
* FStack (functional stack)?
* Vector
* WeakArray? (from Weak)
* WeakHash? (from Weak)

### Data Types

* Int/32/64/NativeInt
* Float
* Bool
* Char?
* Uchar (expanded)
* Option
* Result
* Lazy
* Pair? (see Containers.CCPair)

### OS

* Path
* File
* Dir
* IO (see [CCIO](https://github.com/c-cube/ocaml-containers/blob/master/src/core/CCIO.mli))
* Process
* Mutex
* Thread
* Socket (from Unix)
* Time (from Unix & Sys)

### Utilities

* Arg
* Marshal
* Printf (unify with Format?)
* Random
* Regex (incorporate ocamlre)
* Terminal? (from Unix)
