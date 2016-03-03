# Specifications for *DiscreteZOO* objects

This repository contains JSON files defining the specifications of objects used in *DiscreteZOO*.
The specifications are shared by both the core and the Sage interface.

## File format

Each file is named for the class of the object that it specifies and has a `.json` extension indicating its format.
It contains an object with the following fields:
* `name`: the name of the table conatining instances of the class;
* `primary_key`: the name of the property acting as the primary key;
* `indices`: a list of any of the following:
    + a name of a property to be indexed,
    + a list with two elements:
        - a name of a property of a list of names of properties to be indexed, and
        - a list of constraints on the index (currently only `"unique"` is supported);
* `skip`: a list of names of properties to be left out from the object dictionary (e.g. construction data);
* `noupdate`: a list of names of properties which should not be automatically updated;
* `fields`: an object with a field for each property, having one of the following values:
    + a data type (`"Integer"`, `"Rational"`, `"RealNumber"`, `"bool"`, `"str"` or any of the *DiscreteZOO* classes), or
    + an object with the following fields:
        - `class`: the name of the metaclass to be used,
        - `params`: an object with named parameters to the specified metaclass, each having as value an object of the same form as the `fields` field of the toplevel object,
        - the fields `indices`, `skip`, `noupdate`, `fieldparams`, `aliases`, `compute` or `default` as in the toplevel object;
* `fieldparams`: an object containing a list of parameters (`"autoincrement"`, `"not_null"`, `"unique"`) for each property (empty lists need not be specified);
* `aliases`: an object with aliases for properties,
* `compute`: an object containing a list of properties for each superclass which are computed upon creation of a new *DiscreteZOO* object (empty lists need not be specified);
* `default`: an object containing an object with default values of properties for each superclass (empty objects need not be specified).
