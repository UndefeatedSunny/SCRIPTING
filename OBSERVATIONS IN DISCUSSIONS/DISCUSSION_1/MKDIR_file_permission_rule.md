    When using -m with -p, the permissions will be given only to the last directory in the hierarchy.

    For example:
    mkdir -m 777 -p d1/d2/d3

    d3 will have the mode set by -m. d1 and d2 will have default permissions.
