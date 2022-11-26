# Aries Cloudagent Python Sandbox
# Making use of cloudagent-python

The instructions provided at https://github.com/hyperledger/aries-cloudagent-python/blob/main/DevReadMe.md#running do not allow the agent to start. 

The following does allow the agent to start although the parameter values used are not 'real' values and would, almost certainly, produce difficulties if used in the real world.

```
(aries-cloudagent-python) 1 rshea@cosi:~/dev/aries-cloudagent-python$ aca-py start --inbound-transport http 0.0.0.0 8000 --inbound-transport ws 0.0.0.0 8001 --outbound-transport ws --outbound-transport http --endpoint https://example.com/agent-endpoint --no-ledger

::::::::::::::::::::::::::::::::::::::::::::::
:: Aries Cloud Agent                        ::
::                                          ::
::                                          ::
:: Inbound Transports:                      ::
::                                          ::
::   - http://0.0.0.0:8000                  ::
::   - ws://0.0.0.0:8001                    ::
::                                          ::
:: Outbound Transports:                     ::
::                                          ::
::   - http                                 ::
::   - https                                ::
::   - ws                                   ::
::   - wss                                  ::
::                                          ::
:: Administration API:                      ::
::                                          ::
::   - not enabled                          ::
::                                          ::
::                               ver: 0.7.5 ::
::::::::::::::::::::::::::::::::::::::::::::::

```

