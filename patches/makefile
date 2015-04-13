--- /dev/null
+++ b/Makefile
@@ -0,0 +1,49 @@
+prefix=/opt/microsoft/msodbcsql/11.0.2270.0
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
+	install -d $(DESTDIR)/$(prefix)
+	install WARNING $(DESTDIR)/$(prefix)
+	install LICENSE $(DESTDIR)/$(prefix)
+	install -d $(DESTDIR)/$(libdir)
+	ln -s /lib/x86_64-linux-gnu/libssl.so.1.0.0 $(DESTDIR)/$(libdir)/libssl.so.10
+	ln -s /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 $(DESTDIR)/$(libdir)/libcrypto.so.10
+	install lib64/libmsodbcsql-11.0.so.2270.0 $(DESTDIR)/$(libdir)
+	install -d $(DESTDIR)/$(bindir)
+	install bin/bcp-11.0.2270.0 $(DESTDIR)/$(bindir)
+	install bin/sqlcmd-11.0.2270.0 $(DESTDIR)/$(bindir)
+	install -d $(DESTDIR)/$(docdir)
+	tar -C $(DESTDIR)/$(docdir) -xz -f docs/en_US.tar.gz
+	install -d $(DESTDIR)/$(prefix)/en_US
+	install lib64/msodbcsqlr11.rll $(DESTDIR)/$(prefix)/en_US
+	install bin/BatchParserGrammar.dfa $(DESTDIR)/$(prefix)/en_US
+	install bin/BatchParserGrammar.llr $(DESTDIR)/$(prefix)/en_US
+	install bin/bcp.rll $(DESTDIR)/$(prefix)/en_US
+	install bin/SQLCMD.rll $(DESTDIR)/$(prefix)/en_US
+	install -d $(DESTDIR)/$(includedir)
+	install include/msodbcsql.h $(DESTDIR)/$(includedir)
+	install -d $(DESTDIR)/$(sysconfdir)
+	install msodbcsql.ini $(DESTDIR)/$(sysconfdir)
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
