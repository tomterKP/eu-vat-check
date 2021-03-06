eu-vat-check
============

Verify the validity of a VAT number issued by any Member State of the European Union.

More info about this subject is found [here](http://ec.europa.eu/taxation_customs/vies/).

Requirements
------------

* Java 1.7+

Usage
-----

Add the linkID repositories to your pom file:
```xml
<!-- REMOTE ARTIFACT REPOSITORIES -->
<repositories>
    <repository>
        <id>repo.linkid.be.release</id>
        <name>LinkID Public Repository</name>
        <url>http://repo.linkid.be/releases</url>
        <snapshots>
            <enabled>false</enabled>
            <updatePolicy>never</updatePolicy>
        </snapshots>
        <releases>
            <enabled>true</enabled>
            <updatePolicy>never</updatePolicy>
        </releases>
    </repository>
    <repository>
        <id>repo.linkid.be.snapshot</id>
        <name>LinkID Public Repository</name>
        <url>http://repo.linkid.be/snapshots</url>
        <snapshots>
            <enabled>true</enabled>
            <updatePolicy>always</updatePolicy>
        </snapshots>
        <releases>
            <enabled>false</enabled>
            <updatePolicy>never</updatePolicy>
        </releases>
    </repository>
</repositories>
```

Add the eu-vat-check-client dependency to your pom file:
```xml
<dependency>
    <groupId>net.lin-k.eu.eu-vat-check</groupId>
    <artifactId>eu-vat-check-client</artifactId>
    <version>0.4</version>
</dependency>
```

Example code:
```java
CountryCode countryCode = CountryCode.BE;
String vatNumber        = "0446495156";

logger.inf( "VAT Number check for %s %s", countryCode, vatNumber );

VatCheckServiceClient vatCheckServiceClient = new VatCheckServiceClient( countryCode, vatNumber );

boolean valid = vatCheckServiceClient.isVatNumberValid();

//After isVatNumberValid() you can get the name and address of the enterprise
logger.inf( "Returned: valid=%s; name=%s; address=%s",
        valid, vatCheckServiceClient.getName(), vatCheckServiceClient.getAddress() );
```

RELEASE NOTES
=============

v0.5 (2016-06-23)
-----------------

* Release for repo.linkid.be move

v0.4 (2014-03-11)
-----------------

* Added some utility methods. (See VATUtil class)

v0.3 (2013-12-17)
-----------------

* Updated the WSDL location.

v0.2 (2013-12-02)
-----------------

* Implemented all country codes.

v0.1 (2013-11-29)
-----------------

* Initial release.