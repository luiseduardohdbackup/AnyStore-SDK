AnyStore SDK Integration Guide
====

##1. Package
---
SDK: AnyStore SDK integration files

Demo: A Demo project demostrates how to integrate AnyStore SDK

docs: Documentations

##2. Setup
---
Copy every thing under SDK folder to your porject folder

##3. Edit AndroidManifest
---
Adding the following permission to AndroidManifest.xml

```xml
<uses-permissionandroid:name="android.permission.INTERNET"/>

<serviceandroid:name="com.ckmobilling.CkService"


```xml
<application

##4. Initialize AnyStore SDK

---
####Add the following line to your `Application` Class

```java
import com.ckmobilling.CkSdkApi;

public class App extends Application {

```
####Add the folloing line to your `Activity` Class

```java
import com.ckmobilling.CkSdkApi;
import com.ckmobilling.PaymentCallback;
import com.ckmobilling.PaymentResult;

protected void onCreate(Bundle savedInstanceState) {


@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
	super.onActivityResult(requestCode, resultCode, data);
	CkSdkApi.getInstance().onActivityResult(requestCode, resultCode, data);
}

@Override
protected void onDestroy() {
	super.onDestroy();
	CkSdkApi.getInstance().onDestroy();
}

##5. Send Payment
---

Use `doPayment` perform IAP

```java
public void doPayment(Context context, String PayCode, PaymentCallback callback);
```
Context: The `Activity` where it was created

PayCode: The ID for the IAP item

Callback: The callback for this transaction

```java
CkSdkApi.getInstance().doPayment(MainActivity.this, "0007", new PaymentCallback() {

	@Override
	public void paySuccess(PaymentResult result) {
	}

	@Override
	public void payFailed(PaymentResult result) {
	}

	@Override
	public void payCanceled(PaymentResult result) {
	}
	
});
```

The `PaymentResult` returns from the callback will contain the PayCode indicating which item is associated with the payment