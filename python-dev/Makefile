#Python & virtualenv config
PYTHON := /usr/bin/python3
VIRTUALENV = /usr/bin/virtualenv
VIRTUALENVDIR := virtenv
REQFILE := requirements.txt
VIRTENV_PIP = $(abspath $(VIRTUALENVDIR)/bin/pip3)

#Docker config
COMPOSE := /usr/bin/docker-compose
COMPOSEFILE := docker-compose.yml

#FANCY COLOR TAGGING for better visaualization
T1 := ----\e[1m\e[33m
T1C := \e[0m----

virtualenv:
	@echo -e "$(T1)Creating virtualenv$(T1C)"
	mkdir -p $(VIRTUALENVDIR)
	$(VIRTUALENV) $(VIRTUALENVDIR)

installreq:
	@echo -e "$(T1)Activating virtualenv$(T1C)"
	. $(abspath $(VIRTUALENVDIR)/bin/activate)
	@echo -e "$(T1)Installing Python packages from $REQFILE$(T1C)"
	$(VIRTENV_PIP) install -r $(REQFILE)
	@echo "Installed python pacakges:"
	@$(VIRTENV_PIP) list --format=columns | grep "`cat $(REQFILE)`";

full-env:

#DOCKER ENV

compose-up:
	@echo "----\e[33mDOCKER: creating full environment----"
	@$(COMPOSE) -v
	docker-compose -d -f $(COMPOSEFILE) up
	docker-compose -f $(COMPOSEFILE) ps

clean:
	#Remove everything that connect to this project
	@echo -e "$(T1)Remove virtualenv: $(VIRTUALENVDIR) - cache files, directories, etc $(T1C)"
	rm -rf $(VIRTUALENVDIR)

help:
	#HELP here

.PHONY: help
