& "$env:JAVA_HOME\bin\keytool.exe" -importcert -trustcacerts `
-alias ejdev-ca-root `
-file "C:\Workspace1\luna-services\certs\ca-chain-inclroot.crt" `
-keystore "C:\Workspace1\luna-services\certs\truststore.jks" `
-storepass "VxRrE0_304_2mfQf7" -noprompt



& "$env:JAVA_HOME\bin\keytool.exe" -list -v -keystore "C:\Workspace1\luna-services\certs\truststore.jks"


