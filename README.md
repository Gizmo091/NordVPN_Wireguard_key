# How to get NordVPN WireGuard Key </ br>
# For this Youtube video: [https://youtu.be/eY4sYGYt0b4](https://youtu.be/eY4sYGYt0b4)  </ br>
# So you need to have 'curl' and 'jq' utilities installed, then you get NordVPN access token and run: </ br>
`curl -s -u token:<ACCESS_TOKEN> https://api.nordvpn.com/v1/users/services/credentials | jq -r .nordlynx_private_key`
# that will give you WireGuard private key, and you can run: </ br>
`curl -s "https://api.nordvpn.com/v1/servers/recommendations?&filters\[servers_technologies\]\[identifier\]=wireguard_udp&limit=1" | jq -r '.[]|.hostname, .station, (.locations|.[]|.country|.city.name), (.locations|.[]|.country|.name), (.technologies|.[].metadata|.[].value), .load'`
# to get server info.
 
