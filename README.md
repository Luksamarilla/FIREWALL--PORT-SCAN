# FIREWALL--PORT-SCAN
FILTER RULES EVIT PORT-SCAN_MIKROTIK
/ip firewall filter
add action=accept chain=input comment="Aceita estabelecidas e relacionadas" connection-state=established,related
add action=add-src-to-address-list address-list=atacante-ps address-list-timeout=14w2d chain=input comment="Detecta atacanete para TCP" protocol=tcp psd=21,3s,3,1
add action=add-src-to-address-list address-list=atacante-ps address-list-timeout=14w2d chain=input comment="Detecta atacanete para UDP" protocol=udp psd=21,3s,5,1
add action=drop chain=input comment="Dropa atacantes de Port-Scanner" src-address-list=atacante-ps
