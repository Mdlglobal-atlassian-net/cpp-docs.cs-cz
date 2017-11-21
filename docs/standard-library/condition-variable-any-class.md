---
title: "condition_variable_any – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- condition_variable/std::condition_variable_any
- condition_variable/std::condition_variable_any::condition_variable_any
- condition_variable/std::condition_variable_any::notify_all
- condition_variable/std::condition_variable_any::notify_one
- condition_variable/std::condition_variable_any::wait
- condition_variable/std::condition_variable_any::wait_for
- condition_variable/std::condition_variable_any::wait_until
dev_langs: C++
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::condition_variable_any
- std::condition_variable_any::condition_variable_any
- std::condition_variable_any::notify_all
- std::condition_variable_any::notify_one
- std::condition_variable_any::wait
- std::condition_variable_any::wait_for
- std::condition_variable_any::wait_until
ms.openlocfilehash: 2f15319ec5d35ef5bc6ebdf047f1ea0a963510e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="conditionvariableany-class"></a>condition_variable_any – třída
Použití třídy `condition_variable_any` čekání na událost, která obsahuje některý `mutex` typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class condition_variable_any;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[condition_variable_any](#condition_variable_any)|Vytvoří `condition_variable_any` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[notify_all](#notify_all)|Odblokuje všechna vlákna, která čekají `condition_variable_any` objektu.|  
|[notify_one](#notify_one)|Odblokuje jeden vláken, která čekají `condition_variable_any` objektu.|  
|[Počkej](#wait)|Blokuje vlákno.|  
|[wait_for](#wait_for)|Blokuje vlákno a nastaví časový interval, po jejímž uplynutí odblokuje vlákno.|  
|[wait_until](#wait_until)|Blokuje vlákno a nastaví maximální bodu v čase, kdy odblokuje vlákno.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<condition_variable >  
  
 **Namespace:** – std  
  
##  <a name="condition_variable_any"></a>condition_variable_any::condition_variable_any – konstruktor  
 Vytvoří `condition_variable_any` objektu.  
  
```
condition_variable_any();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je k dispozici není dostatek paměti, vyvolá konstruktoru [system_error –](../standard-library/system-error-class.md) objekt, který má `not_enough_memory` kód chyby. Pokud objekt nelze vytvořit, protože jiný prostředek není k dispozici, vyvolá konstruktoru `system_error` objekt, který má `resource_unavailable_try_again` kód chyby.  
  
##  <a name="notify_all"></a>condition_variable_any::notify_all –  
 Odblokuje všechna vlákna, která čekají `condition_variable_any` objektu.  
  
```
void notify_all() noexcept;
```  
  
##  <a name="notify_one"></a>condition_variable_any::notify_one –  
 Jeden z vláken, která čekají na odblokuje `condition_variable_any` objektu.  
  
```
void notify_one() noexcept;
```  
  
##  <a name="wait"></a>condition_variable_any::wait –  
 Blokuje vlákno.  
  
```
template <class Lock>  
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```  
  
### <a name="parameters"></a>Parametry  
 `Lck`  
 A `mutex` objektu libovolného typu.  
  
 `Pred`  
 Jakýkoli výraz, který vrací `true` nebo `false`.  
  
### <a name="remarks"></a>Poznámky  
 První metoda blokuje až `condition_variable_any` objekt signalizace voláním [notify_one](../standard-library/condition-variable-class.md#notify_one) nebo [notify_all](../standard-library/condition-variable-class.md#notify_all). Ho můžete také probuzení spuriously.  
  
 Druhá metoda spustí platí následující kód.  
  
```
while (!Pred())
    wait(Lck);
```    
  
##  <a name="wait_for"></a>condition_variable_any::wait_for –  
 Blokuje vlákno a nastaví časový interval, po jejímž uplynutí odblokuje vlákno.  
  
```
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```  
  
### <a name="parameters"></a>Parametry  
 `Lck`  
 A `mutex` objektu libovolného typu.  
  
 `Rel_time`  
 A `chrono::duration` probudí objekt, který určuje množství času, než vlákno.  
  
 `Pred`  
 Jakýkoli výraz, který vrací `true` nebo `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první metoda `cv_status::timeout` Pokud ukončí dobu, kdy `Rel_time` uplynul. Jinak, vrátí metoda `cv_status::no_timeout`.  
  
 Druhá metoda vrátí hodnotu `Pred`.  
  
### <a name="remarks"></a>Poznámky  
 První metoda blokuje až `condition_variable_any` objekt signalizace voláním [notify_one](../standard-library/condition-variable-class.md#notify_one) nebo [notify_all](../standard-library/condition-variable-class.md#notify_all), nebo dokud se časový interval `Rel_time` uplynul. Ho můžete také probuzení spuriously.  
  
 Druhá metoda spustí platí následující kód.  
  
```cpp  
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```  
  
##  <a name="wait_until"></a>condition_variable_any::wait_until –  
 Blokuje vlákno a nastaví maximální bodu v čase, kdy odblokuje vlákno.  
  
```
template <class Lock, class Clock, class Duration>
void wait_until(Lock& Lck, const chrono::time_point<Clock, Duration>& Abs_time);

template <class Lock, class Clock, class Duration, class Predicate>
void wait_until(
    Lock& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

template <class Lock>
void wait_until(Lock Lck, const xtime* Abs_time);

template <class Lock, class Predicate>
void wait_until(
    Lock Lck,
    const xtime* Abs_time,
    Predicate Pred);
```  
  
### <a name="parameters"></a>Parametry  
 `Lck`  
 Objekt mutex.  
  
 `Abs_time`  
 A [chrono::time_point](../standard-library/time-point-class.md) objektu.  
  
 `Pred`  
 Jakýkoli výraz, který vrací `true` nebo `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Metody, které vracejí `cv_status` návratový typ `cv_status::timeout` Pokud ukončí dobu, kdy `Abs_time` uplynutí. Jinak vrátí metody `cv_status::no_timeout`.  
  
 Metody, které vracejí `bool` vrátí hodnotu `Pred`.  
  
### <a name="remarks"></a>Poznámky  
 První metoda blokuje až `condition_variable` objekt signalizace voláním [notify_one](../standard-library/condition-variable-class.md#notify_one) nebo [notify_all](../standard-library/condition-variable-class.md#notify_all), nebo dokud `Abs_time`. Ho můžete také probuzení spuriously.  
  
 Druhá metoda spustí platí následující kód.  
  
```
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```  
  
 Metody třetí a čtvrtý použití ukazatel na objekt typu `xtime` nahradit `chrono::time_point` objektu. `xtime` Objektu určuje maximální množství času čekání na signál.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [< condition_variable >](../standard-library/condition-variable.md)



