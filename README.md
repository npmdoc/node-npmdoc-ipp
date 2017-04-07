# api documentation for  [ipp (v1.1.0)](http://github.com/williamkapke/ipp)  [![npm package](https://img.shields.io/npm/v/npmdoc-ipp.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-ipp) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-ipp.svg)](https://travis-ci.org/npmdoc/node-npmdoc-ipp)
#### Internet Printing Protocol (IPP) for nodejs

[![NPM](https://nodei.co/npm/ipp.png?downloads=true)](https://www.npmjs.com/package/ipp)

[![apidoc](https://npmdoc.github.io/node-npmdoc-ipp/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-ipp_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-ipp/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-ipp/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-ipp/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "William Kapke",
        "email": "william.kapke@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/williamkapke/ipp/issues"
    },
    "dependencies": {},
    "description": "Internet Printing Protocol (IPP) for nodejs",
    "devDependencies": {
        "mdns2": "*",
        "pdfkit": "*"
    },
    "directories": {},
    "dist": {
        "shasum": "153e1e3ebb12913799298c718dd9f30acc529baa",
        "tarball": "https://registry.npmjs.org/ipp/-/ipp-1.1.0.tgz"
    },
    "engines": {
        "node": "*"
    },
    "gitHead": "8ce50cc37c372be544a2f8df22b3dd82a6f5cb1f",
    "homepage": "http://github.com/williamkapke/ipp",
    "keywords": [
        "ipp",
        "print",
        "printing"
    ],
    "licenses": [
        {
            "type": "MIT",
            "url": "http://www.opensource.org/licenses/MIT"
        }
    ],
    "main": "ipp.js",
    "maintainers": [
        {
            "name": "williamkapke",
            "email": "william.kapke@gmail.com"
        }
    ],
    "name": "ipp",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/williamkapke/ipp.git"
    },
    "scripts": {},
    "version": "1.1.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module ipp](#apidoc.module.ipp)
1.  [function <span class="apidocSignatureSpan">ipp.</span>Printer (url, opts)](#apidoc.element.ipp.Printer)
1.  [function <span class="apidocSignatureSpan">ipp.</span>parse (buf)](#apidoc.element.ipp.parse)
1.  [function <span class="apidocSignatureSpan">ipp.</span>request (opts, buffer, cb)](#apidoc.element.ipp.request)
1.  [function <span class="apidocSignatureSpan">ipp.</span>serialize (msg)](#apidoc.element.ipp.serialize)
1.  object <span class="apidocSignatureSpan">ipp.</span>Printer.prototype
1.  object <span class="apidocSignatureSpan">ipp.</span>attribute
1.  object <span class="apidocSignatureSpan">ipp.</span>attributes
1.  object <span class="apidocSignatureSpan">ipp.</span>enums
1.  object <span class="apidocSignatureSpan">ipp.</span>ipputil
1.  object <span class="apidocSignatureSpan">ipp.</span>keywords
1.  object <span class="apidocSignatureSpan">ipp.</span>operations
1.  object <span class="apidocSignatureSpan">ipp.</span>statusCodes
1.  object <span class="apidocSignatureSpan">ipp.</span>tags
1.  object <span class="apidocSignatureSpan">ipp.</span>versions

#### [module ipp.Printer](#apidoc.module.ipp.Printer)
1.  [function <span class="apidocSignatureSpan">ipp.</span>Printer (url, opts)](#apidoc.element.ipp.Printer.Printer)

#### [module ipp.Printer.prototype](#apidoc.module.ipp.Printer.prototype)
1.  [function <span class="apidocSignatureSpan">ipp.Printer.prototype.</span>_message (operation, msg)](#apidoc.element.ipp.Printer.prototype._message)
1.  [function <span class="apidocSignatureSpan">ipp.Printer.prototype.</span>execute (operation, msg, cb)](#apidoc.element.ipp.Printer.prototype.execute)

#### [module ipp.ipputil](#apidoc.module.ipp.ipputil)
1.  [function <span class="apidocSignatureSpan">ipp.ipputil.</span>extend (destination, source)](#apidoc.element.ipp.ipputil.extend)
1.  [function <span class="apidocSignatureSpan">ipp.ipputil.</span>xref (arr)](#apidoc.element.ipp.ipputil.xref)

#### [module ipp.parse](#apidoc.module.ipp.parse)
1.  [function <span class="apidocSignatureSpan">ipp.</span>parse (buf)](#apidoc.element.ipp.parse.parse)
1.  [function <span class="apidocSignatureSpan">ipp.parse.</span>handleUnknownTag (tag, name, length, read)](#apidoc.element.ipp.parse.handleUnknownTag)



# <a name="apidoc.module.ipp"></a>[module ipp](#apidoc.module.ipp)

#### <a name="apidoc.element.ipp.Printer"></a>[function <span class="apidocSignatureSpan">ipp.</span>Printer (url, opts)](#apidoc.element.ipp.Printer)
- description and source-code
```javascript
function Printer(url, opts){
	if(!(this instanceof Printer)) return new Printer(url, opts);
	opts = opts || {};
	this.url = typeof url==="string"? parseurl(url) : url;
	this.version = opts.version || '2.0';
	this.uri = opts.uri || 'ipp://' + this.url.host + this.url.path;
	this.charset = opts.charset || 'utf-8';
	this.language = opts.language || 'en-us';
}
```
- example usage
```shell
...
var PDFDocument = require('pdfkit');

//make a PDF document
var doc = new PDFDocument({margin:0});
doc.text(".", 0, 780);

doc.output(function(pdf){
	var printer = ipp.Printer("http://NPI977E4E.local.:631/ipp/printer");
	var msg = {
		"operation-attributes-tag": {
			"requesting-user-name": "William",
			"job-name": "My Test Job",
			"document-format": "application/pdf"
		},
		data: pdf
...
```

#### <a name="apidoc.element.ipp.parse"></a>[function <span class="apidocSignatureSpan">ipp.</span>parse (buf)](#apidoc.element.ipp.parse)
- description and source-code
```javascript
parse = function (buf) {
	var obj = {};
	var position = 0;
	var encoding = 'utf8';
	function read1(){
		return buf[position++];
	}
	function read2(){
		var val = buf.readInt16BE(position, true);
		position+=2;
		return val;
	}
	function read4(){
		var val = buf.readInt32BE(position, true);
		position+=4;
		return val;
	}
	function read(length, enc){
		if(length==0) return '';
		return buf.toString(enc||encoding, position, position+=length);
	}
	function readGroups(){
		var group;
		while(position < buf.length && (group = read1()) !== 0x03){//end-of-attributes-tag
			readGroup(group);
		}
	}
	function readGroup(group){
		var name = tags.lookup[group];
		group={};
		if(obj[name]){
			if(!Array.isArray(obj[name]))
				obj[name] = [obj[name]];
			obj[name].push(group);
		}
		else obj[name] = group;

		while(buf[position] >= 0x0F) {// delimiters are between 0x00 to 0x0F
			readAttr(group);
		}
	}
	function readAttr(group){
		var tag = read1();
		//TODO: find a test for this
		if (tag === 0x7F){//tags.extension
			tag = read4();
		}
		var name = read(read2());
		group[name] = readValues(tag, name)
	}
	function hasAdditionalValue(){
		var current = buf[position];
		return current !== 0x4A //tags.memberAttrName
			&& current !== 0x37 //tags.endCollection
			&& current !== 0x03 //tags.end-of-attributes-tag
			&& buf[position+1] === 0x00 && buf[position+2] === 0x00;
	}
	function readValues(type, name){
		var value = readValue(type, name);
		if(hasAdditionalValue()){
			value = [value];
			do{
				type = read1();
				read2();//empty name
				value.push(readValue(type, name));
			}
			while(hasAdditionalValue())
		}
		return value;
	}
	function readValue(tag, name){
		var length = read2();
		//http://tools.ietf.org/html/rfc2910#section-3.9
		switch (tag) {
			case tags.enum:
				var val = read4();
				return (enums[name] && enums[name].lookup[val]) || val;
			case tags.integer:
				return read4();

			case tags.boolean:
				return !!read1();

			case tags.rangeOfInteger:
				return [read4(), read4()];

			case tags.resolution:
				return [read4(), read4(), read1()===0x03? 'dpi':'dpcm'];

			case tags.dateTime:
				// http://tools.ietf.org/html/rfc1903 page 17
				var date = new Date(read2(), read1(), read1(), read1(), read1(), read1(), read1());
				//silly way to add on the timezone
				return new Date(date.toISOString().substr(0,23).replace('T',',') +','+ String.fromCharCode(read(1)) + read(1) + ':' + read(1
));

			case tags.textWithLanguage:
			case tags.nameWithLanguage:
				var lang = read(read2());
				var subval = read(read2());
				return lang+RS+subval;

			case tags.nameWithoutLanguage:
			case tags.textWithoutLanguage:
			case tags.octetString:
			case tags.memberAttrName:
				return read(length);

			case tags.keyword:
			case tags.uri:
			case tags.uriScheme:
			case tags.charset:
			case tags.naturalLanguage:
			case tags.mimeMediaType:
				return read(length, 'ascii');

			case tags.begCollection:
				//the spec says a value could be present- but can be ignored
				read(length);
				return readCollection();

			case tags['no-value']:
			default:
				debugger;
				return module.exports.handleUnknownTag(tag, name, length, read)
		}
	}
	function readCollection(){
		var tag;
		var collection = {};

		while((tag = read1()) !== 0x37){//tags.endCollection
			if(tag !== 0x4A){
				console.log("unexpected:", tags.lookup[tag]);
				return;
			}
			//read nametag name and discard it
			read(read2());
			var name = readValue(0x4A);
			var values = readCollectionItemValue();
			collection[name] = values;
		}
		//Read endCollection name & value and discard it.
		//The spec says that they MAY have contents in the
		// future- so we can't assume they are empty.
		read(read2());
		read(read2());

		return collection;
	}
	function readCollectionItemValue(name){
		var tag = read1();
		//TODO: find a test for this
		if (tag === 0x7F){//tags.extension
			tag = read4();
		}
		//read valuetag name and discard it
		read(read2());

		return readValues(tag, name);
	}

	obj.version = read1() + '.' + read1();
	var bytes2and3 = read2();
	//byte[2] and b ...
```
- example usage
```shell
...
### printer.execute(operation, message, callback)
Executes an IPP operation on the Printer object.

* 'operation' - There are many operations defined by IPP. See: [/lib/enums.js](https://github.com/williamkapke/ipp/blob/master/lib
/enums.js#L52).
* 'message - A javascript object to be serealized into an IPP binary message.
* 'callback(err, response)' - A function to callback with the Printer's response.

## ipp.parse(buffer)

Parses a binary IPP message into a javascript object tree.

'''javascript
var ipp = require('ipp');
var data = new Buffer(
'0200' +	//version 2.0
...
```

#### <a name="apidoc.element.ipp.request"></a>[function <span class="apidocSignatureSpan">ipp.</span>request (opts, buffer, cb)](#apidoc.element.ipp.request)
- description and source-code
```javascript
request = function (opts, buffer, cb){
	var streamed = typeof buffer === "function";
	//All IPP requires are POSTs- so we must have some data.
	//  10 is just a number I picked- this probably should have something more meaningful
	if(!Buffer.isBuffer(buffer) || buffer.length<10){
		return cb(new Error("Data required"));
	}
	if(typeof opts === "string")
		opts = url.parse(opts);
	if(!opts.port) opts.port = 631;

	if(!opts.headers) opts.headers = {};
	opts.headers['Content-Type'] = 'application/ipp';
	opts.method = "POST";
	
	if(opts.protocol==="ipp:")
		opts.protocol="http:";

	if(opts.protocol==="ipps:")
		opts.protocol="https:";

	var req = (opts.protocol==="https:" ? https : http).request(opts, function(res){
//		console.log('STATUS: ' + res.statusCode);
//		console.log('HEADERS: ' + JSON.stringify(res.headers));
		switch(res.statusCode){
			case 100:
				if(opts.headers['Expect'] !== '100-Continue' || typeof opts.continue !== "function"){
					cb(new IppResponseError(res.statusCode));
				}
				return console.log("100 Continue");
			case 200:
				return readResponse(res, cb);
			default:
				cb(new IppResponseError(res.statusCode));
				return console.log(res.statusCode, "response");
		}
	});
	req.on('error', function(err) {
		cb(err);
	});
	if(opts.headers['Expect'] === '100-Continue' && typeof opts.continue=== "function"){
		req.on('continue', function() {
			opts.continue(req);
		});
	}
	req.write(buffer);
	req.end();
}
```
- example usage
```shell
...

## ipp.serialize(msg)
Converts an IPP message object to IPP binary.

See [request](#request) for example.

<a id="request"></a>
## ipp.request(url, data, callback)

Makes an IPP request to a url.

'''javascript
var ipp = require('ipp');
var uri = "your_printer";
var data = ipp.serialize({
...
```

#### <a name="apidoc.element.ipp.serialize"></a>[function <span class="apidocSignatureSpan">ipp.</span>serialize (msg)](#apidoc.element.ipp.serialize)
- description and source-code
```javascript
function serializer(msg){
	var buf = new Buffer(10240);
	var position = 0;
	function write1(val){
		buf.writeUInt8(val, position);
		position+=1;
	}
	function write2(val){
		buf.writeUInt16BE(val, position);
		position+=2;
	}
	function write4(val){
		buf.writeUInt32BE(val, position);
		position+=4;
	}
	function write(str, enc){
		var length = Buffer.byteLength(str);
		write2(length);
		buf.write(str, position, length, enc || "utf8");
		position+=length;
	}
	var special = {'attributes-charset':1, 'attributes-natural-language':2};
	var groupmap = {
		"job-attributes-tag":	               ['Job Template', 'Job Description'],
		'operation-attributes-tag':          'Operation',
		'printer-attributes-tag':            'Printer Description',
		"unsupported-attributes-tag":        '',//??
		"subscription-attributes-tag":       'Subscription Description',
		"event-notification-attributes-tag": 'Event Notifications',
		"resource-attributes-tag":           '',//??
		"document-attributes-tag":           'Document Description'
	};
	function writeGroup(tag){
		var attrs = msg[tag];
		if(!attrs) return;
		var keys = Object.keys(attrs);
		//'attributes-charset' and 'attributes-natural-language' need to come first- so we sort them to the front
		if(tag==tags['operation-attributes-tag'])
			keys = keys.sort(function(a,b){ return (special[a]||3)-(special[b]||3); });
		var groupname = groupmap[tag];
		write1(tags[tag]);
		keys.forEach(function(name){
			attr(groupname, name, attrs);
		});
	}
	function attr(group, name, obj){
		var groupName = Array.isArray(group)
			? group.find((grp) => { return attributes[grp][name] })
			: group;
		if(!groupName) throw "Unknown attribute: " + name;

		var syntax = attributes[groupName][name];
		if(!syntax) throw "Unknown attribute: " + name;

		var value = obj[name];
		if(!Array.isArray(value))
			value = [value];

		value.forEach(function(value, i){
			//we need to re-evaluate the alternates every time
			var syntax2 = Array.isArray(syntax)? resolveAlternates(syntax, name, value) : syntax;
			var tag = getTag(syntax2, name, value);
			if(tag===tags.enum)
				value = enums[name][value];

			write1(tag);
			if(i==0){
				write(name);
			}
			else {
				write2(0x0000);//empty name
			}

			writeValue(tag, value, syntax2.members);
		});
	}
	function getTag(syntax, name, value){
		var tag = syntax.tag;
		if(!tag){
			var hasRS = !!~value.indexOf(RS);
			tag = tags[syntax.type+(hasRS?'With':'Without')+'Language'];
		}
		return tag;
	}
	function resolveAlternates(array, name, value){
		switch(array.alts){
			case 'keyword,name':
			case 'keyword,name,novalue':
				if(value===null && array.lookup['novalue']) return array.lookup['novalue'];
				return ~keywords[name].indexOf(value)? array.lookup.keyword : array.lookup.name;
			case 'integer,rangeOfInteger':
				return Array.isArray(value)? array.lookup.rangeOfInteger : array.lookup.integer;
			case 'dateTime,novalue':
				return !IsNaN(date.parse(value))? array.lookup.dateTime : array.lookup['novalue'];
			case 'integer,novalue':
				return !IsNaN(value)? array.lookup.integer : array.lookup['novalue'];
			case 'name,novalue':
				return value!==null? array.lookup.name : array.lookup['novalue'];
			case 'novalue,uri':
				return value!==null? array.lookup.uri : array.lookup['novalue'];
			case 'enumeration,unknown':
				return enums[name][value]? array.lookup['enumeration'] : array.lookup.unknown;
			case 'enumeration,novalue':
				return value!==null? array.lookup['enumeration'] : array.lookup['novalue'];
			case 'collection,novalue':
				return value!==null? array.lookup['enumeration'] : array.lookup['novalue'];
			default:
				throw "Unknown atlernates";
		}
	}
	function writeValue(tag, value, submembers){
		switch(tag){
			case tags.enum:
				write2(0x0004);
				return write4(value);
			case tags.integer:
				write2(0x0004);
				return write4(value);

			case tags.boolean:
				write2(0x0001);
				return write1(Number(value));

			case tags.rangeOfInteger:
				write2(0x0008);
				write4(value[0]);
				write4(value[1]);
				return;

			case tags.resolution:
				w ...
```
- example usage
```shell
...
//	"operation-attributes-tag": {
//		"attributes-charset": "utf-8",
//		"attributes-natural-language": "en"
//	}
//}
'''

## ipp.serialize(msg)
Converts an IPP message object to IPP binary.

See [request](#request) for example.

<a id="request"></a>
## ipp.request(url, data, callback)
...
```



# <a name="apidoc.module.ipp.Printer"></a>[module ipp.Printer](#apidoc.module.ipp.Printer)

#### <a name="apidoc.element.ipp.Printer.Printer"></a>[function <span class="apidocSignatureSpan">ipp.</span>Printer (url, opts)](#apidoc.element.ipp.Printer.Printer)
- description and source-code
```javascript
function Printer(url, opts){
	if(!(this instanceof Printer)) return new Printer(url, opts);
	opts = opts || {};
	this.url = typeof url==="string"? parseurl(url) : url;
	this.version = opts.version || '2.0';
	this.uri = opts.uri || 'ipp://' + this.url.host + this.url.path;
	this.charset = opts.charset || 'utf-8';
	this.language = opts.language || 'en-us';
}
```
- example usage
```shell
...
var PDFDocument = require('pdfkit');

//make a PDF document
var doc = new PDFDocument({margin:0});
doc.text(".", 0, 780);

doc.output(function(pdf){
	var printer = ipp.Printer("http://NPI977E4E.local.:631/ipp/printer");
	var msg = {
		"operation-attributes-tag": {
			"requesting-user-name": "William",
			"job-name": "My Test Job",
			"document-format": "application/pdf"
		},
		data: pdf
...
```



# <a name="apidoc.module.ipp.Printer.prototype"></a>[module ipp.Printer.prototype](#apidoc.module.ipp.Printer.prototype)

#### <a name="apidoc.element.ipp.Printer.prototype._message"></a>[function <span class="apidocSignatureSpan">ipp.Printer.prototype.</span>_message (operation, msg)](#apidoc.element.ipp.Printer.prototype._message)
- description and source-code
```javascript
_message = function (operation, msg){
		if(typeof operation === "undefined") operation = 'Get-Printer-Attributes';

		var base = {
			version: this.version,
			operation: operation,
			id: null,//will get added by serializer if one isn't given
			'operation-attributes-tag': {
				//these are required to be in this order
				'attributes-charset': this.charset,
				'attributes-natural-language': this.language,
				'printer-uri': this.uri
			}
		};
		//these are required to be in this order
		if(msg && msg['operation-attributes-tag']['job-id'])
			base['operation-attributes-tag']['job-id'] = msg['operation-attributes-tag']['job-id'];
		//yes, this gets done in extend()- however, by doing this now, we define the position in the result object.
		else if(msg && msg['operation-attributes-tag']['job-uri'])
			base['operation-attributes-tag']['job-uri'] = msg['operation-attributes-tag']['job-uri'];

		msg = extend(base, msg);
		if(msg['operation-attributes-tag']['job-uri'])
			delete msg['operation-attributes-tag']['printer-uri'];
		return msg;
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.ipp.Printer.prototype.execute"></a>[function <span class="apidocSignatureSpan">ipp.Printer.prototype.</span>execute (operation, msg, cb)](#apidoc.element.ipp.Printer.prototype.execute)
- description and source-code
```javascript
execute = function (operation, msg, cb){
		msg = this._message(operation, msg);
		var buf = serialize(msg);
//		console.log(buf.toString('hex'));
//		console.log(JSON.stringify(
//			require('./parser')(buf), null, 2
//		));
		request(this.url, buf, cb);
	}
```
- example usage
```shell
...
		"operation-attributes-tag": {
			"requesting-user-name": "William",
			"job-name": "My Test Job",
			"document-format": "application/pdf"
		},
		data: pdf
	};
	printer.execute("Print-Job", msg, function(err, res){
		console.log(res);
	});
});
'''

To interact with a printer, create a 'Printer' object.
...
```



# <a name="apidoc.module.ipp.ipputil"></a>[module ipp.ipputil](#apidoc.module.ipp.ipputil)

#### <a name="apidoc.element.ipp.ipputil.extend"></a>[function <span class="apidocSignatureSpan">ipp.ipputil.</span>extend (destination, source)](#apidoc.element.ipp.ipputil.extend)
- description and source-code
```javascript
function extend(destination, source) {
	for(var property in source) {
		if (source[property] && source[property].constructor === Object) {
			destination[property] = destination[property] || {};
			extend(destination[property], source[property]);
		}
		else {
			destination[property] = source[property];
		}
	}
	return destination;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.ipp.ipputil.xref"></a>[function <span class="apidocSignatureSpan">ipp.ipputil.</span>xref (arr)](#apidoc.element.ipp.ipputil.xref)
- description and source-code
```javascript
function xref(arr){
	var obj = {};
	arr.forEach(function(item, index){
		obj[item] = index;
	});
	obj.lookup = arr;
	return obj;
}
```
- example usage
```shell
...
	enums: require('./lib/enums'),
	tags: require('./lib/tags'),
	statusCodes: require('./lib/status-codes')
};
module.exports.operations = module.exports.enums['operations-supported'];
module.exports.attribute = {
	//http://www.iana.org/assignments/ipp-registrations/ipp-registrations.xml#ipp-registrations-7
	groups: util.xref(module.exports.tags.lookup.slice(0x00, 0x0F)),
	//http://www.iana.org/assignments/ipp-registrations/ipp-registrations.xml#ipp-registrations-8
	values: util.xref(module.exports.tags.lookup.slice(0x10, 0x1F)),
	//http://www.iana.org/assignments/ipp-registrations/ipp-registrations.xml#ipp-registrations-9
	syntaxes: util.xref(module.exports.tags.lookup.slice(0x20))
}
...
```



# <a name="apidoc.module.ipp.parse"></a>[module ipp.parse](#apidoc.module.ipp.parse)

#### <a name="apidoc.element.ipp.parse.parse"></a>[function <span class="apidocSignatureSpan">ipp.</span>parse (buf)](#apidoc.element.ipp.parse.parse)
- description and source-code
```javascript
parse = function (buf) {
	var obj = {};
	var position = 0;
	var encoding = 'utf8';
	function read1(){
		return buf[position++];
	}
	function read2(){
		var val = buf.readInt16BE(position, true);
		position+=2;
		return val;
	}
	function read4(){
		var val = buf.readInt32BE(position, true);
		position+=4;
		return val;
	}
	function read(length, enc){
		if(length==0) return '';
		return buf.toString(enc||encoding, position, position+=length);
	}
	function readGroups(){
		var group;
		while(position < buf.length && (group = read1()) !== 0x03){//end-of-attributes-tag
			readGroup(group);
		}
	}
	function readGroup(group){
		var name = tags.lookup[group];
		group={};
		if(obj[name]){
			if(!Array.isArray(obj[name]))
				obj[name] = [obj[name]];
			obj[name].push(group);
		}
		else obj[name] = group;

		while(buf[position] >= 0x0F) {// delimiters are between 0x00 to 0x0F
			readAttr(group);
		}
	}
	function readAttr(group){
		var tag = read1();
		//TODO: find a test for this
		if (tag === 0x7F){//tags.extension
			tag = read4();
		}
		var name = read(read2());
		group[name] = readValues(tag, name)
	}
	function hasAdditionalValue(){
		var current = buf[position];
		return current !== 0x4A //tags.memberAttrName
			&& current !== 0x37 //tags.endCollection
			&& current !== 0x03 //tags.end-of-attributes-tag
			&& buf[position+1] === 0x00 && buf[position+2] === 0x00;
	}
	function readValues(type, name){
		var value = readValue(type, name);
		if(hasAdditionalValue()){
			value = [value];
			do{
				type = read1();
				read2();//empty name
				value.push(readValue(type, name));
			}
			while(hasAdditionalValue())
		}
		return value;
	}
	function readValue(tag, name){
		var length = read2();
		//http://tools.ietf.org/html/rfc2910#section-3.9
		switch (tag) {
			case tags.enum:
				var val = read4();
				return (enums[name] && enums[name].lookup[val]) || val;
			case tags.integer:
				return read4();

			case tags.boolean:
				return !!read1();

			case tags.rangeOfInteger:
				return [read4(), read4()];

			case tags.resolution:
				return [read4(), read4(), read1()===0x03? 'dpi':'dpcm'];

			case tags.dateTime:
				// http://tools.ietf.org/html/rfc1903 page 17
				var date = new Date(read2(), read1(), read1(), read1(), read1(), read1(), read1());
				//silly way to add on the timezone
				return new Date(date.toISOString().substr(0,23).replace('T',',') +','+ String.fromCharCode(read(1)) + read(1) + ':' + read(1
));

			case tags.textWithLanguage:
			case tags.nameWithLanguage:
				var lang = read(read2());
				var subval = read(read2());
				return lang+RS+subval;

			case tags.nameWithoutLanguage:
			case tags.textWithoutLanguage:
			case tags.octetString:
			case tags.memberAttrName:
				return read(length);

			case tags.keyword:
			case tags.uri:
			case tags.uriScheme:
			case tags.charset:
			case tags.naturalLanguage:
			case tags.mimeMediaType:
				return read(length, 'ascii');

			case tags.begCollection:
				//the spec says a value could be present- but can be ignored
				read(length);
				return readCollection();

			case tags['no-value']:
			default:
				debugger;
				return module.exports.handleUnknownTag(tag, name, length, read)
		}
	}
	function readCollection(){
		var tag;
		var collection = {};

		while((tag = read1()) !== 0x37){//tags.endCollection
			if(tag !== 0x4A){
				console.log("unexpected:", tags.lookup[tag]);
				return;
			}
			//read nametag name and discard it
			read(read2());
			var name = readValue(0x4A);
			var values = readCollectionItemValue();
			collection[name] = values;
		}
		//Read endCollection name & value and discard it.
		//The spec says that they MAY have contents in the
		// future- so we can't assume they are empty.
		read(read2());
		read(read2());

		return collection;
	}
	function readCollectionItemValue(name){
		var tag = read1();
		//TODO: find a test for this
		if (tag === 0x7F){//tags.extension
			tag = read4();
		}
		//read valuetag name and discard it
		read(read2());

		return readValues(tag, name);
	}

	obj.version = read1() + '.' + read1();
	var bytes2and3 = read2();
	//byte[2] and b ...
```
- example usage
```shell
...
### printer.execute(operation, message, callback)
Executes an IPP operation on the Printer object.

* 'operation' - There are many operations defined by IPP. See: [/lib/enums.js](https://github.com/williamkapke/ipp/blob/master/lib
/enums.js#L52).
* 'message - A javascript object to be serealized into an IPP binary message.
* 'callback(err, response)' - A function to callback with the Printer's response.

## ipp.parse(buffer)

Parses a binary IPP message into a javascript object tree.

'''javascript
var ipp = require('ipp');
var data = new Buffer(
'0200' +	//version 2.0
...
```

#### <a name="apidoc.element.ipp.parse.handleUnknownTag"></a>[function <span class="apidocSignatureSpan">ipp.parse.</span>handleUnknownTag (tag, name, length, read)](#apidoc.element.ipp.parse.handleUnknownTag)
- description and source-code
```javascript
function log(tag, name, length, read) {
	var value = length? read(length) : undefined;
	console.log("The spec is not clear on how to handle tag " +tag+ ": " +name+ "=" +String(value)+ ". " +
		"Please open a github issue to help find a solution!");
	return value;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
