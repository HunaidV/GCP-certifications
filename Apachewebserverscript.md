#! /bin/bash
if [ -f /etc/startup_script_completed ]; then
exit 0
fi
apt-get update
apt-get install apache2 -y
a2ensite default-ssl
a2enmod ssl
file_ports="/etc/apache2/ports.conf"
file_http_site="/etc/apache2/sites-available/000-default.conf"
file_https_site="/etc/apache2/sites-available/default-ssl.conf"
http_listen_prts="Listen 80\nListen 8008\nListen 8080\nListen 8088"
http_vh_prts="*:80 *:8008 *:8080 *:8088"
https_listen_prts="Listen 443\nListen 8443"
https_vh_prts="*:443 *:8443"
vm_hostname="$(curl -H "Metadata-Flavor:Google" \
http://169.254.169.254/computeMetadata/v1/instance/name)"
echo "Page served from: $vm_hostname" | \
tee /var/www/html/index.html
echo "Page served from: $vm_hostname" | \
tee /var/www/html/index.html
prt_conf="$(cat "$file_ports")"
prt_conf_2="$(echo "$prt_conf" | sed "s|Listen 80|${http_listen_prts}|")"
prt_conf="$(echo "$prt_conf_2" | sed "s|Listen 443|${https_listen_prts}|")"
echo "$prt_conf" | tee "$file_ports"
http_site_conf="$(cat "$file_http_site")"
http_site_conf_2="$(echo "$http_site_conf" | sed "s|*:80|${http_vh_prts}|")"
echo "$http_site_conf_2" | tee "$file_http_site"
https_site_conf="$(cat "$file_https_site")"
https_site_conf_2="$(echo "$https_site_conf" | sed "s|_default_:443|${https_vh_prts}|")"
echo "$https_site_conf_2" | tee "$file_https_site"
systemctl restart apache2
touch /etc/startup_script_completed