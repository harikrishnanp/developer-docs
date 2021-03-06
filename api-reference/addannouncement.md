+++
title = "AddAnnouncement"
toc = true
+++

Adds an announcement.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddAnnouncement" | Required |
| date | \datetime | Date in the format YYYY-MM-DD HH:MM:SS | Required |
| title | string |  | Required |
| announcement | string | Announcement text | Required |
| published | bool | Pass as true to publish | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| announcementid | int | The id of the new announcement |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddAnnouncement',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'date' => '2016-01-01 15:30:00',
            'title' => 'Sample announcement',
            'announcement' => 'Text goes here...',
            'published' => '1',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'AddAnnouncement';
$postData = array(
    'date' => '2016-01-01 15:30:00',
    'title' => 'Sample announcement',
    'announcement' => 'Text goes here...',
    'published' => '1',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "announcementid": "1"
}
```


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
