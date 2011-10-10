# Stripe Java Bindings

Requirements
============

Java 1.5 and later

Installation
============

### Maven users

Add this dependency to your project's POM:

    <dependency>
      <groupId>com.stripe</groupId>
      <artifactId>stripe-java</artifactId>
      <version>...</version>
    </dependency>

### Others

Download the following JARs:

* The packaged Stripe JAR from https://oss.sonatype.org/content/repositories/releases/com/stripe/stripe-java/
* [Google Gson](http://code.google.com/p/google-gson/) from <http://google-gson.googlecode.com/files/google-gson-1.7.1-release.zip>.
* [Apache HttpClient](http://hc.apache.org/httpcomponents-client-ga/index.html) from <http://www.alliedquotes.com/mirrors/apache/httpcomponents/httpclient/binary/httpcomponents-client-4.1.2-bin.tar.gz>.

Usage
=====

StripeExample.java

    import java.util.HashMap;
    import java.util.Map;

    import com.stripe.Stripe;
    import com.stripe.exception.StripeException;
    import com.stripe.model.Charge;

    public class StripeExample {

        public static void main(String[] args) {
            Stripe.apiKey = "YOUR-SECRET-KEY";
            Map<String, Object> chargeMap = new HashMap<String, Object>();
            chargeMap.put("amount", 100);
            chargeMap.put("currency", "usd");
            Map<String, Object> cardMap = new HashMap<String, Object>();
            cardMap.put("number", "4242424242424242");
            cardMap.put("exp_month", 12);
            cardMap.put("exp_year", 2012);
            chargeMap.put("card", cardMap);
            try {
                Charge charge = Charge.create(chargeMap);
                System.out.println(charge);
            } catch (StripeException e) {
                e.printStackTrace();
            }
        }
    }


See [StripeTest.java](https://github.com/stripe/stripe-java/blob/master/src/test/java/com/stripe/StripeTest.java) for more examples.