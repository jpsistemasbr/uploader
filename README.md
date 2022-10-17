# Uploader @JPsistemasBR



###### Uploader is a set of small classes for sending images, files, and media received by a form of your application. The Uploader handles, validates and sends the files to your server. Image class can still handle sizes with the gd library.

Uploader é um conjunto de pequenas classes para envio de imagens, arquivos e midias recebidos por um formulário de sua
aplicação. O Uploader trata, valida e envia os arquivos a seu servidor. A classe de imagem ainda consegue tratar
tamanhos com a biblioteca gd.


### Highlights

- Image simple upload (Simples envio de imagems)
- File simple upload (Simples envio de arquivos)
- Media simple upload (Simples envio de midias)
- Managing directories with date schemas (Gestão de diretórios com esquema de datas)
- Validation of images, files and media by mime-types (Valida de imagens, arquivos e mídias por mime-types)
- Composer ready and PSR-2 compliant (Pronto para o composer e compatível com PSR-2)

## Installation

Uploader is available via Composer:

```bash
"jpsistemasbr/uploader": "2.0.*"
```

or run

```bash
composer require jpsistemasbr/uploader
```

## Documentation

###### For details on how to use the upload, see a sample folder in the component directory. In it you will have an example of use for each class. JPsistemasBR Uploader works like this:

Para mais detalhes sobre como usar o upload, veja uma pasta de exemplo no diretório do componente. Nela terá um exemplo
de uso para cada classe. JPsistemasBR Uploader funciona assim:

#### Upload Image

```php
<?php

$image = new JPsistemasBR\Uploader\Image("uploads", "images", 600);

if ($_FILES) {
    try {
        $upload = $image->upload($_FILES['image'], $_POST['name']);
        echo "<img src='{$upload}' width='100%'>";
    } catch (Exception $e) {
        echo "<p>(!) {$e->getMessage()}</p>";
    }
}
```

#### Upload File

```php
<?php

$file = new JPsistemasBR\Uploader\File("uploads", "files");

if ($_FILES) {
    try {
        $upload = $file->upload($_FILES['file'], $_POST['name']);
        echo "<p><a href='{$upload}' target='_blank'>@JPsistemasBR</a></p>";
    } catch (Exception $e) {
        echo "<p>(!) {$e->getMessage()}</p>";
    }
}
```

#### Upload Media

```php
<?php

$media = new JPsistemasBR\Uploader\Media("uploads", "medias");

if ($_FILES) {
    try {
        $upload = $media->upload($_FILES['file'], $_POST['name']);
        echo "<p><a href='{$upload}' target='_blank'>@JPsistemasBR</a></p>";
    } catch (Exception $e) {
        echo "<p>(!) {$e->getMessage()}</p>";
    }
}
```

#### Upload by Filetype (Send)

```php
<?php

$postscript = new JPsistemasBR\Uploader\Send("uploads", "postscript", [
    "application/postscript"
], ["ai"]);

if ($_FILES) {
    try {
        $upload = $postscript->upload($_FILES['file'], $_POST['name']);
        echo "<p><a href='{$upload}' target='_blank'>@JPsistemasBR</a></p>";
    } catch (Exception $e) {
        echo "<p>(!) {$e->getMessage()}</p>";
    }
}
```

#### Upload Multiple

```php

$image = new JPsistemasBR\Uploader\Image("uploads", "images");

try {
    foreach ($image->multiple("file", $_FILES) as $file) {
        $image->upload($file, "image-" . $file["name"], 1200);
    }
    echo "Success!";
} catch (Exception $e) {
    echo "<p>(!) {$e->getMessage()}</p>";
}
```


## Support

###### Security: If you discover any security related issues, please email jpsistemasbr@gmail.com instead of using the issue tracker.

Se você descobrir algum problema relacionado à segurança, envie um e-mail para cursos@upinside.com.br em vez de usar o
rastreador de problemas.

Thank you

## Credits

- [Robson V. Leite](https://github.com/jpsistemasbr) (Developer)

## License

The MIT License (MIT). Please see [License File](https://github.com/jpsistemasbr/uploader/blob/master/LICENSE) for more
information.
