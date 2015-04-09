--- /dev/null
+++ b/Makefile
@@ -0,0 +1,48 @@
+prefix=$(DESTDIR)/opt/microsoft/msodbcsql/11.0.2270.0
+bindir=$(prefix)/bin
+libdir=$(prefix)/lib
+sysconfdir=$(prefix)/etc
+includedir=$(prefix)/include
+docdir=$(prefix)/en_US/docs
+
+driver_name="Microsoft ODBC Driver 11 for SQL Server";
+driver_dm_name="ODBC Driver 11 for SQL Server"
+driver_file="libmsodbcsql-11.0.so.2270.0"
+
+
+all:
+
+install: msodbcsql.ini
+	install -d $(prefix)
+	install WARNING $(prefix)
+	install LICENSE $(prefix)
+	install -d $(libdir)
+	ln -s /lib/x86_64-linux-gnu/libssl.so.1.0.0 $(libdir)/libssl.so.10
+	ln -s /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 $(libdir)/libcrypto.so.10
+	install lib64/libmsodbcsql-11.0.so.2270.0 $(libdir)
+	install lib64/msodbcsqlr11.rll $(libdir)
+	install -d $(bindir)
+	install bin/bcp-11.0.2270.0 $(bindir)
+	install bin/sqlcmd-11.0.2270.0 $(bindir)
+	install -d $(docdir)
+	tar -C $(docdir) -xz -f docs/en_US.tar.gz
+	install -d $(prefix)/en_US
+	install bin/BatchParserGrammar.dfa $(prefix)/en_US
+	install bin/BatchParserGrammar.llr $(prefix)/en_US
+	install bin/bcp.rll $(prefix)/en_US
+	install bin/SQLCMD.rll $(prefix)/en_US
+	install -d $(includedir)
+	install include/msodbcsql.h $(includedir)
+	install -d $(sysconfdir)
+
+msodbcsql.ini:
+	echo "[$(driver_dm_name)]" > msodbcsql.ini
+	echo "Description = $(driver_name)" >> msodbcsql.ini
+	echo "Driver = $(libdir)/$(driver_file)" >> msodbcsql.ini
+	echo "Threading = 1" >> msodbcsql.ini
+	echo "" >> msodbcsql.ini
+
+clean:
+	-rm msodbcsql.ini
+
+.PHONY: clean
