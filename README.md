# Magma-FED-Integ-Test

## Deploy AGW:
```
cd magma/lte/gateway
vagrant up magma
vagrant ssh magma

# inside vagrant vm
cd magma/lte/gateway
make run

# exit from vagrant vm
exit
```

## Deploy FEG:
```
cd magma/lte/gateway
vagrant up magma
vagrant ssh magma

# inside vagrant vm
cd magma/lte/gateway/python/integ_tests/federated_tests/docker
docker-compose build
./run.py
```

## Deploy Orc8r and register FEG:
```
cd magma/orc8r/cloud/docker
./build.py -a
./run.py

# return to agw folder
cd magma/lte/gateway
# register gateways
fab --fabfile=dev_tools.py register_federated_vm
fab --fabfile=dev_tools.py register_feg_gw
```

## Spin up Test VM:
```
cd magma/lte/gateway
vagrant up magma_test
vagrant ssh magma_test

# inside vagrant vm
cd magma/lte/gateway/python
make

# exit from vagrant vm
exit
```

## Spin up Traffic VM:
```	
cd magma/lte/gateway
vagrant up magma_trfserver
```
## Running Test:
```	
cd magma/lte/gateway
vagrant ssh magma_test

# inside vagrant vm
cd magma/lte/gateway/python/integ_tests
## Individual test(s), e.g.:
make fed_integ_test TESTS=s1aptests/test_attach_detach.py

## All tests
make fed_integ_test

# once the tests are done, you can exit the vagrant vm
exit
```
