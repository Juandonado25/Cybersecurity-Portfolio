Al finalizar de instalar Wazuh en docker y comprobar que recibe y colecta correctamente los logs que por el momento solo provee el firewall pfsense me di cuenta que necesito poder hacer los decoders para normalizar y parsear correctamente la información que me proveen esos logs, ademas de hacer las reglas para que Wazuh me pueda alertar correctamente si algún evento sospechoso ha sido detectado.

Para probar los decoders y las reglas hay un binario en /var/ossec/bin/wauh-logtest, se introduce el log, matchea con el decoder o rule y ves si funciona comparando el resultado. Cuando se agregue una nueva regla o decoder se debe reiniciar el manager.



