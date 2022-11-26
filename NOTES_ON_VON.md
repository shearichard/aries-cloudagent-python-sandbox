When I
http://greenlight.bcovrin.vonx.io/



Seed: richard0000000000000000000000000
DID: Lz5GQiq5eSxXaoLi7CLsHL
Verkey: BtjbndyyPL1Db5vAf3UnvqGjb3RcyPC9bRzi1CtqUEoo

============================================================
When I tried the following ... 

```
aca-py start \
  --label Alice \
  -it http 0.0.0.0 8000 \
  -ot http \
  --admin 0.0.0.0 8001 \
  --admin-insecure-mode \
  --genesis-url http://localhost:9000/genesis \
  --seed richard0000000000000000000000000 \
  --endpoint http://localhost:8000/ \
  --debug-connections \
  --public-invites \
  --wallet-type indy \
  --wallet-name Alice \
  --wallet-key BtjbndyyPL1Db5vAf3UnvqGjb3RcyPC9bRzi1CtqUEoo
```

... based on, although slightly adapted from, https://ldej.nl/post/becoming-a-hyperledger-aries-developer-part-3-connecting-using-swagger/ . I got the following response ...

```
ConnectionRefusedError: [Errno 111] Connect call failed ('127.0.0.1', 9000)
```

... which seemed to suggest that I was meant to have setup the Swagger instance myself ?


Based on what it says here https://ldej.nl/post/becoming-a-hyperledger-aries-developer-part-2-development-environment/ it seems it might be worth running a VON instance locally.

OK so I followed the instructions at https://github.com/bcgov/von-network#running-the-web-server-on-your-local-machine after I had tried to run the Docker images but came up with error messages.

Trying to get it working using a Python virtual environment also had its problems.

Before I got the 

```
pip install -r server/requirements.txt
```

to run cleanly (it kept choking on the build of the `multidict` wheel, I had to do the following. 

```
sudo apt-get install python3-dev
pip install multidict
pip install --upgrade pip wheel
sudo apt-get install python3 python-dev python3-dev build-essential
sudo apt-get install python3.9-dev
```
I'm pretty sure not all of it was necessary and after the last one then the `pip install ...` ran cleanly. 

After that tried starting Von as follows ...
```
(venv) rshea@tana:~/dev/von-network$ GENESIS_FILE=~/dev/aries-cloudagent-python-sandbox/genesis-file-downloaded-from-von.txt PORT=9000 python -m server.server
```

... but then I got a problem with jinja2. I downgraded it to 3.0.2 and that resolved that problem. I then tried again and I got a problem with not being able to find 'indy' and I have been unable to resolve that problem. I can only think that 'indy' used to be a module and it is no longer but where the functions that used to be in 'indy' now are is not known to me. I have put a question on von-network github repos.

