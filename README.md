# Apache Tika CI/CD pipeline

<a href="https://dash.elest.io/deploy?source=cicd&social=dockerCompose&url=https://github.com/elestio-examples/tika"><img src="deploy-on-elestio.png" alt="Deploy on Elest.io" width="180px" /></a>

Deploy Apache Tika server with CI/CD on Elestio

<img src="tika.png" style='width: 100%;'/>
<br/>
<br/>

# Once deployed ...

You can open Apache Tika here:

    https://[CI_CD_DOMAIN]/
    Login: root
    password: [ADMIN_PASSWORD]

# Languages in Tesseract OCR

Tesseract OCR is a powerful optical character recognition engine, and by default, it comes with support for languages such as English, French, German, Italian, and Spanish. However, if you need additional languages, you can easily install them by following the steps below:

1.  Access Elestio Dashboard

    Navigate to the Elestio dashboard and click on the "Overview" section.

2.  Open Terminal

    Locate the "Open terminal" button positioned at the top right corner of the dashboard and click on it.

3.  Execute Installation Command

    Once the terminal opens, paste the following command to install the Portuguese language pack:

        docker-compose exec -T tika /bin/bash -c "apt-get update && apt-get install -y tesseract-ocr-por"

## Additional Languages

If you need support for languages other than Portuguese, you can modify the installation command accordingly. Simply replace `tesseract-ocr-por` with the appropriate package name for your desired language.

# Using Apache Tika with cURL Commands

Apache Tika provides a convenient way to extract metadata from various file types using cURL commands. Follow the examples and instructions below to utilize Apache Tika in the folder where your document is located.

## Metadata Extraction

To extract metadata from your files, you can use the following cURL command as an example for a PDF file:

    curl -u root:[ADMIN_PASSWORD] -T test.pdf https://[CI_CD_DOMAIN]/meta

This command retrieves metadata from the specified PDF file.

### Specific Metadata

Each file type has a different set of metadata. To view specific metadata, such as Content-Type, you can modify the cURL command with the appropriate URL:

    curl -u root:[ADMIN_PASSWORD] -T test.pdf https://[CI_CD_DOMAIN]/meta/Content-Type

This command specifically fetches the Content-Type metadata for the given PDF file.

### Supported File Formats

These cURL commands can be used for various file formats, including:

- PDF
- DOCX
- ODT
- TXT
- PNG
- JPG

Feel free to adapt these commands to fit your specific use case and explore the wealth of metadata available for different file types.

## Text extraction

One of the primary features of Apache Tika is text extraction. To extract the contents of a file, for example, `test.docx`, using the Tika server, you can use the following cURL command:

    curl -u root:[ADMIN_PASSWORD] -T test.docx https://[CI_CD_DOMAIN]/tika

his command retrieves the textual content from the specified DOCX file.

## OCR (Optical Character Recognition)

Apache Tika seamlessly integrates with Tesseract OCR for extracting content from images. To perform OCR on a PNG file, you can use the following cURL command:

    curl -u root:[ADMIN_PASSWORD] -T test.png http://localhost:9998/tika

This command utilizes Tesseract OCR to extract text from the specified PNG file.

## Documentation

For more informations click <a targer="_blank" href="https://cwiki.apache.org/confluence/display/TIKA/TikaServer">here</a> to explore the documentation.
