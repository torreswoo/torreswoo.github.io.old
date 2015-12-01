## slack.js
```javascript
// https://github.com/clonn/slack-node-sdk
 var Slack = require('slack-node');

 webhookUri = "https://hooks.slack.com/services/........"; // torreswoo.slack.com

 var config = {
    channel : "#general",
    username : "jira",
    text : "this is message"
 };

 slack = new Slack();
 slack.setWebhook(webhookUri);

 slack.webhook( config, function(error, response){
    console.log(response)
    console.log(error);
 });
```

## jira.js
```javascript
// https://github.com/steves/node-jira/blob/master/lib/jira.js

var http = require('http');  // HTTP server
var JiraApi = require('jira').JiraApi;

var config = {
   protocol : 'http',
   host : 'jira.skplanet.com',
   port : 80,
   user : '....',
   password : '...',
   version :'2'
};
var jira = new JiraApi(config.protocol,
                       config.host,
                       config.port,
                       config.user,
                       config.password,
                       config.version
                       );
jira.getProject('PLIN', function(error, project){
   for (var key in project){
      console.log(project[key]);
   }

});


//jira.findIssue('PLIN-12', function(error, issue) {
//       //console.log('Status: ' + issue.fields.status.name);
//   console.log('Status: ' + issue.fields.project.name);

//   for (var key in issue ){
//      console.log(issue[key]);
//   }
//});
```
