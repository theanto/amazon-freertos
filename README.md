## Getting Started

For more information on getting started with your download, refer to the [Getting Started section of Amazon FreeRTOS webpage](https://aws.amazon.com/freertos).

For more information on Amazon FreeRTOS, refer to the [Amazon FreeRTOS User Guide](https://aws.amazon.com/documentation/freertos).

## Hardware Requirements

Use the following MCU hardware to get started:
1. **Texas Instruments** - [CC3220SF-LAUNCHXL](http://www.ti.com/tool/cc3220sf-launchxl).
2. **STMicroelectronics** - [STM32L4 Discovery kit IoT node](http://www.st.com/en/evaluation-tools/b-l475e-iot01a.html).
3. **NXP** - [LPC54018 IoT Module](http://www.nxp.com/LPC-AWS-Module).
4. **Microchip** - [Curiosity PIC32MZEF](http://www.microchipdirect.com/product/search/all/dm320104-BNDL).
5. **Espressif**  -[ESP32-DevKitC & ESP-WROVER-KIT](https://www.espressif.com/en/products/hardware/esp32-devkitc/overview) - **~~SOON~~**

To evaluate Amazon FreeRTOS without using an MCU-based hardware, use the following:
1. **Windows Simulator** - Microsoft Windows 7 or newer, with at least a dual core and a hard-wired Ethernet connection.

## Development Environment

Based on your MCU hardware, download one of the following Integrated Development Environments (IDEs):
1. **Texas Instruments** - [Code Composer Studio](http://www.ti.com/tools-software/ccs.html).
2. **STMicroelectronics** - [STM32 System Workbench](http://openstm32.org/HomePage).
3. **NXP** - [IAR Embedded Workbench](https://www.iar.com/iar-embedded-workbench/partners/nxp).
4. **Microchip** - [MPLAB X IDE](http://www.microchip.com/mplab/mplab-x-ide).
5. **Windows Simulator** - [Visual Studio Community Edition](https://www.visualstudio.com/downloads/).


## User and Permissions 

In the console, create your user and choose Add permissions.

Choose Attach existing policies directly.

In the search box, type:

AmazonFreeRTOSFullAccess 
AWSIoTFullAccess

## Policies

In the AWS IoT console choose Secure, choose Policies and create a policy.

In the Add statements section, choose Advanced mode. 



<b>
	
{	

    "Version": "2012-10-17",     
    "Statement": [
    
    {
        "Effect": "Allow",
        "Action": "iot:Connect",
        "Resource":"arn:aws:iot:<aws-region>:<aws-account-id>:*"
	}, 
    {
        "Effect": "Allow",
        "Action": "iot:Publish",
        "Resource": "arn:aws:iot:<aws-region>:<aws-account-id>:*"
    },
    {
         "Effect": "Allow",
         "Action": "iot:Subscribe",
         "Resource": "arn:aws:iot:<aws-region>>:<aws-account-id>:*"
    },
    {
         "Effect": "Allow",
         "Action": "iot:Receive",
         "Resource": "arn:aws:iot:<aws-region>:<aws-account-id>:*"
    }
    ]
}</b>

## Things

In  the AWS IoT console go to Manage and then create a single Things in this way: 

Type a name for your thing.

Add a certificate for your thing page (choose Create certificate).

Download your private key and certificate.

Choose Activate, because Certificates must be activated prior to use.

Choose Attach a policy to attach.

Choose the policy you just created and choose Register thing.

## Setting System workbench 

Import the Amazon FreeRTOS Sample Code into the STM32 System Workbench

Copy your AWS IoT endpoint from the Endpoint text box. It should look like <1234567890123>.iot.<us-east-1>.amazonaws.com.

In aws_clientcredential.h set clientcredentialMQTT_BROKER_ENDPOINT to your AWS IoT endpoint.

## IoT Credential 

Go to : <BASE_FOLDER>\demos\common\devmode_key_provisioning\CertificateConfigurationTool\CertificateConfigurator.html.

Under Certificate PEM file, choose the <ID>-certificate.pem.crt you downloaded from the AWS IoT console.

Under Private Key PEM file, choose the <ID>-private.pem.key you downloaded from the AWS IoT console.

Choose Generate and save aws_clientcredential_keys.h, and then save the file in <BASE_FOLDER>\demos\common\include.

## Running the example 

In the AWS IoT console go to Test
In the Subscription topic text box, type freertos/demos/echo and then choose Subscribe to topic.




