# download-ocultar-ruta
Descargar una imagen y ocultar ruta de acceso directo


. crear una carpeta "caché" y mapear el contenido de tu carpeta evitando referenciar la carpeta original. 
. restringir el acceso a tu carpeta original mediante .htaccess

|-pdf
    |-readme.pdf
.htaccess    
index.php

<?php
$filename = 'pdf/readme.pdf';

if (file_exists($filename)) {
header('Content-Description: File Transfer');
header('Content-Type: application/octet-stream');
header('Content-Disposition: attachment; filename="' . basename($filename) . '"');
header('Expires: 0');
header('Cache-Control: must-revalidate');
header('Pragma: public');
header('Content-Length: ' . filesize($filename));
readfile($filename);
exit;
}
?>
