# Diccionario de Datos

## Caso 1 — Hotel Booking Demand

### Variables originales

| Variable | Tipo semántico | Dtype | Descripción | Valores posibles / Rango |
|---|---|---|---|---|
| `hotel` | Categórica nominal | object | Tipo de hotel | Resort Hotel, City Hotel |
| `is_canceled` | Binaria — variable objetivo | int64 | Indica si la reserva fue cancelada | 0 = No, 1 = Sí |
| `lead_time` | Numérica discreta | int64 | Días entre la reserva y la llegada | 0 – 737 |
| `arrival_date_year` | Categórica ordinal | int64 | Año de llegada | 2015, 2016, 2017 |
| `arrival_date_month` | Categórica ordinal | object | Mes de llegada en texto | January … December |
| `arrival_date_week_number` | Numérica discreta | int64 | Número de semana ISO de llegada | 1 – 53 |
| `arrival_date_day_of_month` | Numérica discreta | int64 | Día del mes de llegada | 1 – 31 |
| `stays_in_weekend_nights` | Numérica discreta | int64 | Noches de fin de semana de la estancia | 0 – 19 |
| `stays_in_week_nights` | Numérica discreta | int64 | Noches entre semana de la estancia | 0 – 50 |
| `adults` | Numérica discreta | int64 | Número de adultos en la reserva | 0 – 55 |
| `children` | Numérica discreta | float64 | Número de niños en la reserva | 0 – 10 |
| `babies` | Numérica discreta | int64 | Número de bebés en la reserva | 0 – 10 |
| `meal` | Categórica nominal | object | Tipo de régimen alimenticio | BB, HB, FB, SC, Undefined |
| `country` | Categórica nominal | object | País de origen del cliente | ~178 países (ISO 3166) |
| `market_segment` | Categórica nominal | object | Segmento de mercado | Direct, Corporate, Online TA, Offline TA/TO, Groups, Complementary, Aviation |
| `distribution_channel` | Categórica nominal | object | Canal de distribución | Direct, Corporate, TA/TO, GDS, Undefined |
| `is_repeated_guest` | Binaria | int64 | Indica si el cliente es recurrente | 0 = No, 1 = Sí |
| `previous_cancellations` | Numérica discreta | int64 | Cancelaciones previas del cliente | 0 – 26 |
| `previous_bookings_not_canceled` | Numérica discreta | int64 | Reservas previas no canceladas | 0 – 72 |
| `reserved_room_type` | Categórica nominal | object | Tipo de habitación reservada | A – P |
| `assigned_room_type` | Categórica nominal | object | Tipo de habitación asignada al check-in | A – P |
| `booking_changes` | Numérica discreta | int64 | Número de cambios realizados a la reserva | 0 – 21 |
| `deposit_type` | Categórica nominal | object | Tipo de depósito realizado | No Deposit, Non Refund, Refundable |
| `agent` | Identificador numérico | float64 | ID de la agencia de viajes | Numérico / NaN |
| `company` | Identificador numérico | float64 | ID de la empresa asociada | Numérico / NaN |
| `days_in_waiting_list` | Numérica discreta | int64 | Días en lista de espera antes de confirmación | 0 – 391 |
| `customer_type` | Categórica nominal | object | Tipo de cliente | Transient, Transient-Party, Contract, Group |
| `adr` | Numérica continua | float64 | Tarifa diaria promedio en euros | 0 – 5400 |
| `required_car_parking_spaces` | Numérica discreta | int64 | Espacios de aparcamiento solicitados | 0 – 8 |
| `total_of_special_requests` | Numérica discreta | int64 | Número de solicitudes especiales | 0 – 5 |
| `reservation_status` | Categórica nominal | object | Estado final de la reserva | Canceled, Check-Out, No-Show |
| `reservation_status_date` | Fecha | object | Fecha en que se registró el estado final | Fecha ISO |

### Variables derivadas

| Variable | Tipo | Descripción | Fórmula / Origen |
|---|---|---|---|
| `arrival_date` | Fecha | Fecha de llegada unificada | `arrival_date_year` + `arrival_date_month` + `arrival_date_day_of_month` |
| `arrival_month_num` | Numérica discreta | Mes de llegada en formato numérico | `arrival_date.dt.month` |
| `arrival_quarter` | Numérica discreta | Trimestre de llegada | `arrival_date.dt.quarter` |
| `arrival_dayofweek` | Numérica discreta | Día de la semana de llegada | `arrival_date.dt.dayofweek` |
| `total_nights` | Numérica discreta | Total de noches de la estancia | `stays_in_weekend_nights + stays_in_week_nights` |
| `ingreso_estimado` | Numérica continua | Ingreso estimado por reserva en euros | `adr * total_nights` |
| `is_complimentary` | Binaria | Indica si la reserva tiene tarifa cero | `adr == 0 → 1, else 0` |
| `has_agent` | Binaria | Indica si la reserva fue gestionada por agencia | `agent notna() → 1, else 0` |
| `has_company` | Binaria | Indica si la reserva está asociada a una empresa | `company notna() → 1, else 0` |
| `periodo` | Categórica ordinal | Año y mes de llegada en formato texto | `arrival_date.dt.to_period("M")` |

---

## Caso 2 — Telco Customer Churn

### Variables originales

| Variable | Tipo semántico | Dtype original | Dtype final | Descripción | Valores posibles |
|---|---|---|---|---|---|
| `customerID` | Identificador | object | — | Identificador único del cliente | String alfanumérico |
| `gender` | Categórica binaria | object | object | Género del cliente | Male, Female |
| `SeniorCitizen` | Categórica binaria | int64 | object | Indica si el cliente es adulto mayor | 0, 1 → No, Yes |
| `Partner` | Categórica binaria | object | object | Indica si el cliente tiene pareja | Yes, No |
| `Dependents` | Categórica binaria | object | object | Indica si el cliente tiene dependientes | Yes, No |
| `tenure` | Numérica discreta | int64 | int64 | Meses como cliente de la compañía | 0 – 72 |
| `PhoneService` | Categórica binaria | object | object | Indica si tiene servicio telefónico | Yes, No |
| `MultipleLines` | Categórica nominal | object | object | Indica si tiene múltiples líneas | Yes, No |
| `InternetService` | Categórica nominal | object | object | Tipo de servicio de internet | DSL, Fiber optic, No |
| `OnlineSecurity` | Categórica binaria | object | object | Indica si tiene seguridad online contratada | Yes, No |
| `OnlineBackup` | Categórica binaria | object | object | Indica si tiene backup online contratado | Yes, No |
| `DeviceProtection` | Categórica binaria | object | object | Indica si tiene protección de dispositivos | Yes, No |
| `TechSupport` | Categórica binaria | object | object | Indica si tiene soporte técnico contratado | Yes, No |
| `StreamingTV` | Categórica binaria | object | object | Indica si tiene streaming de TV contratado | Yes, No |
| `StreamingMovies` | Categórica binaria | object | object | Indica si tiene streaming de películas contratado | Yes, No |
| `Contract` | Categórica ordinal | object | object | Tipo de contrato del cliente | Month-to-month, One year, Two year |
| `PaperlessBilling` | Categórica binaria | object | object | Indica si usa facturación sin papel | Yes, No |
| `PaymentMethod` | Categórica nominal | object | object | Método de pago | Electronic check, Mailed check, Bank transfer, Credit card |
| `MonthlyCharges` | Numérica continua | float64 | float64 | Cargo mensual en dólares | 18.25 – 118.75 |
| `TotalCharges` | Numérica continua | object | float64 | Cargo total acumulado en dólares | 0 – 8684.8 |
| `Churn` | Binaria — variable objetivo | object | int64 | Indica si el cliente canceló el servicio | Yes → 1, No → 0 |

### Variables derivadas

| Variable | Tipo | Descripción | Fórmula / Origen |
|---|---|---|---|
| `n_servicios_adicionales` | Numérica discreta | Número de servicios adicionales contratados | Suma de Yes en: OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies, MultipleLines |
| `cargo_por_servicio` | Numérica continua | Cargo mensual relativo al número de productos contratados | `MonthlyCharges / n_productos.clip(lower=1)` |
| `tenure_group` | Categórica ordinal | Segmento de permanencia del cliente | Bins sobre `tenure`: 0–12m, 13–24m, 25–48m, 49–72m |
| `is_high_value` | Binaria | Indica si el cliente está por encima del percentil 75 en cargo mensual | `MonthlyCharges > p75 → 1, else 0` |
| `n_productos` | Numérica discreta | Total de productos contratados incluyendo servicios base | `n_servicios_adicionales + PhoneService activo + InternetService activo` |
