#  spark-core-mdns

Multicast DNS and DNS-SD for the Spark Core

##  Example

Register a service on HTTP port 80:

```c++

#define HTTP_PORT 80

MDNS mdns;

void setup() {

    // Wait for WiFi to connect
    while (!WiFi.ready()) {
      // empty
    }

    bool success = mdns.setHostname("myservice");
    if (success) {
      success = mdns.addService("tcp", "http", HTTP_PORT, "MyService");
    }
    mdns.addTXTEntry("normal");

    if (success) {
      success = mdns.begin();
    }
}

void loop() {
  mdns.processQueries();

  // Do your magic stuff here :)
}
```

For more examples please take a look [here](firmware/examples/mdns.ino)
