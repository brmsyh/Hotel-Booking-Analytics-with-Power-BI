# DAX Measures

All measures live in the `Hotel Bookings` table.

## Used in the dashboard

```dax
Cancellation Count =
CALCULATE ( COUNTROWS ( 'Hotel Bookings' ), 'Hotel Bookings'[is_canceled] = 1 )

Repeated Guests =
SUM ( 'Hotel Bookings'[is_repeated_guest] )

Week Nights =
SUM ( 'Hotel Bookings'[stays_in_week_nights] )

Weekend Nights =
SUM ( 'Hotel Bookings'[stays_in_weekend_nights] )
```

## Supporting measures

```dax
Total Bookings =
COUNTROWS ( 'Hotel Bookings' )

Cancellation Rate =
DIVIDE ( [Cancellation Count], [Total Bookings] )        -- format as %

Repeat Guest Rate =
DIVIDE ( [Repeated Guests], [Total Bookings] )           -- format as %

Booking Share =
DIVIDE (
    [Total Bookings],
    CALCULATE ( [Total Bookings], ALLSELECTED ( 'Hotel Bookings' ) )
)
```

## Calculated column — month order

`arrival_date_month` is text, so it sorts alphabetically by default. Add this column and use **Column tools → Sort by column → Month Number** on `arrival_date_month` so line charts run January → December.

```dax
Month Number =
SWITCH (
    'Hotel Bookings'[arrival_date_month],
    "January", 1,  "February", 2,  "March", 3,     "April", 4,
    "May", 5,      "June", 6,      "July", 7,      "August", 8,
    "September", 9, "October", 10, "November", 11, "December", 12
)
```
