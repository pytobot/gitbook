# front-end

## Front-End

The Pytbot is build on Full Json communication on a REST Interface.  
Because almost every application has possibilities for a  REST interface integration, the possible choices for a front-end are and-less. 

When going to flow programming, and having a nice and easy environment to start learning to program. There a plenty of programming tools. On the Pytobot, 3 front-end tools will be included to control the basic of the robot. 

## NodeRed

Node-RED is a programming tool for wiring hardware devices together.

It provides a browser-based editor that makes it easy to wire together flows using the wide range of nodes in the palette that can be deployed to its runtime in a single-click.

![](../../.gitbook/assets/687474703a2f2f6e6f64657265642e6f72672f696d616765732f6e6f64652d7265642d73637265656e73686f742e706e67.png)

### Setup

```text
bash <(curl -sL https://raw.githubusercontent.com/node-red/raspbian-deb-package/master/resources/update-nodejs-and-nodered)
npm install node-red-dashboard
```

The following code imports an demo application to run control the robot.

```text
[{"id":"68ba1908.11e4c8","type":"tab","label":"Flow 1","disabled":false,"info":""},{"id":"40017c9e.ff4684","type":"http request","z":"68ba1908.11e4c8","name":"","method":"POST","ret":"txt","url":"http://172.17.2.50:5000/direction","tls":"","x":350,"y":60,"wires":[["a4e390e6.0c371","42a86628.cf6298"]]},{"id":"a594ee52.24bbd","type":"ui_form","z":"68ba1908.11e4c8","name":"","label":"","group":"40c14489.1a682c","order":2,"width":0,"height":0,"options":[{"label":"direction","value":"direction","type":"text","required":true},{"label":"time","value":"time","type":"number","required":true}],"formValue":{"direction":"","time":""},"payload":"","submit":"send","cancel":"cancel","topic":"","x":150,"y":60,"wires":[["40017c9e.ff4684","15a3561f.5c0ada"]]},{"id":"a4e390e6.0c371","type":"debug","z":"68ba1908.11e4c8","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","x":650,"y":60,"wires":[]},{"id":"42a86628.cf6298","type":"ui_toast","z":"68ba1908.11e4c8","position":"top right","displayTime":"3","highlight":"","outputs":0,"ok":"OK","cancel":"","topic":"","name":"","x":660,"y":100,"wires":[]},{"id":"211de8fc.3c6cb8","type":"ui_slider","z":"68ba1908.11e4c8","name":"","label":"slider","tooltip":"","group":"40c14489.1a682c","order":1,"width":0,"height":0,"passthru":true,"outs":"all","topic":"","min":0,"max":10,"step":1,"x":150,"y":140,"wires":[["7d6e8599.40d1bc"]]},{"id":"7d6e8599.40d1bc","type":"change","z":"68ba1908.11e4c8","name":"","rules":[{"t":"change","p":"payload","pt":"msg","from":"","fromt":"num","to":"","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":360,"y":140,"wires":[[]]},{"id":"469da4f5.48a90c","type":"ui_button","z":"68ba1908.11e4c8","name":"","group":"d0b6dc80.89e48","order":3,"width":0,"height":0,"passthru":false,"label":"left","tooltip":"","color":"","bgcolor":"","icon":"","payload":"{\"direction\":\"left\",\"time\":0.24}","payloadType":"json","topic":"","x":150,"y":320,"wires":[["40017c9e.ff4684","15a3561f.5c0ada"]]},{"id":"c9c451a6.d0232","type":"ui_button","z":"68ba1908.11e4c8","name":"","group":"d0b6dc80.89e48","order":1,"width":"0","height":"0","passthru":false,"label":"up","tooltip":"","color":"","bgcolor":"","icon":"","payload":"{\"direction\":\"test\", \"time\":0.24, \"speed\":1}","payloadType":"json","topic":"","x":150,"y":240,"wires":[["40017c9e.ff4684","15a3561f.5c0ada"]]},{"id":"9cafea6e.b25848","type":"ui_button","z":"68ba1908.11e4c8","name":"","group":"d0b6dc80.89e48","order":2,"width":0,"height":0,"passthru":false,"label":"down","tooltip":"","color":"","bgcolor":"","icon":"","payload":"{\"direction\":\"down\",\"time\":0.24, \"speed\":1}","payloadType":"json","topic":"","x":150,"y":280,"wires":[["40017c9e.ff4684","15a3561f.5c0ada"]]},{"id":"c74c974.814e168","type":"ui_button","z":"68ba1908.11e4c8","name":"","group":"d0b6dc80.89e48","order":4,"width":0,"height":0,"passthru":false,"label":"right","tooltip":"","color":"","bgcolor":"","icon":"","payload":"{\"direction\":\"right\",\"time\":0.24}","payloadType":"json","topic":"","x":150,"y":360,"wires":[["40017c9e.ff4684","15a3561f.5c0ada"]]},{"id":"15a3561f.5c0ada","type":"ui_text","z":"68ba1908.11e4c8","group":"d0b6dc80.89e48","order":5,"width":0,"height":0,"name":"","label":"data send","format":"{{msg.payload}}","layout":"row-spread","x":440,"y":300,"wires":[]},{"id":"81952644.b52f68","type":"ui_switch","z":"68ba1908.11e4c8","name":"","label":"switch","tooltip":"","group":"d0b6dc80.89e48","order":5,"width":0,"height":0,"passthru":true,"decouple":"false","topic":"","style":"","onvalue":"true","onvalueType":"bool","onicon":"","oncolor":"","offvalue":"false","offvalueType":"bool","officon":"","offcolor":"","x":140,"y":480,"wires":[[]]},{"id":"2306ec5a.fbedc4","type":"keypress","z":"68ba1908.11e4c8","key":"a","x":160,"y":440,"wires":[["ff52c471.a386d8","a43e977d.28dee8"]]},{"id":"ff52c471.a386d8","type":"change","z":"68ba1908.11e4c8","name":"","rules":[{"t":"change","p":"payload","pt":"msg","from":"a","fromt":"str","to":"{\"direction\":\"up\",\"time\":0.24}","tot":"json"}],"action":"","property":"","from":"","to":"","reg":false,"x":420,"y":420,"wires":[["40017c9e.ff4684"]]},{"id":"a43e977d.28dee8","type":"ui_text","z":"68ba1908.11e4c8","group":"d0b6dc80.89e48","order":5,"width":0,"height":0,"name":"","label":"data send","format":"{{msg.payload}}","layout":"row-spread","x":400,"y":520,"wires":[]},{"id":"99f91f64.969b9","type":"ui_button","z":"68ba1908.11e4c8","name":"","group":"40c14489.1a682c","order":3,"width":0,"height":0,"passthru":false,"label":"up","tooltip":"","color":"","bgcolor":"","icon":"","payload":"","payloadType":"str","topic":"","x":160,"y":200,"wires":[[]]},{"id":"40c14489.1a682c","type":"ui_group","z":"","name":"Movement Pytobot","tab":"a58bf3ca.f3e41","order":2,"disp":true,"width":"6","collapse":false},{"id":"d0b6dc80.89e48","type":"ui_group","z":"","name":"Group 2","tab":"a58bf3ca.f3e41","order":1,"disp":true,"width":"6","collapse":false},{"id":"a58bf3ca.f3e41","type":"ui_tab","z":"","name":"Home","icon":"dashboard","disabled":false,"hidden":false}]
```

## Blockly

**Blockly** is a client-side [JavaScript](https://en.wikipedia.org/wiki/JavaScript) library for creating [visual block programming languages](https://en.wikipedia.org/w/index.php?title=Visual_block_programming_languages&action=edit&redlink=1) and editors. It is a project of [Google](https://en.wikipedia.org/wiki/Google) and is [open-source](https://en.wikipedia.org/wiki/Open-source) under the [Apache 2.0 License](https://en.wikipedia.org/wiki/Apache_2.0_License).[\[1\]](https://en.wikipedia.org/wiki/Blockly#cite_note-1) It typically runs in a web browser, and visually resembles [Scratch](https://en.wikipedia.org/wiki/Scratch_%28programming_language%29). Blockly is also being implemented for Android and iOS; not all web browser based features are available for Android/iOS.

Blockly uses visual blocks that link together to make writing code easier, and can generate [JavaScript](https://en.wikipedia.org/wiki/JavaScript), [Python](https://en.wikipedia.org/wiki/Python_%28programming_language%29), [PHP](https://en.wikipedia.org/wiki/PHP) or [Dart](https://en.wikipedia.org/wiki/Dart_%28programming_language%29) code. It can also be customised to generate code in any textual computer language

![](../../.gitbook/assets/blocklydemoimage.png)

## Microsoft MakeCode

Microsoft MakeCode is a free, open source platform for creating engaging computer science learning experiences that support a progression path into real-world programming.

![](../../.gitbook/assets/javascript.gif)

