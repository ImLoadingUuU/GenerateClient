# VPClient
![VPClient](vpclient.png)

A VistaPanel API client in PHP.

VistaPanel is a web hosting control panel that allows users to manage their websites, email accounts, databases, and other aspects of their hosting environment.  
A VistaPanel API client is a program that can interact with VistaPanel using the VistaPanel API (Application Programming Interface). The API provides a set of methods that can be used to manage various aspects of the hosting environment programmatically.
# API Documentation

The VistaPanel Users API allows you to interact with the VistaPanel hosting control panel using PHP. It provides methods for performing various tasks such as logging in, managing databases, working with domains, creating redirects, uploading SSL certificates, and more.

## Class: VistapanelApi

### Properties

- `cpanelUrl`: The URL of the VistaPanel control panel.
- `loggedIn`: Indicates whether the user is logged in or not.
- `vistapanelSession`: The session ID obtained after logging in.
- `vistapanelSessionName`: The name of the session cookie.
- `vistapanelToken`: The token used for API requests.
- `accountUsername`: The username of the logged-in account.
- `cookie`: The cookie string used for authentication.

### Methods

#### `setCpanelUrl($url)`

Sets the URL of the VistaPanel control panel.

- `$url` (string): The URL of the control panel.

#### `login($username, $password, $theme)`

Logs in to the VistaPanel control panel.

- `$username` (string): The username of the account.
- `$password` (string): The password of the account.
- `$theme` (string): The theme to use after logging in (default: "PaperLantern").

#### `createDatabase($dbname)`

Creates a new database.

- `$dbname` (string): The name of the database, without the account prefix.

#### `listDatabases()`

Returns an array of databases associated with the logged-in account.

#### `deleteDatabase($database)`

Deletes a database.

- `$database` (string): The name of the database, without the account prefix.

#### `getPhpmyadminLink($database)`

Returns the phpMyAdmin link for a specific database.

- `$database` (string): The name of the database, without the account prefix.

#### `listDomains($option)`

Returns an array of domains in a specific category.

- `$option` (string): The category of domains to retrieve. Available options: "addon", "sub", and "parked" (default: "addon").

#### `createRedirect($domainname, $target)`

Creates a redirect for a domain.

- `$domainname` (string): The name of the domain.
- `$target` (string): The target URL for the redirect.

#### `deleteRedirect($domainname)`

Deletes a redirect for a domain.

- `$domainname` (string): The name of the domain.

#### `uploadKey($domainname, $key, $csr)`

Uploads an SSL key for a domain.

- `$domainname` (string): The name of the domain.
- `$key` (string): The content of the SSL key file.
- `$csr` (string): The content of the Certificate Signing Request (CSR) file.

#### `uploadCert($domainname, $cert)`

Uploads an SSL certificate for a domain.

- `$domainname` (string): The name of the domain.
- `$cert` (string): The content of the SSL certificate file.

#### `getSoftaculousLink()`

Returns the Softaculous link for the control panel.

#### `logout()`

Logs out from the control panel, and resets client configuration.

#### `approveNotification()`

Allow iFastNet to send you notifications about Account Suspensions, also unlock vPanel.

## Example Usage

```php
<?php
require_once 'VistapanelApi.php';

$vpClient = new VistapanelApi();
$vpClient->setCpanelUrl('https://example.com');
$vpClient->login('username', 'password');

$databases = $vpClient->listDatabases();
foreach ($databases as $database => $value) {
    echo $database . "\n";
}

$vpClient->logout();
?>
```
---

Fork of [VistaPanel PHP API](https://github.com/oddmario/vistapanel-php-api)
