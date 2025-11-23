# What is THIS?

libdepixelize links to 2geom. But that doesn't work in Meson because they're two separate CMake projects, completely isolated, so doing:

```
target_link_libraries(TARGET 2Geom::2Geom)
```

didn't work. For that reason, we put 2geom and libdepixelize in the same CMake project, and include their targets.
