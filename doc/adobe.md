##Integrate adjust with Adobe SDK

To integrate adjust with all tracked events of Adobe SDK, you must send adjust attribution data to Adobe SDK 
after receiving the attribution response from our backend. Follow the steps of the 
[delegate callbacks][response_callbacks] chapter in our iOS SDK guide to implement it. 
The delegate function can be set as the following, to use the Adobe SDK API:

```objc
- (void)adjustAttributionChanged:(ADJAttribution *)attribution {
    NSMutableDictionary *adjustData= [NSMutableDictionary dictionary];
    
    if (attribution.network != nil)
        // Do not change the key "Adjust Network". This key is being used in the Data Connector Processing Rule
        [adjustData setObject:@attribution.network forKey:@"Adjust Network"]; 
    if (attribution.campaign != nil)
        // Do not change the key "Adjust Campaign". This key is being used in the Data Connector Processing Rule
        [adjustData setObject:@attribution.campaign forKey:@"Adjust Campaign"];
    if (attribution.adgroup != nil)
        // Do not change the key "Adjust AdGroup". This key is being used in the Data Connector Processing Rule
        [adjustData setObject:@attribution.adgroup forKey:@"Adjust AdGroup"];
    if (attribution.creative != nil)
        // Do not change the key "Adjust Creative". This key is being used in the Data Connector Processing Rule
        [adjustData setObject:@attribution.creative forKey:@"Adjust Creative"];

    [ADBMobile trackAction:@"Adjust Campaign Data Received" data:adjustData];
}
```

Before you implement this interface, please take care to consider 
[possible conditions for usage of some of your data][attribution_data].

[attribution_data]: https://github.com/adjust/sdks/blob/master/doc/attribution-data.md
[response_callbacks]: https://github.com/adjust/ios_sdk#9-receive-delegate-callbacks
