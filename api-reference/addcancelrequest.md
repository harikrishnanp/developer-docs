+++
title = "AddCancelRequest"
toc = true
+++

Adds a Cancellation Request

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddCancelRequest" | Required |
| serviceid | int | The Service ID to cancel | Required |
| type | string | The type of cancellation. 'Immediate' or 'End of Billing Period' | Optional |
| reason | string | The customer reason for cancellation | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| serviceid | int | The id of the service the request was for |
| userid | int | The id of the user the service belongs to |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddCancelRequest',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'serviceid' => '1',
            'type' => 'Immediate',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'AddCancelRequest';
$postData = array(
    'serviceid' => '1',
    'type' => 'Immediate',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "serviceid": "1",
    "userid": "1"
}
```


### Error Responses

Possible error condition responses include:

* Service ID Not Found
* Existing Cancellation Request Exists


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
