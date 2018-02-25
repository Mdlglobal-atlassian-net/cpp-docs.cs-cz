---
title: "packaged_task – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
dev_langs:
- C++
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::packaged_task [C++]
- std::packaged_task [C++], packaged_task
- std::packaged_task [C++], get_future
- std::packaged_task [C++], make_ready_at_thread_exit
- std::packaged_task [C++], reset
- std::packaged_task [C++], swap
- std::packaged_task [C++], valid
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce3db6f4685d8448efd88bf2203d541cc864abd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="packagedtask-class"></a>packaged_task – třída
Popisuje, *asynchronní zprostředkovatele* tedy obálku volání jejíž volání podpis je `Ty(ArgTypes...)`. Jeho *přidružené asynchronní stavu* obsahuje kopii svého s objektu kromě potenciální výsledek.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class>
class packaged_task;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[packaged_task](#packaged_task)|Vytvoří `packaged_task` objektu.|  
|[packaged_task::~packaged_task Destructor](#dtorpackaged_task_destructor)|Zničí `packaged_task` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get_future](#get_future)|Vrátí [budoucí](../standard-library/future-class.md) objekt, který má stejné přidružené asynchronní stavu.|  
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Volání s objekt, který je uložený v přidružený stav asynchronní a atomicky ukládá vrácené hodnoty.|  
|[reset](#reset)|Nahradí přidružený stav asynchronní.|  
|[swap](#swap)|Výměny přidružené asynchronní stavu se u zadaného objektu.|  
|[Platný](#valid)|Určuje, zda má objekt přidružený asynchronní stát.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[packaged_task::operator=](#op_eq)|Přenos přidružený asynchronní stát ze zadaného objektu.|  
|[packaged_task::operator()](#op_call)|Volání s objekt, který je uložený v přidružený stav asynchronní, atomicky ukládá vrácené hodnoty a nastaví stav *připraven*.|  
|[packaged_task::operator bool](#op_bool)|Určuje, zda má objekt přidružený asynchronní stát.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<budoucí >  
  
 **Namespace:** – std  
  
##  <a name="get_future"></a>  packaged_task::get_future –  
 Vrátí objekt typu `future<Ty>` má stejné *přidružené asynchronní stavu*.  
  
```
future<Ty> get_future();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `packaged_task` objekt nemá přidružený asynchronní stát, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) s kódem chyby `no_state`.  
  
 Pokud tato metoda již byla volána pro `packaged_task` objekt, který má stejné přidružené asynchronní stavu, vyvolá metoda `future_error` s kódem chyby `future_already_retrieved`.  
  
##  <a name="make_ready_at_thread_exit"></a>  packaged_task::make_ready_at_thread_exit –  
 Volání s objekt, který je uložen v *přidružené asynchronní stavu* a atomicky ukládá vrácené hodnoty.  
  
```
void make_ready_at_thread_exit(ArgTypes... args);
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `packaged_task` objekt nemá přidružený asynchronní stát, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) s kódem chyby `no_state`.  
  
 Pokud tato metoda nebo [make_ready_at_thread_exit](#make_ready_at_thread_exit) již byla volána pro `packaged_task` objekt, který má stejné přidružené asynchronní stavu, vyvolá metoda `future_error` s kódem chyby `promise_already_satisfied`.  
  
 Jinak zavolá tento operátor `INVOKE(fn, args..., Ty)`, kde *fn* je možné volat objekt, který je uložen v přidružený stav asynchronní. Všechny vrácená hodnota je uložena atomicky jako na vrácený výsledek přidružený stav asynchronní.  
  
 Rozdíl k [packaged_task:: Operator() –](#op_call), přidružené asynchronní stav není nastavený na `ready` až po všech místní objekty v volající vlákno zničena. Obvykle vláken, které blokují na přidružený stav asynchronní nejsou odblokuje, až do konce volající vlákno.  
  
##  <a name="op_eq"></a>  packaged_task::Operator =  
 Přenosy *přidružené asynchronní stavu* ze zadaného objektu.  
  
```
packaged_task& operator=(packaged_task&& Right);
```  
  
### <a name="parameters"></a>Parametry  
 `Right`  
 A `packaged_task` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `*this`  
  
### <a name="remarks"></a>Poznámky  
 Po operaci `Right` již nemá přidružený asynchronní stát.  
  
##  <a name="op_call"></a>  packaged_task:: Operator() –  
 Volání s objekt, který je uložen v *přidružené asynchronní stavu*, atomicky ukládá vrácené hodnoty a nastaví stav *připraven*.  
  
```
void operator()(ArgTypes... args);
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `packaged_task` objekt nemá přidružený asynchronní stát, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) s kódem chyby `no_state`.  
  
 Pokud tato metoda nebo [make_ready_at_thread_exit](#make_ready_at_thread_exit) již byla volána pro `packaged_task` objekt, který má stejné přidružené asynchronní stavu, vyvolá metoda `future_error` s kódem chyby `promise_already_satisfied`.  
  
 Jinak zavolá tento operátor `INVOKE(fn, args..., Ty)`, kde *fn* je možné volat objekt, který je uložen v přidružený stav asynchronní. Žádné vrácená hodnota je uložena atomicky jako na vrácený výsledek přidružený asynchronní stav a stav nastaven na hodnotu Připraveno. V důsledku toho žádné podprocesy, které blokují na přidružený stav asynchronní stát odblokování.  
  
##  <a name="op_bool"></a>  packaged_task::Operator bool  
 Určuje, zda je objekt `associated asynchronous state`.  
  
```
operator bool() const noexcept;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud objekt má přidružený stav asynchronní; v opačném `false`.  
  
##  <a name="packaged_task"></a>  packaged_task::packaged_task – konstruktor  
 Vytvoří `packaged_task` objektu.  
  
```
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```  
  
### <a name="parameters"></a>Parametry  
 `Right`  
 A `packaged_task` objektu.  
  
 `alloc`  
 Přidělení paměti. Další informace najdete v tématu [ \<alokátorů >](../standard-library/allocators-header.md).  
  
 `fn`  
 Objekt funkce.  
  
### <a name="remarks"></a>Poznámky  
 První konstrukce konstruktor `packaged_task` objekt, který neobsahuje žádné *přidružené asynchronní stavu*.  
  
 Druhý konstruktor konstrukce `packaged_task` objektu a přenáší přidružený stav asynchronní z `Right`. Po operaci `Right` již nemá přidružený asynchronní stát.  
  
 Třetí konstrukce konstruktor `packaged_task` objekt, který obsahuje kopie `fn` uložen v jeho přidružený stav asynchronní.  
  
 Čtvrtý konstrukce konstruktor `packaged_task` objekt, který obsahuje kopie `fn` uložen v jeho přidružený stav asynchronní a používá `alloc` pro přidělení paměti.  
  
##  <a name="dtorpackaged_task_destructor"></a>  packaged_task:: ~ packaged_task – destruktor  
 Zničí `packaged_task` objektu.  
  
```
~packaged_task();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud *přidružené asynchronní stavu* není *připraven*, destruktor úložiště [future_error](../standard-library/future-error-class.md) výjimka, která má chybový kód `broken_promise` jako výsledek v přidružený stav asynchronní a všechny vláken, která se v přidružené asynchronní stavu stát odblokuje blokuje.  
  
##  <a name="reset"></a>  packaged_task::Reset –  
 Používá nový *přidružené asynchronní stavu* nahradit stávající přidružené asynchronní stavu.  
  
```
void reset();
```  
  
### <a name="remarks"></a>Poznámky  
 V důsledku toho tato metoda provede `*this = packaged_task(move(fn))`, kde *fn* je objekt funkce, který je uložen v asynchronním přidružený stav pro tento objekt. Proto je zrušeno stav objektu, a [get_future](#get_future), [Operator() –](#op_call), a [make_ready_at_thread_exit](#make_ready_at_thread_exit) lze volat jako na nově vytvořený objekt.  
  
##  <a name="swap"></a>  packaged_task::swap –  
 Výměny přidružené asynchronní stavu se u zadaného objektu.  
  
```
void swap(packaged_task& Right) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Right`  
 A `packaged_task` objektu.  
  
##  <a name="valid"></a>  packaged_task::valid –  
 Určuje, zda je objekt `associated asynchronous state`.  
  
```
bool valid() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud objekt má přidružený stav asynchronní; v opačném `false`.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<budoucí >](../standard-library/future.md)



