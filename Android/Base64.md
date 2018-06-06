[Apache](http://commons.apache.org/proper/commons-codec/download_codec.cgi) 사이트에서 받을 수 있음

```java
import java.net.URLDecoder;
import org.apache.commons.codec.binary.Base64;
import org.apache.commons.codec.binary.BinaryCodec;
import org.apache.commons.codec.binary.Hex;
import org.apache.commons.codec.digest.DigestUtils;
import org.apache.commons.codec.net.BCodec;
import org.apache.commons.codec.net.QCodec;
import org.apache.commons.codec.net.URLCodec;

public void testApache() {
	String encMsg = null;
	String decMsg = null;
	String msg = "테스트 테스트 테스트";
	
    try {
        // Base64 encode/decode
        encMsg = new String(Base64.encodeBase64(msg.getBytes()));
        decMsg = new String(Base64.decodeBase64(encMsg.getBytes()));
        Log.d("Base64 Encode", encMsg);
        Log.d("Base64 Decode", decMsg);

        // URL encode/decode
        URLCodec urlCodec = new URLCodec();
        encMsg = urlCodec.encode(msg);
        decMsg = urlCodec.decode(encMsg);
        Log.d("URL Encode", encMsg);
        Log.d("URL Decode", decMsg);
        Log.d("URLDecoder.decode", URLDecoder.decode(encMsg, "utf-8"));

        // MD5/SHA
        String md5HexText = DigestUtils.md5Hex(msg);
        String shaHexText = DigestUtils.shaHex(msg);
        Log.d("MD5", md5HexText);
        Log.d("SHA", shaHexText);
        
        // Hex
        encMsg = new String(Hex.encodeHex(msg.getBytes()));
        decMsg = new String(Hex.decodeHex(encMsg.toCharArray()));
        Log.d("Hex Encode", encMsg);
        Log.d("Hex Decode", decMsg);
    } catch (Throwable e) {
        e.printStackTrace();
    }
}

```