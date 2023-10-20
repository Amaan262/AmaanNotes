# 1. create powershell profile

=> New-item $profile -Type file -Force

# 2. open Add funciton to Powershell

<code>
notepad $profile 
</code>

# 3. add these in profile file

echo "welcome note..."

function Personal{
Start-Process ssh username@ipaddress
}
function Client1{
Start-Process ssh username2@ipaddress2
}

# 4. Now you can login by typing

Personal
or
client1
