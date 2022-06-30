### `NSProgressIndicator` 颜色更改

```Objective-C
self.indicator = [[NSProgressIndicator alloc] initWithFrame:CGRectMake(100, 100, 120, 20)];
NSMutableArray<CIFilter *> *filters = [NSMutableArray array];
CIFilter *colorFilter = [CIFilter filterWithName:@"CIFalseColor"];
[colorFilter setDefaults];

NSColor *color1 = [NSColor colorWithRed:0 green:0 blue:1 alpha:1];
NSColor *color2 = [NSColor colorWithRed:0 green:1 blue:0 alpha:1];
// 进度颜色
[colorFilter setValue:[CIColor colorWithCGColor:color1.CGColor] forKey:@"inputColor0"];
// 未到达进度颜色
[colorFilter setValue:[CIColor colorWithCGColor:color2.CGColor] forKey:@"inputColor1"];
        
[filters addObject:colorFilter];
        
self.indicator.doubleValue = 80;

self.indicator.indeterminate = NO;
//设置 滤镜颜色
self.indicator.contentFilters = filters;
```