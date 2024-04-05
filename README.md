# blast.io
Blast Engine is an Enterprise NIO web proxy server for running on Node or Kubernetes Ingress which provide Throttling, Security and Speed traffic analysis control


## synopsis

- Sample configuration
```yml
licenseKey: /path/to/your/license.yaml
enableAdmin: true
ioThreads: 4
workers: 4
bufferSize: 102400
ocspStapling: true
http:
- id: blast-web-uat
  port: 80
  sslPort: 443
  ssl: true
  sslProtocols: TLSv1.2,TLSv1.3
  sslCiphers: TLS_AES_256_GCM_SHA384:TLS_AES_128_GCM_SHA256:TLS_CHACHA20_POLY1305_SHA256:TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384:TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256:TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256:TLS_DHE_RSA_WITH_AES_256_GCM_SHA384:TLS_DHE_RSA_WITH_AES_128_GCM_SHA256
  socketOption: {}
  serverOption:
    MAX_BUFFERED_REQUEST_SIZE: 49152
    RECORD_REQUEST_START_TIME: true
  apps:
    - name: frontend.app.com
      aliasName: [frontend-staging.app.com]
      include!: proxy_common.yml ## direct include file
      forceHttps: true
      locations:
      - include!: location_common.yml ## direct include file
        resource:
          dirPath: /path/to/your/resources ## Resource folder
          targetPath: /a
        upstreams:
          - http://192.168.1.33:9099
    - name: backend.app.com
      tlsCert: /path/to/your/cert.pem
      tlsKey: /path/to/your/privatekey.pem
      connectionPerThread: 20
  	  problemServerRetry: 3
  	  secureHeader: true
  	  csp: "default-src 'self' data:; script-src 'self ...."
  	  readBody: false
  	  runNio: true
  	  wafs:
  	    - path: /
  	      regex: true
  	      sqli: true
  	      mz: BODY|ARGS_FILE
  	      warn: true
  	      rule: ".+?\\.php[?&]|.+?\\.php"
  	      score: 100
      locations: 
      - exact: false
        location: /api
        upstreams:
        - http://192.168.1.34:9099
      - exact: true
        location: /
        upstreams:
        - http://192.168.1.35:9099


```

# Powerful Web Proxy Security Server

## Overview

The Powerful Web Proxy Security Server is a cutting-edge solution designed to enhance the security and performance of web applications and services. With its advanced features and robust architecture, it provides comprehensive protection against various threats and vulnerabilities.

## Features

### Web Application Firewall (WAF) Protection Support

- **Real-time Threat Detection**: The WAF feature monitors incoming web traffic in real-time to detect and block malicious requests and attacks.
- **Customizable Rules**: Users can define and customize WAF rules to meet specific security requirements and policies.
- **Log and Reporting**: Detailed logs and reports are generated to provide insights into the detected threats and security events.

### High-End Throttling Control

- **Rate Limiting**: The throttling control feature allows administrators to set rate limits for incoming requests to prevent abuse and ensure optimal performance.
- **Download Rate Limiting**: The throttling control feature allows administrators to set rate limits for incoming requests to prevent abuse and ensure optimal performance.
- **Dynamic Throttling**: Advanced algorithms adjust throttling settings dynamically based on traffic patterns and server load.
- **Granular Control**: Administrators can configure throttling rules based on various parameters such as IP address, user agent, and request method.

### Zero Downtime Config Deployment

- **Seamless Updates**: The zero downtime config deployment ensures that configuration changes are applied without interrupting ongoing traffic or services.
- **Rollback Capabilities**: In case of any issues or errors during deployment, the system allows for quick and easy rollback to the previous configuration.
- **Automated Synchronization**: Configuration changes are automatically synchronized across multiple servers and instances to maintain consistency and reliability.

### Kubernetes Ingress Support

- **Native Integration**: The server offers native support for Kubernetes Ingress, making it easy to deploy and manage web proxy configurations within Kubernetes clusters.
- **Automatic Scaling**: The server can automatically scale resources based on the demand and traffic load within the Kubernetes environment.
- **Enhanced Visibility**: Integration with Kubernetes provides enhanced visibility and control over web traffic, allowing for better monitoring and management of applications and services.

## Conclusion

The Powerful Web Proxy Security Server is a comprehensive solution that combines advanced web proxy capabilities with robust security features to protect and optimize web applications and services. With its support for WAF protection, high-end throttling control, zero downtime config deployment, and Kubernetes ingress, it offers unparalleled performance, scalability, and security for modern web environments.



### Please kindly follow the [instruction.md](./instruction.md) for further details, please support us as below

[![ko-fi](https://storage.ko-fi.com/cdn/kofi2.png)](https://ko-fi.com/blastblast43267/shop)

