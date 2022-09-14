# SII_SSL
Conexión al SII con SSL Versión 1.2

A partir del 20 de septiembre 20222 el sii cambiará la autenticación SSL 1.0 a la versión 1.2.
<br>Las Integraciones con Php 5.5 o superior ya vienen por default con la versión 1.2
<br>Por defecto php utiliza la mayor versión disponible.
<br>Para forzar a php que utilize una versión específica se deben agregar una línea de código.

<br><b>curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_3); // TLS 1.3 </b>
<br>
<br>// 1.0 y 1.1 no son validos en boleta electronica
<br>//curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_0); // TLS 1.0
<br>//curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_1); // TLS 1.1
<br>//
<br>// 1.2 y 1.3 validos en el sii a partir de 20 septiembre 2022
<br>//curl_setopt($handler, CURLOPT_SSLVERSION, 6); 
<br>//curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_2); // TLS 1.2 
<br>curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_3); // TLS 1.3 

<br>
<br>Para consultar la versión de php puede utilizar el siguiente comando
<br>phpinfo();
<br>
<br>Para consultar la versión de php curl puede utilizar el siguiente comando:
<br>var_dump(curl_version());
<br>

<h3>Ejemplo para ver la versión de php curl:</h3>

```
<?php
$info = curl_getinfo($handler);
print_r(curl_getinfo($handler,CURLINFO_HEADER_OUT)); 
?>
```

<h3>Ejemplo para Forzar la conexión por ssl versión 1.3:</h3>

```
<?php
$handler = curl_init();
curl_setopt($handler, CURLOPT_URL, $this->_url);
curl_setopt($handler, CURLOPT_PORT, 443);
curl_setopt($handler, CURLOPT_VERBOSE, 1);
curl_setopt($handler, CURLOPT_HTTPHEADER, $cabecera);
curl_setopt($handler, CURLOPT_HTTP_VERSION, CURL_HTTP_VERSION_1_0);
curl_setopt($handler, CURLOPT_FOLLOWLOCATION, 1);
curl_setopt($handler, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($handler, CURLOPT_TIMEOUT, 30);
curl_setopt($handler, CURLOPT_SSL_VERIFYHOST, 2);
curl_setopt($handler, CURLOPT_SSL_VERIFYPEER, 0);
// FORZAR LA CONEXION SSL POR VERSION 1.3
curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_3); 
curl_setopt($handler, CURLOPT_POSTFIELDS, $cuerpo);
curl_setopt($handler, CURLOPT_HEADER, 0);
curl_setopt($handler, CURLINFO_HEADER_OUT, $CURLINFO_HEADER_OUT);
curl_setopt($handler, CURLOPT_FILE, $archivito);
$result = curl_exec ($handler);
?>
```

