# How to get NordVPN WireGuard Key
## For this Youtube video: [https://youtu.be/eY4sYGYt0b4](https://youtu.be/eY4sYGYt0b4)
### So you need to have 'curl' and 'jq' utilities installed, then you get NordVPN access token and run:
`curl -s -u token:<ACCESS_TOKEN> https://api.nordvpn.com/v1/users/services/credentials | jq -r .nordlynx_private_key`
### that will give you WireGuard private key, and you can run:
`curl -s "https://api.nordvpn.com/v1/servers/recommendations?&filters\[servers_technologies\]\[identifier\]=wireguard_udp&limit=1" | jq -r '.[]|.hostname, .station, (.locations|.[]|.country|.city.name), (.locations|.[]|.country|.name), (.technologies|.[].metadata|.[].value), .load'`
### to get server info.
 
### Server info for on germany server
`curl --silent "https://api.nordvpn.com/v1/servers?limit=16384"  | jq --raw-output '[.[] | select(.locations[].country.code == "DE") | select(.groups[].identifier="wireguard_udp")][0]' | jq -r '.hostname, .station, (.locations|.[]|.country|.city.name), (.locations|.[]|.country|.name), (.technologies|.[].metadata|.[].value), .load'`

