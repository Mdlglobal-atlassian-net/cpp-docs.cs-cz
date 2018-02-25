---
title: "Future – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
dev_langs:
- C++
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: f54b265e98d8375b20ca5b7cf484290083d1d59c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="future-class"></a>future – třída
Popisuje, *asynchronní návratové objekt*.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Ty>
class future;
```  
  
## <a name="remarks"></a>Poznámky  
 Každé standardní *asynchronní zprostředkovatele* vrátí objekt, jehož typ je vytváření instancí této šablony. A `future` objekt poskytuje jenom přístup k poskytovateli asynchronní, který je přidružen. Pokud potřebujete více asynchronní návratové objekty, které jsou spojeny s stejného asynchronní poskytovatele, zkopírujte `future` do objektu [shared_future](../standard-library/shared-future-class.md) objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Budoucí](#future)|Vytvoří `future` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get](#get)|Načte výsledek, který je uložen v přidružený stav asynchronní.|  
|[share](#share)|Převede objekt, který má `shared_future`.|  
|[Platný](#valid)|Určuje, zda objekt není prázdný.|  
|[wait](#wait)|Aktuální vlákno zablokuje, dokud přidružený stav asynchronní je připraven.|  
|[wait_for](#wait_for)|Bloky dokud přidružený stav asynchronní je připraven nebo dokud určený čas uplynul.|  
|[wait_until](#wait_until)|Bloky dokud přidružený stav asynchronní je připravená, nebo dokud se zadaný bod v čase.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[future::operator=](#op_eq)|Přenos přidružený stav asynchronní ze zadaného objektu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<budoucí >  
  
 **Namespace:** – std  
  
##  <a name="future"></a>  Future::Future – konstruktor  
 Vytvoří `future` objektu.  
  
```
future() noexcept;
future(future&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 A `future` objektu.  
  
### <a name="remarks"></a>Poznámky  
 První konstrukce konstruktor `future` objekt, který nemá žádné přidružené asynchronní stavu.  
  
 Druhý konstruktor konstrukce `future` objektu a přenáší přidružený stav asynchronní z `Other`. `Other` již nemá přidružený asynchronní stát.  
  
##  <a name="get"></a>  Future::Get –  
 Načte výsledek, který je uložen v přidružený stav asynchronní.  
  
```
Ty get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je výsledek výjimku, znovu vyvolá metodu ho. Jinak se vrátí výsledek.  
  
### <a name="remarks"></a>Poznámky  
 Předtím, než se načte výsledek, tato metoda blokuje aktuální vlákno, dokud přidružený stav asynchronní je připraven.  
  
 Pro částečná specializace `future<Ty&>`, uložené hodnoty je efektivně odkaz na objekt, který byl předán asynchronní zprostředkovatele jako návratovou hodnotu.  
  
 Vzhledem k tomu, že neexistuje žádná hodnota uložené pro specializace `future<void>`, vrátí metoda `void`.  
  
 V dalších specializací metodu přesune hodnoty z uložené hodnoty. Tato metoda proto volejte pouze jednou.  
  
##  <a name="op_eq"></a>  Future::Operator =  
 Přenos přidružený asynchronní stát ze zadaného objektu.  
  
```
future& operator=(future&& Right) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Right`  
 A `future` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `*this`  
  
### <a name="remarks"></a>Poznámky  
 Po předání `Right` již nemá přidružený asynchronní stát.  
  
##  <a name="share"></a>  Future::share –  
 Převede objekt, který má [shared_future](../standard-library/shared-future-class.md) objektu.  
  
```
shared_future<Ty> share();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `shared_future(move(*this))`  
  
##  <a name="valid"></a>  Future::valid –  
 Určuje, zda má objekt přidružený asynchronní stát.  
  
```
bool valid() noexcept;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud objekt má přidružený stav asynchronní; v opačném `false`.  
  
##  <a name="wait"></a>  Future::wait –  
 Blokuje aktuální vlákno, dokud je přidružený stav asynchronní *připraven*.  
  
```cpp  
void wait() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Je k dispozici přidružený stav asynchronní *připraven* jenom v případě jeho asynchronní zprostředkovatelem má uložené návratovou hodnotu nebo uložené výjimku.  
  
##  <a name="wait_for"></a>  Future::wait_for –  
 Blokuje aktuální vlákno, dokud je přidružený stav asynchronní *připraven* nebo dokud neuplyne zadaného časového intervalu.  
  
```
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```  
  
### <a name="parameters"></a>Parametry  
 `Rel_time`  
 A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální časový interval, která blokuje přístup z více vláken.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [future_status](../standard-library/future-enums.md#future_status) určující důvod pro vrácení.  
  
### <a name="remarks"></a>Poznámky  
 Přidružený asynchronní stát je připraven jenom v případě jeho asynchronní zprostředkovatelem má uložené návratovou hodnotu nebo uložené výjimku.  
  
##  <a name="wait_until"></a>  Future::wait_until –  
 Blokuje aktuální vlákno, dokud je přidružený stav asynchronní *připraven* nebo dokud nebude po zadaném časovém bodě.  
  
```cpp  
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```  
  
### <a name="parameters"></a>Parametry  
 `Abs_time`  
 A [chrono::time_point](../standard-library/time-point-class.md) objekt, který určuje dobu, po jejímž uplynutí vlákno odblokovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [future_status](../standard-library/future-enums.md#future_status) určující důvod pro vrácení.  
  
### <a name="remarks"></a>Poznámky  
 Je k dispozici přidružený stav asynchronní *připraven* jenom v případě jeho asynchronní zprostředkovatelem má uložené návratovou hodnotu nebo uložené výjimku.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<budoucí >](../standard-library/future.md)



