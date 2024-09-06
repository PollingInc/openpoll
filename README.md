# OpenPoll - OpenAPI Quick Poll Specification by Polling.com

This repository contains the OpenAPI 3.0 specification for generating public polls via URL parameters. With this API, you can create multiple types of polls (multiple choice, checkbox, ranking, text input, star rating) programmatically using URL-encoded query parameters. The poll is rendered as a publicly accessible web page.

For users without programming knowledge, you can [use this poll builder](https://polling.com/free-poll-maker) to create polls easily via a web interface.

## Features

- **Multiple poll types**: Supports radio (multiple choice), checkbox, ranking, short text input, and star ratings.
- **Dynamic poll creation**: Polls can be generated dynamically by passing parameters like question title, description, and answer options.
- **Easy embedding**: The generated polls can be embedded directly into your website using iframes or shared as public URLs.

## How It Works

### Poll URL Structure

The poll is generated via a URL with the following query parameters:

- **qTitle**: The title of the poll question.
- **qDesc**: (Optional) A description that provides more context for the poll.
- **type**: The type of question. Can be one of the following:
  - `radio` (multiple choice)
  - `checkbox` (checkbox options)
  - `ranking` (ranking options)
  - `text` (single line text input)
  - `rating` (star rating)
- **a**: One or more answer options (only used for `radio`, `checkbox`, and `ranking` types).

### Example Polls

#### Multiple Choice Poll (Radio)

```
https://app.polling.com/quick-poll?qTitle=What%27s+your+favorite+color%3F&qDesc=Select+the+color+that+best+fits+your+personality.&type=radio&a=Red&a=Blue&a=Green
```

#### Checkbox Poll

```
https://app.polling.com/quick-poll?qTitle=Which+fruits+do+you+like%3F&qDesc=You+can+choose+more+than+one.&type=checkbox&a=Apple&a=Banana&a=Orange
```

#### Star Rating Poll

```
https://app.polling.com/quick-poll?qTitle=How+would+you+rate+this+product%3F&type=rating
```

### Programmatic Poll Creation

You can also create polls programmatically using JavaScript or PHP.

#### JavaScript Example

```javascript
const baseUrl = 'https://app.polling.com/quick-poll';
let query = new URLSearchParams({
    qTitle: "What's your favorite color?",
    qDesc: "Select the color that best fits your personality.",
    type: "radio"
});
const options = ["Red", "Blue", "Green"];
options.forEach(option => {
    query.append('a', option);
});
const finalUrl = `${baseUrl}?${query.toString()}`;
console.log(finalUrl);
```

#### PHP Example

```php
$baseUrl = 'https://app.polling.com/quick-poll';
$query = http_build_query([
    'qTitle' => "What's your favorite color?",
    'qDesc' => "Select the color that best fits your personality.",
    'type' => 'radio'
]);
$options = ["Red", "Blue", "Green"];
foreach ($options as $option) {
    $query .= "&a=" . urlencode($option);
}
echo "{$baseUrl}?{$query}";
```

## How to Use

1. Download the OpenAPI `.yaml` file.
2. Use the OpenAPI spec to integrate the polling API into your application or system.
3. Generate poll URLs dynamically and share them with your audience or embed them in websites.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
