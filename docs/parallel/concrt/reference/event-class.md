---
title: "Event – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
dev_langs: C++
helpviewer_keywords: event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 53a49eeeaa6c9fb83b5dc2b96001a2b2097fbe5e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="event-class"></a>event – třída
Ruční vynulování události, které explicitně zná Concurrency Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class event;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[~ event – destruktor](#dtor)|Zničí událost.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[resetování](#reset)|Obnoví události do stavu signál.|  
|[nastavení](#set)|Signály události.|  
|[Počkej](#wait)|Čeká na událost, která má být signál.|  
|[wait_for_multiple –](#wait_for_multiple)|Čeká na více událostí k stát signál.|  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[timeout_infinite](#timeout_infinite)|Hodnota označující, počkejte by nikdy neměly vypršení časového limitu.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [synchronizační datové struktury](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `event`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a>události 

 Vytvoří novou událost.  
  
```
_CRTIMP event();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="dtor"></a>~ událostí 

 Zničí událost.  
  
```
~event();
```  
  
### <a name="remarks"></a>Poznámky  
 Očekává se, že neexistují žádné vláken čekajících na událost, když běží destruktoru. Povolení události destruct s vláken, která čekají na něm výsledkem nedefinované chování.  
  
##  <a name="reset"></a>resetování 

 Obnoví události do stavu signál.  
  
```
void reset();
```  
  
##  <a name="set"></a>nastavení 

 Signály události.  
  
```
void set();
```  
  
### <a name="remarks"></a>Poznámky  
 Signalizace události může způsobit libovolný počet kontexty čekání na událost se spustitelného.  
  
##  <a name="timeout_infinite"></a>timeout_infinite 

 Hodnota označující, počkejte by nikdy neměly vypršení časového limitu.  
  
```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```  
  
##  <a name="wait"></a>Počkej 

 Čeká na událost, která má být signál.  
  
```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `_Timeout`  
 Označuje počet milisekund, než vyprší časový limit čekání. Hodnota `COOPERATIVE_TIMEOUT_INFINITE` označuje, že je bez časového limitu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud byla splněna čekání, hodnota `0` je vrácená, jinak hodnota `COOPERATIVE_WAIT_TIMEOUT` indikující, že dobu vypršení časového limitu bez událost signál, aby se aktivovala.  
  
> [!IMPORTANT]
>  V [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] aplikace, nevolejte `wait` na ASTA vláken, protože toto volání může blokovat aktuální vlákno a může způsobit, že aplikace přestane odpovídat.  
  
##  <a name="wait_for_multiple"></a>wait_for_multiple – 

 Čeká na více událostí k stát signál.  
  
```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `_PPEvents`  
 Pole pro čekání na události. Počet událostí v rámci pole je indikován `count` parametr.  
  
 `count`  
 Počet událostí v rámci zadané v poli `_PPEvents` parametr.  
  
 `_FWaitAll`  
 Pokud nastaven na hodnotu `true`, tento parametr určuje, že všechny události v rámci pole zadaná v `_PPEvents` parametr musí být signál, splníte čekání. Pokud nastaven na hodnotu `false`, určuje, že všechny události v rámci pole zadaná v `_PPEvents` parametr signál, aby se aktivovala budou splňovat čekání.  
  
 `_Timeout`  
 Označuje počet milisekund, než vyprší časový limit čekání. Hodnota `COOPERATIVE_TIMEOUT_INFINITE` označuje, že je bez časového limitu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud byla splněna čekat, zadána index v poli v `_PPEvents` parametr, který splněna podmínka čekání., jinak hodnota `COOPERATIVE_WAIT_TIMEOUT` indikující, že dobu vypršení časového limitu bez podmínky splněné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud parametr `_FWaitAll` je nastaven na hodnotu `true` k označení, že všechny události musí stát signál, aby pokryl čekání, představuje index vráceným funkcí žádný speciální význam než fakt, že se nejedná o hodnotě `COOPERATIVE_WAIT_TIMEOUT`.  
  
> [!IMPORTANT]
>  V [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] aplikace, nevolejte `wait_for_multiple` na ASTA vláken, protože toto volání může blokovat aktuální vlákno a může způsobit, že aplikace přestane odpovídat.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)
