# sails-hook-push 

**DEPRECATED : NOT MAINTAINED ANYMORE** I'm using Trails now, if you want access to this repo to contribute and maintain it, please let me know.

Base on node-gcm and apn modules.

## Install : 

    npm install sails-hook-push

## Configuration :
You need a /config/push.js file under your sails project to configure your apis credential like this : 

    module.exports.push = {
    	gcm : {
    		senderId : "" //Server API key
    	},
    	apn : {
    		cert : "", //Path to cert file
    		key  : "", //Path to key file
    		/*
    		 ca         : [],
    		 pfx        : "",
    		 passphrase : "",
    		 production : NODE_ENV == "production",
    		 voip : false,
    		 port : 2195,
    		 rejectUnauthorized : true,
    		 cacheLength : 1000,
    		 autoAdjustCache : true,
    		 maxConnections : 1,
    		 connectTimeout : 10000,
    		 connectionTimeout : 3600000,
    		 connectionRetryLimit : 10,
    		 buffersNotifications : true,
    		 fastMode : false
    		 //more infos here : https://github.com/argon/node-apn/blob/master/doc/connection.markdown
    		 */
    	}
    };
    
## Usage : 
After install a new service is available. You can send GCM message/notification like this : 

    sails.services.pushnotification.sendGCMNotification("DEVICE_TOKEN", {
        data         : {
          key1 : 'message1',
          key2 : 'message2'
        },
        notification: {
          title: "Hello, World",
          icon: "ic_launcher",
          body: "This is a notification that will be displayed ASAP."
        }
      }, true, function (err, results)
      {
        console.log(err, results);
      });
More informations about parameters here : https://github.com/ToothlessGear/node-gcm#usage
      
For an APN notification : 

    sails.services.pushnotification.sendAPNNotification("DEVICE_TOKEN", {
        badge : 3,
        sound : "ping.aiff",
        alert : "new message",
        payload : {'messageFrom': 'Caroline'}
    });
More informations about parameters here : https://github.com/argon/node-apn#sending-a-notification
   
You can use sails.services.pushnotification or PushNotification if you have global services option enable on your sails project.
