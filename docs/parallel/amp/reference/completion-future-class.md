---
title: "completion_future – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
dev_langs: C++
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07e41d6bf03df1231249a9e2ea5e54e420c9840c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="completionfuture-class"></a>completion_future – třída
Představuje budoucí odpovídající C++ AMP asynchronní operaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
class completion_future;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[completion_future – konstruktor](#ctor)|Inicializuje novou instanci třídy `completion_future` třídy.|  
|[~ completion_future – destruktor](#dtor)|Zničí `completion_future` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get](#get)|Čeká na dokončení přidružené asynchronní operace.|  
|[potom](#then)|Řetězí do objekt funkce zpětného volání `completion_future` objekt, který chcete provést po dokončení provádění přidružené asynchronní operaci.|  
|[to_task](#to_task)|Vrátí `task` objekt odpovídající přidružené asynchronní operaci.|  
|[platný](#valid)|Získá logickou hodnotu, která určuje, zda je objekt přidružený asynchronní operace.|  
|[Počkej](#wait)|Bloky, dokud se nedokončí přidružené asynchronní operaci.|  
|[wait_for](#wait_for)|Bloky, dokud se nedokončí přidružené asynchronní operaci nebo za dobu určenou podle `_Rel_time` uplynul.|  
|[wait_until](#wait_until)|Blokuje až do dokončení přidružené asynchronní operaci, nebo dokud aktuální čas překročí hodnotu zadanou pomocí `_Abs_time`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operátor std::shared_future\<void >](#operator_shared_future)|Implicitně převede `completion_future` do objektu `std::shared_future` objektu.|  
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `completion_future` objekt s touto.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `completion_future`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amprt.h  
  
 **Namespace:** souběžnosti  


## <a name="ctor"></a>completion_future 

Inicializuje novou instanci třídy `completion_future` třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
completion_future();  
  
completion_future(  
    const completion_future& _Other );  
  
completion_future(  
    completion_future&& _Other );  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `completion_future` Objekt, který chcete zkopírovat nebo přesunout.  
  
### <a name="overloads-list"></a>Seznam přetížení  
  
|Název|Popis|  
|----------|-----------------|  
|`completion_future();`|Inicializuje novou instanci třídy `completion_future` – třída|  
|`completion_future(const completion_future& _Other);`|Inicializuje novou instanci třídy `completion_future` zkopírováním konstruktor.|  
|`completion_future(completion_future&& _Other);`|Inicializuje novou instanci třídy `completion_future` třída přesunutím konstruktor.|  
  
## <a name="get"></a>GET 

Čeká na dokončení přidružené asynchronní operace. Vyvolá uložené výjimku, pokud jeden došlo během asynchronní operaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void get() const;  
```  
  
## <a name="operator_shared_future"></a>std::shared_future – operátor<void> 

Implicitně převede `completion_future` do objektu `std::shared_future` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
operator std::shared_future<void>() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `std::shared_future` Objektu.  
  
## <a name="operator_eq"></a>operátor = 

Zkopíruje obsah zadaného `completion_future` objekt s touto.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
completion_future&  operator= (const completion_future& _Other );    
completion_future&  operator= (completion_future&& _Other );  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 Objekt, který se má zkopírovat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `completion_future` objektu.  
  
## <a name="overloads-list"></a>Seznam přetížení  
  
|Název|Popis|  
|----------|-----------------|  
|`completion_future& operator=(const completion_future& _Other);`|Zkopíruje obsah zadaného `completion_future` objektu do následujícímu pomocí hloubkové kopie.|  
|`completion_future& operator=(completion_future&& _Other);`|Zkopíruje obsah zadaného `completion_future` objekt s touto, pomocí přiřazení move.|  
  
## <a name="then"></a>potom 

Řetězí do objekt funkce zpětného volání `completion_future` objekt, který chcete provést po dokončení provádění přidružené asynchronní operaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template <typename _Functor>  
void then(const _Functor & _Func ) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Functor`  
 Functor zpětného volání.  
  
 `_Func`  
 Objekt funkce zpětného volání.  
  
## <a name="to_task"></a>to_task 

Vrátí `task` objekt odpovídající přidružené asynchronní operaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
concurrency::task<void> to_task() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `task` objekt odpovídající přidružené asynchronní operaci.  
  
## <a name="valid"></a>platný 

Získá logickou hodnotu, která určuje, zda je objekt přidružený asynchronní operace.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool valid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je objekt přidružený asynchronní operace; v opačném `false`.  
  
## <a name="wait"></a>Počkej 

Bloky, dokud se nedokončí přidružené asynchronní operaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void wait() const;  
```  
  
## <a name="wait_for"></a>wait_for 

Bloky, dokud se nedokončí přidružené asynchronní operaci nebo čas, který je zadán `_Rel_time` uplynul.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template <  
    class _Rep,  
    class _Period  
>  
std::future_status::future_status wait_for(  
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rep`  
 Aritmetické typ, který představuje počet značek.  
  
 `_Period`  
 Std::ratio představující počet sekund, po které uplynout za značek.  
  
 `_Rel_time`  
 Maximální množství času čekání na dokončení operace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí:  
  
-   `std::future_status::deferred`Pokud není spuštěná přidružené asynchronní operaci.  
  
-   `std::future_status::ready`Pokud je přidružené asynchronní operace dokončena.  
  
-   `std::future_status::timeout`Pokud zadané časové období uplynul.  
  
## <a name="wait_until"></a>wait_until 

Blokuje až do dokončení přidružené asynchronní operaci, nebo dokud aktuální čas překročí hodnotu zadanou pomocí `_Abs_time`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template <  
    class _Clock,  
    class _Duration  
>  
std::future_status::future_status wait_until(  
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Clock`  
 Hodiny, na kterém se měří tento bod čas.  
  
 `_Duration`  
 Časový interval od začátku `_Clock`na epoch, po jehož uplynutí dojde funkce vypršení časového limitu.  
  
 `_Abs_time`  
 Bod v čase, po které bude funkce vypršení časového limitu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí:  
  
1.  `std::future_status::deferred`Pokud není spuštěná přidružené asynchronní operaci.  
  
2.  `std::future_status::ready`Pokud je přidružené asynchronní operace dokončena.  
  
3.  `std::future_status::timeout`Pokud zadané časové období uplynul.  
  
## <a name="dtor"></a>~ completion_future 

Zničí `completion_future` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
~completion_future();  
```  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
