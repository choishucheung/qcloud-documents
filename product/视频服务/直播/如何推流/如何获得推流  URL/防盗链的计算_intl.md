The security hotlink protection refers to the txSecret field in push and playback URLs. It is used to prevent attackers from simulating your backend server to generate push URL or hacking your playback URL for their benefits.

### How it works
To prevent attackers from simulating your server to generate push URL, you need to configure in LVB console a hotlink protection encryption key that is unlikely to be obtained by attackers for faking a valid push URL. The figure below shows how it works.
![](//mccdn.qcloud.com/static/img/4ea1512fd335f68f30cca0a01e902966/image.png)

### Computing procedure
- **Step 1: Exchange the key**
You need to negotiate an encryption key on the console at the official website. This encryption key is used to generate a hotlink protection signature on your server. Since Tencent Cloud has the same key as yours, it can decrypt and verify the hotlink protection signature generated by your server.

 The encryption keys include push hotlink protection key and playback hotlink protection key. The former is used to generate the push hotlink protection URL and the latter is to generate the playback hotlink protection URL. On the [LVB Console](https://console.cloud.tencent.com/live), you can configure the push hotlink protection key, as shown below:
![](//mc.qcloudimg.com/static/img/b3b4641c0af4f9f5c17921cfe8320a01/image.png)
 >  **Playback hotlink protection is disabled by default:**   
 > Since the configuration of playback hotlink protection key needs to be synchronized to thousands of CDN clusters, the key cannot be frequently modified in the debugging phase due to a long synchronization period. Contact us if you need to configure the playback hotlink protection. It generally takes 1 to 3 days to complete the synchronization for all the clusters.

- **Step 2: Generate txTime**
The plaintext in the signature is txTime, which indicates the validity period of URL. For example, if the current time is 2016-07-29 11:13:45 and the generated URL is expected to expire after 24 hours, then set txTime to 2016-07-30 11:13:45.

 Such a long time string would occupy too much space in the URL. In actual scenario, 2016-07-30 11:13:45 is converted into a UNIX timestamp, i.e. 1469848425 (various backend programming languages are directly handled by available time functions during the conversion). Then, the timestamp is converted into a hexadecimal string to further reduce the string length, that is, txTime = 1469848425 (hexadecimal) = 579C1B69 (hexadecimal).
 
 Generally, txTime is set to a time which is 24 hours later than the current time. It is not recommended to set a too short validity period to avoid the inability of VJ to restore push in case of a flash breakdown of network during the broadcasting.

- **Step 3: Generate txSecret**
txSecret is generated as follows: txSecret = MD5 (KEY+stream_id+txTime), where the KEY is the encryption key you configured in Step 1. In this example, stream_id is 8888_test001, txTime is 579C1B69 as calculated above, and MD5 is the standard unidirectional irreversible hash algorithm.

- **Step 4: Construct the hotlink protection URL**
  Combine the push (or playback) URL, the txTime indicating expiration time of URL and the txSecret that can be decrypted and verified only by Tencent Cloud to generate a secure hotlink protection URL.
	
### Sample Code
Go to [LVB Console](https://console.cloud.tencent.com/), select **LVB Code Access (Recommended)** -> [**Push Generator**](https://console.cloud.tencent.com/live/livecodemanage). In the lower part of the page, **Push URL Sample Code** (PHP and Java) is provided to show how to generate a hotlink protection URL.

