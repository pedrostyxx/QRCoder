# QRCoder

|Build|Code coverage|Build status|NuGet Package|
|-----|-------------|------------|-------------|
|Latest / Stable|[![codecov](https://codecov.io/gh/codebude/QRCoder/branch/master/graph/badge.svg?token=3yNs88KD8S)](https://codecov.io/gh/codebude/QRCoder)|[![Build, test, pack, push (Release)](https://github.com/codebude/QRCoder/actions/workflows/wf-build-release.yml/badge.svg?branch=master)](https://github.com/codebude/QRCoder/actions/workflows/wf-build-release.yml)|[![NuGet Badge](https://buildstats.info/nuget/QRCoder?rnd=0892982314)](https://www.nuget.org/packages/QRCoder/)|
|CI / Last commit|[![codecov](https://codecov.io/gh/codebude/QRCoder/branch/master/graph/badge.svg?token=3yNs88KD8S)](https://codecov.io/gh/codebude/QRCoder)|[![Build, test, pack, push (CI)](https://github.com/codebude/QRCoder/actions/workflows/wf-build-release-ci.yml/badge.svg)](https://github.com/codebude/QRCoder/actions/workflows/wf-build-release-ci.yml)|[![Github packages](https://img.shields.io/badge/Github-Packages-blue)](https://github.com/codebude/qrcoder/packages)|


## Info

QRCoder is a simple library, written in C#.NET, which enables you to create QR codes. It hasn't any dependencies to other libraries and is available as .NET Framework and .NET Core PCL version on NuGet.

Feel free to grab-up/fork the project and make it better!

For more information see:
[**QRCode Wiki**](https://github.com/codebude/QRCoder/wiki) | [Creator's blog (english)](http://en.code-bude.net/2013/10/17/qrcoder-an-open-source-qr-code-generator-implementation-in-csharp/) | [Creator's blog (german)](http://code-bude.net/2013/10/17/qrcoder-eine-open-source-qr-code-implementierung-in-csharp/)

### Release Notes
The release notes for the current and all past releases can be read here: [📄 Release Notes](https://github.com/codebude/QRCoder/wiki/Release-notes)

## Legal information and credits

QRCoder is a project by [Raffael Herrmann](https://raffaelherrmann.de) and was first released in 10/2013. It's licensed under the [MIT license](https://github.com/codebude/QRCoder/blob/master/LICENSE.txt).


* * *


## Installation

Either checkout this Github repository or install QRCoder via NuGet Package Manager. If you want to use NuGet just search for "QRCoder" or run the following command in the NuGet Package Manager console:
```bash
PM> Install-Package QRCoder
```

#### CI builds
The NuGet feed contains only **major/stable** releases. If you want the latest functions and features, you can use the CI builds [via Github packages](https://github.com/codebude/qrcoder/packages).
_(More information on how to use Github Packages in Nuget Package Manager can be [found here](http://webcache.googleusercontent.com/search?q=cache:i_gL6oIwpr8J:www.catiawidgets.net/2021/04/20/creating-github-packages-and-accessing-them-in-nuget/+&cd=1&hl=de&ct=clnk&gl=de).)_


## Usage

You only need four lines of code, to generate and view your first QR code.

```csharp
QRCodeGenerator qrGenerator = new QRCodeGenerator();
QRCodeData qrCodeData = qrGenerator.CreateQrCode("The text which should be encoded.", QRCodeGenerator.ECCLevel.Q);
PngByteQRCode qrCode = new PngByteQRCode(qrCodeData);
byte[] qrCodeImage = qrCode.GetGraphic(20);
```

### Optional parameters and overloads

The GetGraphics-method has some more overloads. The first two enable you to set the color of the QR code graphic. One uses Color-class-types, the other HTML hex color notation.

```csharp
//Set color by using Color-class types
Bitmap qrCodeImage = qrCode.GetGraphic(20, Color.DarkRed, Color.PaleGreen, true);

//Set color by using HTML hex color notation
Bitmap qrCodeImage = qrCode.GetGraphic(20, "#000ff0", "#0ff000");
```

The other overload enables you to render a logo/image in the center of the QR code.

```csharp
Bitmap qrCodeImage = qrCode.GetGraphic(20, Color.Black, Color.White, (Bitmap)Bitmap.FromFile("C:\\myimage.png"));
```

There are a plenty of other options. So feel free to read more on that in our wiki: [Wiki: How to use QRCoder](https://github.com/codebude/QRCoder/wiki/How-to-use-QRCoder)

### Special rendering types

Besides the normal QRCode class (which is shown in the example above) for creating QR codes in Bitmap format, there are some more QR code rendering classes, each for another special purpose.

* [QRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#21-qrcode-renderer-in-detail)
* [ArtQRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#211-artqrcode-renderer-in-detail)
* [AsciiQRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#22-asciiqrcode-renderer-in-detail)
* [Base64QRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#23-base64qrcode-renderer-in-detail)
* [BitmapByteQRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#24-bitmapbyteqrcode-renderer-in-detail)
* [PdfByteQRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#210-pdfbyteqrcode-renderer-in-detail)
* [PngByteQRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#25-pngbyteqrcode-renderer-in-detail)
* [PostscriptQRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#29-postscriptqrcode-renderer-in-detail)
* [SvgQRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#26-svgqrcode-renderer-in-detail)
* [UnityQRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#27-unityqrcode-renderer-in-detail) (_via [QRCoder.Unity](https://www.nuget.org/packages/QRCoder.Unity)_)
* [XamlQRCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#28-xamlqrcode-renderer-in-detail) (_via [QRCoder.Xaml](https://www.nuget.org/packages/QRCoder.Xaml)_)

*Note: Please be aware that not all renderers are available on all target frameworks. Please check the [compatibility table](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers#2-overview-of-the-different-renderers) in our wiki, to see if a specific renderer is available on your favourite target framework.*  



For more information about the different rendering types click on one of the types in the list above or have a look at: [Wiki: Advanced usage - QR-Code renderers](https://github.com/codebude/QRCoder/wiki/Advanced-usage---QR-Code-renderers)

## PayloadGenerator.cs - Generate QR code payloads

Technically QR code is just a visual representation of a text/string. Nevertheless most QR code readers can read "special" QR codes which trigger different actions.

For example: WiFi-QRcodes which, when scanned by smartphone, let the smartphone join an access point automatically.

This "special" QR codes are generated by using special structured payload string, when generating the QR code. The [PayloadGenerator.cs class](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators) helps you to generate this payload strings. To generate a WiFi payload for example, you need just this one line of code:

```csharp
PayloadGenerator.WiFi wifiPayload = new PayloadGenerator.WiFi("MyWiFi-SSID", "MyWiFi-Pass", PayloadGenerator.WiFi.Authentication.WPA);
```

To generate a QR code from this payload, just call the "ToString()"-method and pass it to the QRCoder.

```csharp
//[...]
QRCodeData qrCodeData = qrGenerator.CreateQrCode(wifiPayload.ToString(), QRCodeGenerator.ECCLevel.Q);
//[...]
```

You can also use overloaded method that accepts Payload as parameter. Payload generator can have QR Code Version set (default is auto set), ECC Level (default is M) and ECI mode (default is automatic detection).

```csharp
//[...]
QRCodeData qrCodeData = qrGenerator.CreateQrCode(wifiPayload);
//[...]
```

Or if you want to override ECC Level set by Payload generator, you can use overloaded method, that allows setting ECC Level.

```csharp
//[...]
QRCodeData qrCodeData = qrGenerator.CreateQrCode(wifiPayload, QRCodeGenerator.ECCLevel.Q);
//[...]
```


You can learn more about the payload generator [in our Wiki](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators).

The PayloadGenerator supports the following types of payloads:

* [BezahlCode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#31-bezahlcode)
* [Bitcoin-Like cryptocurrency (Bitcoin, Bitcoin Cash, Litecoin) payment address](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#32-bitcoin-like-crypto-currency-payment-address)
* [Bookmark](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#33-bookmark)
* [Calendar events (iCal/vEvent)](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#34-calendar-events-icalvevent)
* [ContactData (MeCard/vCard)](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#35-contactdata-mecardvcard)
* [Geolocation](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#36-geolocation)
* [Girocode](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#37-girocode)
* [Mail](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#38-mail)
* [MMS](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#39-mms)
* [Monero address/payment](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#310-monero-addresspayment)
* [One-Time-Password](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#311-one-time-password)
* [Phonenumber](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#312-phonenumber)
* [RussiaPaymentOrder (ГОСТ Р 56042-2014)](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#313-russiapaymentorder)
* [Shadowsocks configuration](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#314-shadowsocks-configuration)
* [Skype call](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#315-skype-call)
* [SlovenianUpnQr](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#316-slovenianupnqr)
* [SMS](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#317-sms)
* [SwissQrCode (ISO-20022)](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#318-swissqrcode-iso-20022)
* [URL](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#319-url)
* [WhatsAppMessage](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#320-whatsappmessage)
* [WiFi](https://github.com/codebude/QRCoder/wiki/Advanced-usage---Payload-generators#321-wifi)
