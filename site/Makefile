SHELL:=/bin/zsh
CSSFILES:=$(shell find _site -regex '.*\.css')

server:
	@@jekyll --server --auto

render:
	@@echo "Building the site..."
	@@jekyll --no-future

minify:

	@@echo "Minifying the CSS..."
	for cssfile in $(CSSFILES) ; do \
		/usr/local/bin/yuicompressor --verbose --type css -o $$cssfile $$cssfile ; \
	done
	@@echo "Minifying the HTML..."
	@@/usr/local/bin/htmlcompressor -r --type html -o _site _site

build: render minify

stage: build
	@@echo 'Deplying site to staging server.'
	@@rsync -arvuz _site/ asmoll01@staging.babygrowapp.com:staging.babygrowapp.com/ --exclude '.git' --exclude '.hg' --exclude '.hgcheck' --exclude 'build' --delete

deploy: build
	@@echo 'Doing nothing.'

.PHONY: server render build minify deploy
