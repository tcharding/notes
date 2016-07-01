OpenBazaar and Related 
======================

Requires Python2, use virtualenv

virtualenv: ~/build/python/virtualenv/openbazaar

aliases:
workon_ob
workoff_ob

start server
python openbazaard.py start --testnet

start client
npm start

test
nosetests -vs --with-coverage --cover-package=dht --cover-package=db --cover-package=market --cover-inclusive ./dht/tests ./db/tests ./market/tests


