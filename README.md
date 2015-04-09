Debian Packaging for Microsoft ODBC Driver

This is some real quick work dashed off to enable packaging of the Microsoft ODBC driver for Linux into a .deb

# Use:

* Make sure libssl1.0.0 is installed
* Download the ODBC driver version 11.0.2270.0
* Rename tarball to `msodbcsql_11.0.2270.0.orig.tar.gz`
* expand tarball
* Clone this repository into newly created directory
* debuild -us -uc

# Notes:

* this package does break things pretty bad: installs to /opt, but that's a requirement for the driver to function as the path to some supporting files is hard-coded into the library.

* the driver is also linked against `libcrypto.so.10` and `libssl.so.10` because RedHat, I guess.  The traditional way to do this is to make links in `/usr` that point these names to the Debian equivalents (e.g. `libcrypto.so.1.0.0`).  Rather than clutter up /usr, I've installed these inside the `/opt` directory where the ODBC library is installed.  The downside is that you will need to set `LD_LIBRARY_PATH` for things to function.

* this appears to work with the Trusty version of unixODBC (2.2.14p2), though the msodbcsql readme indicates that 2.3.2 is required. YMMV, something will undoubtedly break.  Hoping it might get picked up in backports.

# Disclaimer:

No guarantees, y'all- might not function, might melt down your data center and turn your dog against you.  It's ugly- help welcomed, I hope to improve this over time.

