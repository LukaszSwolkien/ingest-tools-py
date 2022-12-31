# Ingest-Tools-Python
Sample python scripts to send data into Splunk O11y suite. 

## Usage examples:

Create your organisation using Splunk API (see [here](https://github.com/LukaszSwolkien/ingest-tools)), and setup access tokens.
Remember to set all necessery secrets in the `.secrets.yaml` file

### Custom metric samples (SignalFx format):
Note! Those examples use `signalfx` python library. To learn more about signalfx library: https://github.com/signalfx/signalfx-python

```bash
./crypto.py ethereum
./stock.py SPLK
```

* The python `crypto.py` script collects publicly available market data on a given cryptocurrency and sends selected metrics to the Splunk o11y suite.

* The python `stock.py` exchange script collects information about a given stock symbol and sends the selected data to the Splunk o11y suite

You can run any script periodicaly as a cron job, for example:

```crontab -e```

```vim
5 4 * * 1-5 /home/ec2-user/Devel/test_integration/stock.py SPLK
```

## Setup project 
### Create `.secrets.yaml` file with tokens and endpoints defined, for example:

```yaml
splunk-ingest-token: "your_access_token"
splunk-api-token: "your_access_token"
splunk-ingest: "https://ingest.{realm}.signalfx.com"
splunk-api: "https://api.{realm}.signalfx.com/v2/integration"
```

### Create virtual environment

```bash
python3 -m venv venv
```

### Activate venv and install dependencies

```bash
. ./venv/bin/activate
pip install -r req.txt
```
