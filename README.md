
& "$env:JAVA_HOME\bin\keytool.exe" -importcert -trustcacerts `
 -alias ejdev-ca-root `
 -file "C:\Users\p251889\Downloads\lunadb_DEVL\ca-chain-inclroot.cer" `
 -keystore "C:\Workspace1\luna-services\certs\truststore.jks" `
 -storepass "VxRrE0_304_2mfQf7" -noprompt


& "$env:JAVA_HOME\bin\keytool.exe" -list -v -keystore "C:\Workspace1\luna-services\certs\truststore.jks" -storepass "VxRrE0_304_2mfQf7"