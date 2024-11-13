all: ja/index.html \
	ja/man/manpage.css \
	ja/man/rbenv.1.html \
	ja/man/ruby-build.1.html
.PHONY: all

ja/man/rbenv.1.html: vendor/rbenv/translation/ja/share/man/man1/rbenv.1.adoc
	asciidoctor \
		-b html5 \
		-a linkcss \
		-a stylesheet=manpage.css \
		-a 'webfonts!' \
		-a idprefix= \
		-o $@ \
		$<

vendor/rbenv/translation/ja/share/man/man1/rbenv.1.adoc:
	${MAKE} \
		--directory vendor/rbenv/translation \
		ja/share/man/man1/rbenv.1.adoc

ja/man/ruby-build.1.html: vendor/ruby-build/translation/ja/share/man/man1/ruby-build.1.adoc
	asciidoctor -b html5 -a linkcss -a stylesheet=manpage.css -a 'webfonts!' -a idprefix= -o $@ $<

vendor/ruby-build/translation/ja/share/man/man1/ruby-build.1.adoc:
	${MAKE} --directory vendor/ruby-build/translation ja/share/man/man1/ruby-build.1.adoc

ja/man/manpage.css: ../man/manpage.css
	mkdir -p $(dir $@)
	cp $< $@

ja/index.html: XHTML/index.html po4a.cfg po/en.pot credit.html po/ja.po
	po4a po4a.cfg

po/en.pot:
	touch $@

XHTML/index.html: ../index.html
	mkdir -p $(dir $@)
	./HTML-to-XHTML < $< > $@

update:
	git submodule update --recursive --remote --force
.PHONY: update

clean:
	rm -f \
		ja/man/rbenv.1.html \
		ja/man/ruby-build.1.html \
		vendor/rbenv/translation/ja/share/man/man1/rbenv.1.adoc \
		vendor/ruby-build/translation/ja/share/man/man1/ruby-build.1.adoc \
		vendor/rbenv/translation/ja/share/man/man1/rbenv.1.adoc \
		vendor/ruby-build/translation/ja/share/man/man1/ruby-build.1.adoc
.PHONY: clean
