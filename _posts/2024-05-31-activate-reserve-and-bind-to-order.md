---
title: Метод ActivateReserve переименован в ActivateReserveAndBindToOrder и изменена его логика.
layout: default
---

Метод ActivateReserve переименован в [`ActivateReserveAndBindToOrder`](https://iiko.github.io/front.api.sdk/v9/html/M_Resto_Front_Api_Editors_IEditSession_ActivateReserveAndBindToOrder.htm) появилось свойство [`CurrencyInfo`](https://iiko.github.io/front.api.sdk/v9/html/P_Resto_Front_Api_Data_Payments_IPaymentItem_CurrencyInfo.htm).
Кроме того, была изменена логика метода. После активации резерва он связан с заказом, а заказ связан с резервом. Если количество гостей в заказе меньше, чем указано в резерве, то недостающее количество гостей добавляется в заказ.
