# swiftSwisseph
 a way to access swisseph the swiss ephemeris in swift.  
 
 compile Framework, then include into your project.  
 interact in swift using c data type.  
 
 make sure you satisfy AstroDienst's licensing agenda.  
 
 ```swift
 import swiftSwisseph
 ```

```swift
    deinit {
        // perform the deinitialization
        self.swissephClose()
    }
```

```swift
        var theYear:NSNumber
        var theMonth:NSNumber
        var theDay:NSNumber
        
        var theHour:NSNumber
        var theMin:NSNumber
        var theSec:NSNumber
        
        let now = Date()
        let formatterYear = DateFormatter()
        formatterYear.timeZone = TimeZone.current
        formatterYear.dateFormat = "yyyy"
        let formatterMonth = DateFormatter()
        formatterMonth.timeZone = TimeZone.current
        formatterMonth.dateFormat = "MM"
        let formatterDay = DateFormatter()
        formatterDay.timeZone = TimeZone.current
        formatterDay.dateFormat = "dd"
        
        let formatterHour = DateFormatter()
        formatterHour.timeZone = TimeZone.current
        formatterHour.dateFormat = "HH"
        let formatterMin = DateFormatter()
        formatterMin.timeZone = TimeZone.current
        formatterMin.dateFormat = "mm"
        let formatterSec = DateFormatter()
        formatterSec.timeZone = TimeZone.current
        formatterSec.dateFormat = "ss"
        
        let dateYearString = formatterYear.string(from: now)
        let myYear = Int(dateYearString)
        theYear = NSNumber(value:myYear!)
        let dateMonthString = formatterMonth.string(from: now)
        let myMonth = Int(dateMonthString)
        theMonth = NSNumber(value:myMonth!)
        let dateDayString = formatterDay.string(from: now)
        let myDay = Int(dateDayString)
        theDay = NSNumber(value:myDay!)
        
        let dateHourString = formatterHour.string(from: now)
        let myHour = Int(dateHourString)
        theHour = NSNumber(value:myHour!)
        
        let dateMinString = formatterMin.string(from: now)
        let myMin = Int(dateMinString)
        theMin = NSNumber(value:myMin!)
        
        let dateSecString = formatterSec.string(from: now)
        let mySec = Int(dateSecString)
        theSec = NSNumber(value:mySec!)
        
        //decimal time
        let dh:Double = theHour.doubleValue
        let dm:Double = theMin.doubleValue / 60.0
        let ds:Double = theSec.doubleValue / 3600.0
        
        let decimalTime:Double = dh + dm + ds
        
        //asign to global/public vars
        overallDecimalTime = decimalTime
        overallTheDay = formatterDay
        overallTheMonth = formatterMonth
        overallTheYear = formatterYear
        overallNow = now
        
        let theDecimalHour:NSNumber = NSNumber(value: decimalTime)
        
        //let theHour = 0.0
        //gregflag uses constant SE_GREG_CAL
        print("theYear: \(theYear), theMonth: \(theMonth), theDay: \(theDay), theDecimalHour: \(theDecimalHour)")   //print the NSNumber's
        
        //have to recast the vars
        tjd_ut = swe_julday((theYear as! Int32), (theMonth as! Int32), (theDay as! Int32), (theDecimalHour as! Double), SE_GREG_CAL)   //set tjd_ut = a "Julian" date. SE_GREG_CAL determines its a Gregorian Calendar instead. Have to cast to C data-types. (theYear as! Int32)
```
