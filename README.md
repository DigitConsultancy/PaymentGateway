1. Go to https://test.payumoney.com/ and sign up as a merchant account.

2. Merchant -Key and Salt copy your key and paste in your code

3. PHP code is provided with the repository.

4. Java code is written below.

String hashSequence = "key|txnid|amount|productinfo|firstname|email|udf1|udf2|udf3|udf4|udf5|udf6|udf7|udf8|udf9|udf10";
if (empty(params.get("hash")) &amp;&amp; params.size() &gt; 0) {
if (empty(params.get("key")) || empty(txnid) || empty(params.get("amount")) || empty(params.get("firstname")) || empty(params.get("email")) || empty(params.get("phone")) || empty(params.get("productinfo")) || empty(params.get("surl")) || empty(params.get("furl")) || )) {
error = 1;
} else {
 
String[] hashVarSeq = hashSequence.split("\\|");
for (String part : hashVarSeq) {
if (part.equals("txnid")) {
hashString = hashString + txnid;
urlParams.put("txnid", txnid);
} else {
hashString = (empty(params.get(part))) ? hashString.concat("") : hashString.concat(params.get(part).trim());
urlParams.put(part, empty(params.get(part)) ? "" : params.get(part).trim());
}
hashString = hashString.concat("|");
}
hashString = hashString.concat(salt);
hash = hashCal("SHA-512", hashString);
action1 = base_url.concat("/_payment");
String[] otherPostParamVarSeq = otherPostParamSeq.split("\\|");
for (String part : otherPostParamVarSeq) {
urlParams.put(part, empty(params.get(part)) ? "" : params.get(part).trim());
}
 
}
} else if (!empty(params.get("hash"))) {
hash = params.get("hash");
action1 = base_url.concat("/_payment");
}
 
urlParams.put("hash", hash);
urlParams.put("action", action1);
urlParams.put("hashString", hashString);
return urlParams;
