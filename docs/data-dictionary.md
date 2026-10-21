# Data Dictionary

Source: *Hotel Booking Demand* dataset (Antonio, Almeida & Nunes, 2019). One row = one booking. Table name in the Power BI model: `Hotel Bookings`.

Fields used in the dashboard:

| Column | Type | Description |
|--------|------|-------------|
| `hotel` | Text | `City Hotel` or `Resort Hotel` |
| `is_canceled` | 0 / 1 | 1 if the booking was cancelled |
| `arrival_date_month` | Text | Month of arrival (January–December) |
| `stays_in_week_nights` | Integer | Nights stayed (or booked) Monday–Friday |
| `stays_in_weekend_nights` | Integer | Nights stayed (or booked) Saturday–Sunday |
| `country` | Text | Guest country of origin (ISO 3166-1 alpha-3, e.g. `PRT`, `GBR`) |
| `market_segment` | Text | Booking channel segment: `Online TA`, `Offline TA/TO`, `Groups`, `Direct`, `Corporate`, `Complementary`, `Aviation` |
| `is_repeated_guest` | 0 / 1 | 1 if the guest had stayed before |
| `previous_bookings_not_canceled` | Integer | Guest's earlier bookings that were not cancelled |
| `assigned_room_type` | Text | Room type code assigned to the booking (A, B, C, D, …) — codes are anonymised |

Other columns in the dataset (not used in this dashboard) include `lead_time`, `adr` (average daily rate), `deposit_type`, `customer_type`, `adults`, `children`, `babies` and `reservation_status`.
