# Callflows

## About Callflows

Callflows are the instructions Kazoo uses to process a call. A callflow includes a list of numbers or regex patterns used by Kazoo to determine what callflow is used when a call comes in for an account. The `flow` parameter defines the tree of actions, allowing branching (such as in the `menu` action) and chaining actions together. You can also branch to other callflows and execute its `flow` (useful to avoid recreating the same sub-flow structure).

#### Schema

Call flows describe steps to take in order to process a phone call. They are trees of information related to a phone call such as "answer, play file, record file" etc. that are logically grouped together and ordered.



Key | Description | Type | Default | Required | Support Level
--- | ----------- | ---- | ------- | -------- | -------------
`featurecode.name` |   | `string(1..128)` |   | `false` |  
`featurecode.number` |   | `string(1..30)` |   | `false` |  
`featurecode` | When the callflow is used as a featurecode this object tracks the intended match of the pattern and name of the feature | `object()` |   | `false` |  
`flags.[]` |   | `string()` |   | `false` | `supported`
`flags` | Flags set by external applications | `array(string())` |   | `false` | `supported`
`flow` | A callflow node defines a module to execute, data to provide to that module, and zero or more children to branch to | [#/definitions/callflows.action](#callflowsaction) |   | `false` |  
`metaflow` | Actions applied to a call outside of the normal callflow, initiated by the caller(s) | [#/definitions/metaflows](#metaflows) |   | `false` |  
`name` | Friendly name of the callflow | `string()` |   | `false` |  
`numbers.[]` |   | `string(1..36)` |   | `false` |  
`numbers` | A list of static numbers that the callflow should execute for | `array(string(1..36))` | `[]` | `false` |  
`patterns.[]` |   | `string(1..)` |   | `false` |  
`patterns` | A list of regular expressions that the callflow should execute for, with optional capture groups | `array(string(1..))` | `[]` | `false` |  
`ringback.early` | Media ID for the early ringback media | `string()` |   | `false` |  
`ringback.transfer` | Media ID for transfer ringback media | `string()` |   | `false` |  
`ringback` | Ringback settings for early media and transfers | `object()` |   | `false` |  

### callflows.action

Call flows describe steps to take in order to process a phone call. They are trees of information related to a phone call such as "answer, play file, record file" etc. that are logically grouped together and ordered.


Key | Description | Type | Default | Required | Support Level
--- | ----------- | ---- | ------- | -------- | -------------
`children./.+/` | Call flows describe steps to take in order to process a phone call. They are trees of information related to a phone call such as "answer, play file, record file" etc. that are logically grouped together and ordered. | [#/definitions/callflows.action](#callflowsaction) |   | `false` |  
`children` | Children callflows | `object()` |   | `false` |  
`data` | The data/arguments of the callflow module | `object()` | `{}` | `true` |  
`module` | The name of the callflow module to execute at this node | `string(1..64)` |   | `true` |  

### metaflow

A metaflow node defines a module to execute, data to provide to that module, and one or more children to branch to


Key | Description | Type | Default | Required | Support Level
--- | ----------- | ---- | ------- | -------- | -------------
`children./.+/` | A metaflow node defines a module to execute, data to provide to that module, and one or more children to branch to | [#/definitions/metaflow](#metaflow) |   | `false` |  
`children` | Children metaflows | `object()` |   | `false` |  
`data` | The data/arguments of the metaflow module | `object()` | `{}` | `false` |  
`module` | The name of the metaflow module to execute at this node | `string(1..64)` |   | `true` |  

### metaflows

Actions applied to a call outside of the normal callflow, initiated by the caller(s)


Key | Description | Type | Default | Required | Support Level
--- | ----------- | ---- | ------- | -------- | -------------
`binding_digit` | What DTMF will trigger the collection and analysis of the subsequent DTMF sequence | `string('1' | '2' | '3' | '4' | '5' | '6' | '7' | '8' | '9' | '0' | '*' | '#')` | `*` | `false` |  
`digit_timeout` | How long to wait between DTMF presses before processing the collected sequence (milliseconds) | `integer()` |   | `false` |  
`listen_on` | Which leg(s) of the call to listen for DTMF | `string('both' | 'self' | 'peer')` |   | `false` |  
`numbers./^[0-9]+$/` | A metaflow node defines a module to execute, data to provide to that module, and one or more children to branch to | [#/definitions/metaflow](#metaflow) |   | `false` |  
`numbers` | A list of static numbers with their flows | `object()` |   | `false` |  
`patterns./.+/` | A metaflow node defines a module to execute, data to provide to that module, and one or more children to branch to | [#/definitions/metaflow](#metaflow) |   | `false` |  
`patterns` | A list of patterns with their flows | `object()` |   | `false` |  



## Fetch

> GET /v2/accounts/{ACCOUNT_ID}/callflows

```shell
curl -v -X GET \
    -H "X-Auth-Token: {AUTH_TOKEN}" \
    http://{SERVER}:8000/v2/accounts/{ACCOUNT_ID}/callflows
```

## Create a new callflow

> PUT /v2/accounts/{ACCOUNT_ID}/callflows

```shell
curl -v -X PUT \
    -H "X-Auth-Token: {AUTH_TOKEN}" \
    http://{SERVER}:8000/v2/accounts/{ACCOUNT_ID}/callflows
```

## Remove a callflow

> DELETE /v2/accounts/{ACCOUNT_ID}/callflows/{CALLFLOW_ID}

```shell
curl -v -X DELETE \
    -H "X-Auth-Token: {AUTH_TOKEN}" \
    http://{SERVER}:8000/v2/accounts/{ACCOUNT_ID}/callflows/{CALLFLOW_ID}
```

## Fetch a callflow's details

> GET /v2/accounts/{ACCOUNT_ID}/callflows/{CALLFLOW_ID}

```shell
curl -v -X GET \
    -H "X-Auth-Token: {AUTH_TOKEN}" \
    http://{SERVER}:8000/v2/accounts/{ACCOUNT_ID}/callflows/{CALLFLOW_ID}
```

## Patch a callflow object

> PATCH /v2/accounts/{ACCOUNT_ID}/callflows/{CALLFLOW_ID}

```shell
curl -v -X PATCH \
    -H "X-Auth-Token: {AUTH_TOKEN}" \
    http://{SERVER}:8000/v2/accounts/{ACCOUNT_ID}/callflows/{CALLFLOW_ID}
```

## Change a callflow object

> POST /v2/accounts/{ACCOUNT_ID}/callflows/{CALLFLOW_ID}

```shell
curl -v -X POST \
    -H "X-Auth-Token: {AUTH_TOKEN}" \
    http://{SERVER}:8000/v2/accounts/{ACCOUNT_ID}/callflows/{CALLFLOW_ID}
```
