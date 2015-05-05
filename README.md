# abcstats

Given one or more Alembic archives, this script will traverse each archive's objects and properties, and accumulate the following statistics:

* Number of files and total file size in bytes
* Number of IObjects
* Total occurrences of each schema
* Total array length of all array properties (keyed on schema name + property path)


## Example Output

The script will produce some output like this:

    Total AbcGeom_Camera_v1: 8
    Total AbcGeom_PolyMesh_v1: 10
    Total AbcGeom_PolyMesh_v1/.faceCounts: 2232
    Total AbcGeom_PolyMesh_v1/.faceIndices: 8712
    Total AbcGeom_PolyMesh_v1/N: 912
    Total AbcGeom_PolyMesh_v1/P: 2144
    Total AbcGeom_PolyMesh_v1/uv/.indices: 8064
    Total AbcGeom_PolyMesh_v1/uv/.vals: 2288
    Total AbcGeom_Xform_v3: 18
    Total File Count: 9
    Total File Size (Bytes): 4892874
    Total IObject Count (excl. top): 36
    Total IObject Count (incl. top): 45


## Usage

The `abcstats` script can be given one or more paths to alembic archives, e.g:

`abcstats box.abc sphere.abc`

If no file paths are given, the script will attempt to read a list of files via `stdin`. This is particularly handy for piping the results of `find` to the script, e.g:

`find . -name "*.abc" | abcstats`

The command can optionally take the following flags:

* `-h` / `--help`: print help message and exit
* `-d` / `--distinct`: filter out duplicate file paths (off by default)


## Requirements

To use this script, the Alembic python bindings must be available in your python environment.
