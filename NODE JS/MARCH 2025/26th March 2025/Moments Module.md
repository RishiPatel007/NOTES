```js
moment().format('MMMM Do YYYY, h:mm:ss a'); // March 27th 2025, 10:27:50 am
moment().format('dddd');                    // Thursday
moment().format("MMM Do YY");               // Mar 27th 25
moment().format('YYYY [escaped] YYYY');     // 2025 escaped 2025
moment().format();                          // 2025-03-27T10:27:50+05:30
```

```js
moment("20111031", "YYYYMMDD").fromNow(); // 13 years ago
moment("20120620", "YYYYMMDD").fromNow(); // 13 years ago
moment().startOf('day').fromNow();        // 10 hours ago
moment().endOf('day').fromNow();          // in 14 hours
moment().startOf('hour').fromNow();       // 29 minutes ago
```

```js
moment().subtract(10, 'days').calendar(); // 03/17/2025
moment().subtract(6, 'days').calendar();  // Last Friday at 10:29 AM
moment().subtract(3, 'days').calendar();  // Last Monday at 10:29 AM
moment().subtract(1, 'days').calendar();  // Yesterday at 10:29 AM
moment().calendar();                      // Today at 10:29 AM
moment().add(1, 'days').calendar();       // Tomorrow at 10:29 AM
moment().add(3, 'days').calendar();       // Sunday at 10:29 AM
moment().add(10, 'days').calendar();      // 04/06/2025
```

```js
moment.locale();         // en
moment().format('LT');   // 10:30 AM
moment().format('LTS');  // 10:30:42 AM
moment().format('L');    // 03/27/2025
moment().format('l');    // 3/27/2025
moment().format('LL');   // March 27, 2025
moment().format('ll');   // Mar 27, 2025
moment().format('LLL');  // March 27, 2025 10:30 AM
moment().format('lll');  // Mar 27, 2025 10:30 AM
moment().format('LLLL'); // Thursday, March 27, 2025 10:30 AM
moment().format('llll'); // Thu, Mar 27, 2025 10:30 AM
```

|                                | Token              | Output                                  |
| ------------------------------ | ------------------ | --------------------------------------- |
| **Month**                      | M                  | 1 2 ... 11 12                           |
|                                | Mo                 | 1st 2nd ... 11th 12th                   |
|                                | MM                 | 01 02 ... 11 12                         |
|                                | MMM                | Jan Feb ... Nov Dec                     |
|                                | MMMM               | January February ... November December  |
| **Quarter**                    | Q                  | 1 2 3 4                                 |
|                                | Qo                 | 1st 2nd 3rd 4th                         |
| **Day of Month**               | D                  | 1 2 ... 30 31                           |
|                                | Do                 | 1st 2nd ... 30th 31st                   |
|                                | DD                 | 01 02 ... 30 31                         |
| **Day of Year**                | DDD                | 1 2 ... 364 365                         |
|                                | DDDo               | 1st 2nd ... 364th 365th                 |
|                                | DDDD               | 001 002 ... 364 365                     |
| **Day of Week**                | d                  | 0 1 ... 5 6                             |
|                                | do                 | 0th 1st ... 5th 6th                     |
|                                | dd                 | Su Mo ... Fr Sa                         |
|                                | ddd                | Sun Mon ... Fri Sat                     |
|                                | dddd               | Sunday Monday ... Friday Saturday       |
| **Day of Week (Locale)**       | e                  | 0 1 ... 5 6                             |
| **Day of Week (ISO)**          | E                  | 1 2 ... 6 7                             |
| **Week of Year**               | w                  | 1 2 ... 52 53                           |
|                                | wo                 | 1st 2nd ... 52nd 53rd                   |
|                                | ww                 | 01 02 ... 52 53                         |
| **Week of Year (ISO)**         | W                  | 1 2 ... 52 53                           |
|                                | Wo                 | 1st 2nd ... 52nd 53rd                   |
|                                | WW                 | 01 02 ... 52 53                         |
| **Year**                       | YY                 | 70 71 ... 29 30                         |
|                                | YYYY               | 1970 1971 ... 2029 2030                 |
|                                | YYYYYY             | -001970 -001971 ... +001907 +001971     |
|                                | Y                  | 1970 1971 ... 9999 +10000 +10001        |
| **Era Year**                   | y                  | 1 2 ... 2020 ...                        |
| **Era**                        | N, NN, NNN         | BC AD                                   |
|                                | NNNN               | Before Christ, Anno Domini              |
|                                | NNNNN              | BC AD                                   |
| **Week Year**                  | gg                 | 70 71 ... 29 30                         |
|                                | gggg               | 1970 1971 ... 2029 2030                 |
| **Week Year (ISO)**            | GG                 | 70 71 ... 29 30                         |
|                                | GGGG               | 1970 1971 ... 2029 2030                 |
| **AM/PM**                      | A                  | AM PM                                   |
|                                | a                  | am pm                                   |
| **Hour**                       | H                  | 0 1 ... 22 23                           |
|                                | HH                 | 00 01 ... 22 23                         |
|                                | h                  | 1 2 ... 11 12                           |
|                                | hh                 | 01 02 ... 11 12                         |
|                                | k                  | 1 2 ... 23 24                           |
|                                | kk                 | 01 02 ... 23 24                         |
| **Minute**                     | m                  | 0 1 ... 58 59                           |
|                                | mm                 | 00 01 ... 58 59                         |
| **Second**                     | s                  | 0 1 ... 58 59                           |
|                                | ss                 | 00 01 ... 58 59                         |
| **Fractional Second**          | S                  | 0 1 ... 8 9                             |
|                                | SS                 | 00 01 ... 98 99                         |
|                                | SSS                | 000 001 ... 998 999                     |
|                                | SSSS ... SSSSSSSSS | 000[0..] 001[0..] ... 998[0..] 999[0..] |
| **Time Zone**                  | z or zz            | EST CST ... MST PST                     |
|                                | Z                  | -07:00 -06:00 ... +06:00 +07:00         |
|                                | ZZ                 | -0700 -0600 ... +0600 +0700             |
| **Unix Timestamp**             | X                  | 1360013296                              |
| **Unix Millisecond Timestamp** | x                  | 1360013296123                           |


