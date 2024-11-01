
# Text-to-HTML Converter

A Django-based web application that converts structured plain text into HTML. This tool is designed to recognize specific syntax in the input text and apply the appropriate HTML tags for a more readable, formatted output. This project supports headers, images (internal and external), links, lists, tables, bold, italic text, and more.

## Features

- **Header Conversion**: Recognizes lines starting with `/`, `//`, `///`, and `////` as H1, H2, H3, and H4 headers, respectively.
- **Image Embedding**: Embeds images with support for internal and external sources, and options for centered or right-aligned images.
- **Link Formatting**: Transforms URLs in the text into HTML anchor (`<a>`) tags, with support for custom anchor text.
- **List and Table Formatting**: Converts plain text syntax into HTML lists (`<ul>`, `<li>`) and tables.
- **Text Styling**: Applies bold and italic styling based on specific syntax.
- **Line Breaks and Paragraphs**: Automatically applies `<br>` and `<p>` tags for line breaks and paragraphs.

## Project Structure

- `text_to_html/`: Main Django project directory.
- `text_to_html_app/`: Contains the application logic, including the `formatHtml` function.
  - `views.py`: Defines the view functions to handle the form submission and text conversion.
  - `urls.py`: Contains URL routes for the app.
  - `templates/`: HTML templates for the web interface.
- `static/images/`: Folder for internal images, allowing users to reference internal images by filename.

## Setup Instructions

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/yourusername/text-to-html.git
   cd text-to-html
   ```

2. **Install Dependencies**:

   Ensure you have Python and Django installed. Install dependencies with:

   ```bash
   pip install -r requirements.txt
   ```

3. **Run Migrations**:

   ```bash
   python manage.py migrate
   ```

4. **Start the Server**:

   ```bash
   python manage.py runserver
   ```

5. **Access the Application**:

   Open your web browser and go to `http://127.0.0.1:8000`.

## Usage Instructions

1. Enter or paste the structured text into the input field on the web page.
2. Submit the form, and the HTML-formatted output will appear on the page.
3. Download or copy the generated HTML code as needed.

### Syntax Guide

Use the following syntax to format your text:

- **Headers**:
  - `/Header 1` for H1
  - `//Header 2` for H2
  - `///Header 3` for H3
  - `////Header 4` for H4
- **Images**:
  - `img__http://example.com/image.jpg__Alt Text__` for an external image
  - `img__image.jpg__Alt Text__` for an internal image
  - `imgcenter__image.jpg__Alt Text__` for centered image
  - `imgright__image.jpg__Alt Text__` for right-aligned image
- **Links**:
  - `__http://example.com__Custom Text__` for a hyperlink with custom anchor text
- **Lists**:
  - `- List item` for list items
- **Tables**:
  - `!!` as a delimiter for columns
- **Bold**:
  - `*Bold Text*`
- **Italic**:
  - `**Italic Text**`

## Examples

### Input:

```
/Welcome to the Site

//Introduction
Here's some introductory text.

img__http://example.com/logo.jpg__Logo Image__

- First item
- Second item

!!Table!!Data!!Example
```

### Output:

```html
<h1>Welcome to the Site</h1>
<h2>Introduction</h2>
<p>Here's some introductory text.</p>
<a href="http://example.com/logo.jpg"><img src="http://example.com/logo.jpg" alt="Logo Image" title="Logo Image" /></a>
<ul>
  <li>First item</li>
  <li>Second item</li>
</ul>
<table class="table table-bordered table-striped table-hover">
  <tr><td>Table</td><td>Data</td><td>Example</td></tr>
</table>
```

## Contributing

Feel free to contribute by submitting pull requests, reporting issues, or suggesting improvements.

