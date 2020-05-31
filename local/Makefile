REMOTE_SERVERS=`docker ps | grep local_server | grep -o '\local_server_.' | tr '\n' ','`
OUTPUT_NAME=`date '+%Y%m%d-%H%M%S'`
USERS_COUNT ?= 10
REPEAT_COUNT ?= 5
PLAN_TEST_NAME ?= "sample.jmx"
SERVERS ?= 5
DIRECTORY_TEST ?= ""

compose:
	@docker-compose up -d

scale:
	@docker-compose scale server=$(SERVERS)

running_test:
	@docker exec -it local_master_1 jmeter -Jserver.rmi.ssl.disable=true -DTHREAD_USERSl=$(USERS_COUNT) -DLOOP_COUNT=$(REPEAT_COUNT) -n -t bin/plan/$(DIRECTORY_TEST)$(PLAN_TEST_NAME) -l bin/plan/$(DIRECTORY_TEST)result-$(OUTPUT_NAME).jtl -e -o bin/plan/$(DIRECTORY_TEST)dashboard_$(OUTPUT_NAME) -R$(REMOTE_SERVERS)

teste:
	@echo $(DIRECTORY_TEST)
