##Integrate adjust with Mixpanel SDK

Mixpanel API allows to register common properties to be sent in all events as `"super properties"`, as it is explained in the [Mixpanel page][mixpanel_ios]. To integrate adjust with all tracked events of Mixpanel, register the following properties. Replace the values between braces `{value}` with the correspondent value.

```objc
Mixpanel *mixpanel = [Mixpanel sharedInstance];

// The adjust properties properties will be sent
// with all future track calls.
[mixpanel registerSuperProperties:@{@"[Adjust]Network": @"{Network}"}];
[mixpanel registerSuperProperties:@{@"[Adjust]Campaign": @"{Campaign}"}];
[mixpanel registerSuperProperties:@{@"[Adjust]Adgroup": @"{AdgroupValue}"}];
[mixpanel registerSuperProperties:@{@"[Adjust]Creative": @"{CreativeValue}"}];
```

[mixpanel_ios]: https://mixpanel.com/help/reference/ios#super-properties
