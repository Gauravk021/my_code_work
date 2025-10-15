# 2a) Find the .p12 or .pfx file in your Downloads\lunadb_DEVL
dir "$env:USERPROFILE\Downloads\lunadb_DEVL\*.p12","$env:USERPROFILE\Downloads\lunadb_DEVL\*.pfx"

# 2b) Copy it into your project certs folder (if the name is different, replace it below)
Copy-Item "$env:USERPROFILE\Downloads\lunadb_DEVL\lunadb.p12" "C:\Workspace1\luna-services\certs\" -Force