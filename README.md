TeamSpeak Server Virtual User Connections GROK pattern for Graylog
==================================================================

Pattern
-------

	"name":"TEAMSPEAK3_USER_CONNECTED"
	"pattern":"%{TIMESTAMP_ISO8601:log_ts_timestamp}\|%{WORD:log_ts_level}%{GREEDYDATA}\|%{WORD:log_ts_module}%{GREEDYDATA}\|%{POSINT:log_ts_virtualserver}%{GREEDYDATA}\|%{DATA:log_ts_action} \'%{DATA:log_ts_user}\'\(id:%{POSINT:log_ts_client_dbid}\) from %{IP:log_ts_client_ip}"

	"name":"TEAMSPEAK3_USER_DISCONNECTED"
	"pattern":"%{TIMESTAMP_ISO8601:log_ts_timestamp}\|%{WORD:log_ts_level}%{GREEDYDATA}\|%{WORD:log_ts_module}%{GREEDYDATA}\|%{POSINT:log_ts_virtualserver}%{GREEDYDATA}\|%{DATA:log_ts_action} \'%{DATA:log_ts_user}\'\(id:%{POSINT:log_ts_client_dbid}\) reason \'reasonmsg=%{GREEDYDATA:log_ts_client_reasonmsg}\'"

Example message
---------------

	2018-05-01 22:03:11.818173|INFO    |VirtualServerBase|1  |client connected 'User1'(id:999) from 127.0.0.1:52764
	
	2018-05-01 22:41:14.310749|INFO    |VirtualServerBase|1  |client disconnected 'User1'(id:999) reason 'reasonmsg=leaving'

Fields
------

    log_ts_action: client connected
    log_ts_client_dbid: 999
    log_ts_client_ip: 127.0.0.1
    log_ts_level: INFO
    log_ts_module: VirtualServerBase
    log_ts_timestamp: 2018-05-01 22:03:11.818173
    log_ts_user: User1
    log_ts_virtualserver: 1
    
    log_ts_action: client disconnected
    log_ts_client_dbid: 999
    log_ts_client_reasonmsg: leaving
    log_ts_level: INFO
    log_ts_module: VirtualServerBase
    log_ts_timestamp: 2018-05-01 22:41:14.310749
    log_ts_user: User1
    log_ts_virtualserver: 1


Installation
------------

Go to **Graylog Web Interface** -> **System** -> **Content Packs** then select *content_pack.json* file and upload it.

[![screen1](https://i.imgbox.com/HAsDC4FR.png)](https://i.imgbox.com/wP2n4HXH.png)