#SHELL:=/bin/zsh

stage: 
	@@echo 'Deplying site to staging server.'
	@@rsync -arvuz SlickAppTheme/HTML/ asmoll01@staging.babygrowapp.com:staging.babygrowapp.com/ --exclude '.git' --exclude '.hg' --exclude '.hgcheck' --exclude 'build' --delete

deploy: 
	@@while true; do \
		read -p "Deploy site to production server? " yn ;\
		case $$yn in \
			[Yy]* ) break;; \
			[Nn]* ) break;; \
			* ) echo "Please answer yes or no.";; \
		esac ;\
	done; \
	echo yn: $$yn;\
	\
	if [[ $$yn =~ [Nn]* ]]; then echo "Aborting."; false; fi; \
	echo 'Deploying.'; \
	rsync -arvuz SlickAppTheme/HTML/ asmoll01@staging.babygrowapp.com:babygrowapp.com/ --exclude '.git' --exclude '.hg' --exclude '.hgcheck' --exclude 'build' --delete

.PHONY: server render build minify deploy
