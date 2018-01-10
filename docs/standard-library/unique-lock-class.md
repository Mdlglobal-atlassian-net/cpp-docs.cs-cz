---
title: "unique_lock – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: mutex/std::unique_lock
dev_langs: C++
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8974633a19e6f30f552eac4e5e7c3ec3b104c2ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="uniquelock-class"></a>unique_lock – třída
Reprezentuje šablonu, která se dá vytvořit instance k vytváření objektů, které spravují zamykání a odemykání `mutex`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Mutex>
class unique_lock;
```  
  
## <a name="remarks"></a>Poznámky  
 Argument šablony `Mutex` třeba zadat název *mutex typu*.  
  
 Interně `unique_lock` ukládá ukazatel na přiřazený `mutex` objektu a `bool` určující, zda vlastní aktuální vlákno `mutex`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`mutex_type`|Synonymum argumentu šablony `Mutex`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[unique_lock](#unique_lock)|Vytvoří `unique_lock` objektu.|  
|[~ unique_lock – destruktor](#dtorunique_lock_destructor)|Uvolní všechny prostředky, které jsou přidružené `unique_lock` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[lock](#lock)|Blokuje volající vlákno, dokud vlákno získá vlastnictví přidruženého `mutex`.|  
|[mutex](#mutex)|Načte uložené ukazatel s příslušnými `mutex`.|  
|[owns_lock](#owns_lock)|Určuje, zda vlastní volající vlákno přidruženého `mutex`.|  
|[verze](#release)|Zrušíte `unique_lock` objekt z přidruženého `mutex` objektu.|  
|[swap](#swap)|Prohození přidruženého `mutex` a stav vlastnictví se u zadaného objektu.|  
|[try_lock –](#try_lock)|Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.|  
|[try_lock_for –](#try_lock_for)|Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.|  
|[try_lock_until](#try_lock_until)|Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.|  
|[odemknutí](#unlock)|Uvolní vlastnictví přidruženého `mutex`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operátor bool](#op_bool)|Určuje, zda volající vlákno je vlastnictví přidruženého `mutex`.|  
|[operátor =](#op_eq)|Zkopíruje uložené `mutex` ukazatel a přidružené vlastnictví stav ze zadaného objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `unique_lock`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<mutex >  
  
 **Namespace:** – std  
  
##  <a name="lock"></a>Zámek  
 Blokuje volající vlákno, dokud vlákno získá vlastnictví přidruženého `mutex`.  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud uložená `mutex` ukazatel `null`, tato metoda vyvolá [system_error –](../standard-library/system-error-class.md) s kódem chyby `operation_not_permitted`.  
  
 Pokud volající vlákno již vlastní přidruženého `mutex`, tato metoda vyvolá `system_error` s kódem chyby `resource_deadlock_would_occur`.  
  
 Jinak tato metoda volá `lock` na přidruženého `mutex` a nastaví příznak vlastnictví interní vlákno `true`.  
  
##  <a name="mutex"></a>mutex  
 Načte uložené ukazatel s příslušnými `mutex`.  
  
```cpp  
mutex_type *mutex() const noexcept;
```  
  
##  <a name="op_bool"></a>operátor bool  
 Určuje, zda volající vlákno je související objekt mutex vlastnictví.  
  
```cpp  
explicit operator bool() noexcept
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud vlákno vlastní objekt mutex; v opačném případě `false`.  
  
##  <a name="op_eq"></a>operátor =  
 Zkopíruje uložené `mutex` ukazatel a přidružené vlastnictví stav ze zadaného objektu.  
  
```cpp  
unique_lock& operator=(unique_lock&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 A `unique_lock` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `*this`  
  
### <a name="remarks"></a>Poznámky  
 Pokud volající vlákno vlastní dříve přidružené `mutex`, než tato metoda volá `unlock` na `mutex`, přiřadí nové hodnoty.  
  
 Po kopírování, tato metoda nastaví `Other` sestavený výchozí stav.  
  
##  <a name="owns_lock"></a>owns_lock  
 Určuje, zda vlastní volající vlákno přidruženého `mutex`.  
  
```cpp  
bool owns_lock() const noexcept;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud vlastní vlákno `mutex`, jinak hodnota `false`.  
  
##  <a name="release"></a>verze  
 Zrušíte `unique_lock` objekt z přidruženého `mutex` objektu.  
  
```cpp  
mutex_type *release() noexcept;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí hodnotu uložené `mutex` ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví hodnotu uložené `mutex` ukazatel na 0 a nastaví interní `mutex` vlastnictví příznak, který `false`.  
  
##  <a name="swap"></a>swap  
 Prohození přidruženého `mutex` a stav vlastnictví se u zadaného objektu.  
  
```
void swap(unique_lock& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 A `unique_lock` objektu.  
  
##  <a name="try_lock"></a>try_lock –  
 Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.  
  
```cpp  
bool try_lock() noexcept;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud metoda úspěšně získá vlastnictví `mutex`, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud uložená `mutex` ukazatel `null`, vyvolá metoda [system_error –](../standard-library/system-error-class.md) s kódem chyby `operation_not_permitted`.  
  
 Pokud již vlastní volající vlákno `mutex`, vyvolá metoda `system_error` s kódem chyby `resource_deadlock_would_occur`.  
  
##  <a name="try_lock_for"></a>try_lock_for –  
 Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.  
  
```
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```  
  
### <a name="parameters"></a>Parametry  
 `Rel_time`  
 A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální množství času, která metoda se pokusí získat vlastnictví `mutex`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud metoda úspěšně získá vlastnictví `mutex`, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud uložená `mutex` ukazatel `null`, vyvolá metoda [system_error –](../standard-library/system-error-class.md) s kódem chyby `operation_not_permitted`.  
  
 Pokud již vlastní volající vlákno `mutex`, vyvolá metoda `system_error` s kódem chyby `resource_deadlock_would_occur`.  
  
##  <a name="try_lock_until"></a>try_lock_until  
 Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.  
  
```cpp  
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```  
  
### <a name="parameters"></a>Parametry  
 `Abs_time`  
 Bod v čase, který určuje mezní hodnotu, po jejímž uplynutí metodu již nebude pokoušet o získání vlastnictví `mutex`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud metoda úspěšně získá vlastnictví `mutex`, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud uložená `mutex` ukazatel `null`, vyvolá metoda [system_error –](../standard-library/system-error-class.md) s kódem chyby `operation_not_permitted`.  
  
 Pokud již vlastní volající vlákno `mutex`, vyvolá metoda `system_error` s kódem chyby `resource_deadlock_would_occur`.  
  
##  <a name="unique_lock"></a>unique_lock – konstruktor  
 Vytvoří `unique_lock` objektu.  
  
```cpp  
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>  
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>  
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Mtx`  
 Objekt mutex typu.  
  
 `Rel_time`  
 A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální množství času, která metoda se pokusí získat vlastnictví `mutex`.  
  
 `Abs_time`  
 Bod v čase, který určuje mezní hodnotu, po jejímž uplynutí metodu již nebude pokoušet o získání vlastnictví `mutex`.  
  
 `Other`  
 A `unique_lock` objektu.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktoru vytvoří objekt, který má přidružené mutex ukazatel hodnotu 0.  
  
 Druhý konstruktor přesune stav přidružené mutex z `Other`. Po přesunu `Other` je již přidružen mutex.  
  
 Zbývající úložiště konstruktory & `Mtx` jako uložené `mutex` ukazatel. Vlastnictví `mutex` je dáno druhý argument, pokud existuje.  
  
|||  
|-|-|  
|`No argument`|Vlastnictví se získá voláním `lock` metodu přidruženého `mutex` objektu.|  
|`Adopt`|Předpokládá se vlastnictví. `Mtx`je nutné uzamknout při volání konstruktoru.|  
|`Defer`|Volající vlákno je předpokládá, že není vlastní `mutex` objektu. `Mtx`nesmí být uzamčena při volání konstruktoru.|  
|`Try`|Vlastnictví je dáno volání `try_lock` na přidruženého `mutex` objektu. Konstruktor, vyvolá nic.|  
|`Rel_time`|Vlastnictví je dáno volání `try_lock_for(Rel_time)`.|  
|`Abs_time`|Vlastnictví je dáno volání `try_lock_until(Abs_time)`.|  
  
##  <a name="dtorunique_lock_destructor"></a>~ unique_lock – destruktor  
 Uvolní všechny prostředky, které jsou přidružené `unique_lock` objektu.  
  
```cpp  
~unique_lock() noexcept;
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud volající vlákno vlastní přidruženého `mutex`, vlastnictví verzích destruktor voláním odemknutí na `mutex` objektu.  
  
##  <a name="unlock"></a>odemknutí  
 Uvolní vlastnictví přidruženého `mutex`.  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud není vlastníkem volající vlákno přidruženého `mutex`, tato metoda vyvolá [system_error –](../standard-library/system-error-class.md) s kódem chyby `operation_not_permitted`.  
  
 Jinak tato metoda volá `unlock` na přidruženého `mutex` a nastaví příznak vlastnictví interní vlákno `false`.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex >](../standard-library/mutex.md)



