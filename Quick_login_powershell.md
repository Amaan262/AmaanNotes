# 1. create powershell profile

<code>
 New-item $profile -Type file -Force
</code>
# 2. open Add funciton to Powershell

<code>notepad $profile</code>

# 3. add these in profile file

<code>echo "welcome note..."

function Personal{
Start-Process ssh username@ipaddress
}
function Client1{
Start-Process ssh username2@ipaddress2
}
</code>

# 4. Now you can login by typing

<code>Personal<code>
or
<code>
client1
</code>
