# NSData-byte_operations
```
        // NSString -> NSData
        NSString  *str1 = @"a string";
        NSData *data1 = [str1 dataUsingEncoding:NSUTF8StringEncoding];
        
        // NSData－> NSString
        NSString *str2 = [[NSString alloc] initWithData:data1 encoding:NSUTF8StringEncoding];
        NSLog(@"str2 : %@",str2);
        
        // NSData －> Byte
        NSString *testString = @"1234567890";
        NSData *testData = [testString dataUsingEncoding: NSUTF8StringEncoding];
        Byte *testByte = (Byte *)[testData bytes];
        for(int i=0;i<[testData length];i++)
            printf("testByte = %d\n",testByte[i]);
        
        // Byte数组－> NSData
        Byte byte[] = {0xb1,0x01,0x32,0xff};
        
        NSUInteger byteLength = sizeof(byte);
        
        NSData *adata = [[NSData alloc] initWithBytes:byte length:byteLength];
        
        // Byte数组－>hexString
        Byte *bytes = (Byte *)[adata bytes];
        NSString *hexStr=@"";
        for(int i=0;i<[adata length];i++)
        {
            NSString *newHexStr = [NSString stringWithFormat:@"%x",bytes[i]&0xff]; //16进制数
            if([newHexStr length]==1)
                hexStr = [NSString stringWithFormat:@"%@0%@",hexStr,newHexStr];
            else
                hexStr = [NSString stringWithFormat:@"%@%@",hexStr,newHexStr];
        }
        NSLog(@"bytes 的16进制数为:%@",hexStr);
        
        // hexString -> Byte -> Data
        NSString *hexString = @"b324f0c5"; //16进制字符串
        
        NSData *hexStringToData = [utils hexStringToData:hexString];
        NSLog(@"data:%@",hexStringToData);
        
        // 判断byte指定位数
        if (byte[0] == 0xb1) {
            NSLog(@"right");
        }

```
