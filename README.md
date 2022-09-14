# SII_SSL
Conexión al SII con SSL Versión 1.2

A partir del 20 de septiembre 20222 el sii cambiará la autenticación SSL 1.0 a la versión 1.2.
Las Integraciones con Php 5.5 o superior ya vienen por default con la versión 1.2
Por defecto php utiliza la mayor versión disponible.
Para forzar a php que utilize una versión específica se deben agregar una línea de código.

´´´
curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_3); // TLS 1.3 
´´´

// 1.0 y 1.1 no son validos en boleta electronica
//curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_0); // TLS 1.0
//curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_1); // TLS 1.1
//
// 1.2 y 1.3 validos en el sii a partir de 20 septiembre 2022
//curl_setopt($handler, CURLOPT_SSLVERSION, 6); 
//curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_2); // TLS 1.2 
curl_setopt($handler, CURLOPT_SSLVERSION, CURL_SSLVERSION_TLSv1_3); // TLS 1.3 
