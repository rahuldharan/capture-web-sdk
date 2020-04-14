
# Capture WebSDK

The `capture-web-sdk` library is used to capture documents and faces at an appropriate resolution for our face match and document OCR APIs.

## Overview

Adding the SDK to your project is as simple as following these steps:

- Add the SDK source in your project in your `head` tag.

```javascript
<script src="https://hv-camera-web-sg.s3-ap-southeast-1.amazonaws.com/HypervergeSDK.js"></script>
```

- Initialising the instance and passing a callback function to access the saved image after it is captured.

```javascript

function callback(img) {
  // img is the base64 encoded captured image from the SDK.
}


let selfieCapture = new createHypervergeInstance({
  params: {
    mode: "selfie",
    imagename: "selfie.jpg",
    onSave: callback,
   }
});

```

`capture-web-sdk` is HyperVerge's Document and Face capture SDK from the web browsers. This library can be used in any framework as mentioned on the right.

## Requirements
* JavaScript enabled browsers
* HTTPS based website
* Attached Video Input Source (Camera)

## Integration Steps

### Adding the SDK to your project

Before the SDK can be used, the SDK can be added to your project by adding this code in your HTML code.


### Create a HyperVerge Instance

```javascript
let hvCamera = new createHypervergeInstance({
    params: {}
})
```

### Create the callback function to access the captured image in the base64 format.

```javascript
function callback(imagesrc, blobImg) { 
  // Here you can use base64 image which comes as attribute
}
```

### Query Parameters

| Parameter       | Default           | Accepted  Values                                 | Description                                                  |
| --------------- | ----------------- | ------------------------------------------------ | ------------------------------------------------------------ |
| mode            | document          | document,selfie                                  | Determines for what purpose SDK is required. document mode opens back camera with aspect ratio defined in document type. selfie mode opens front camera with circle overlay for selfie capture |
| documentType    | CARD              | CARD,A4,PASSPORT,OTHER                           | Determines aspect ratio of camera opened. More details about document type is given below |
| onSave          |                   | javascript function as callback                  | On successful image capture. Callback function which is passed in onSave parameter is called with base64 image as attribute. |
| imageName       | image.jpeg        | any string with jpg/png/jpeg extension           | If this parameter is passed SDK will create local storage variable with given filename. Which can be used by localStorage.getItem(<imagename provided>); |
| imageFormat    | jpeg              | jpg,png,jpeg                                     | It should be used with imagename parameter to save image file in repective extension |
| uploadURL       |                   | Valid URL(e.g. https://example.com/captureimage) | If this parameter is provided SDK will pass image data to provided URL as an AJAX request |
| jpegQuality   | 100               | integer between 0 to 100                         | It determines quality of captured image. 0 is worst quality and 100 is best quality |
| width           | 640               | any integer value                                | It determines width of video stream to be opened. It is rarely used parameter and should be used with caution |
| ratio           | 1                 | any value between 0 and 1                        | It determines aspect ratio of video stream. Again rarely used and should be used with caution. |
| captureTopTitle | "Capture ID Card" | any string value                                 | It determines heading of document capture screen             |
| selfieTopTitle  | "Capture Selfie"  | any string value                                 | It determines heading of selfie capture screen               |
| reviewTopTitle | "Review Your Photo" | any string value                                 | It determines heading of review screen             |
| captureTopText  |  "Make sure your document is without any glare and is fully inside"  | any string value                                 | It determines instructions of document capture screen               |
|selfieTopText  |  "Make sure your face is inside the circle and is fully visible"  | any string value                                 | It determines instructions of selfie capture screen               |
|reviewTopText  |  "Is your document fully visible, glare free and not blurred?"  | any string value                                 | It determines instructions of document review  screen               |
|selfieReviewTopText  |  "Is your face fully visible, and not blurred?"  | any string value                                 | It determines instructions of selfie review  screen               |
|retakeBtnText  | "Retake Photo"  | any string value                                 | It determines text of retake button               |
|useThisBtnText  | "Use this Photo"  | any string value                                 | It determines text of final submit button               |


## Supported Document Types

- Following are the document types supported by the Document enum:

    - CARD: Aspect ratio: 0.625. Following documents require CARD aspect ratio.

      - Aadhaar Card (India)
      - PAN Card (India)
      - Driving License (India & Vietnam)
      - National ID (Vietnam)
      - MRC (Vietnam)

    - PASSPORT: Aspect ratio: 0.67. This is for Passports.

    - A4: Aspect ratio: 1.4. Following documents require.

      - Bank statement
      - Insurance receipt
      - EVN (Vietnam)

    - OTHER: This is for aspect ratios that don't fall in the above categories. In this case, the aspect ratio should be set as shown.

      ```javascript
      let hvCamera = new createHypervergeInstance({
          params:{
              ratio: 1
          }
      })
      ```

      Following documents might require `OTHER` aspect ratio.

      - Voter ID (India) (here, set aspect ratio to 1.4)

  
---
For any support, please reach out to our [Support Team](mailto:support@hyperverge.co).


