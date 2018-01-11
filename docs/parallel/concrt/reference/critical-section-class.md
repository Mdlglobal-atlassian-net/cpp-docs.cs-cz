---
title: "critical_section – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
dev_langs: C++
helpviewer_keywords: critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5421cf47214d4ceeb7f8388835cb7a1cc57110ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsection-class"></a>critical_section – třída
Mutex nejsou vícenásobně přístupné, což je explicitně vědět Concurrency Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class critical_section;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`native_handle_type`|Odkaz na `critical_section` objektu.|  
  
### <a name="public-classes"></a>Veřejné třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[critical_section::scoped_lock – třída](#critical_section__scoped_lock_class)|Obálku výjimka bezpečné RAII pro `critical_section` objektu.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[critical_section](#ctor)|Vytvoří novou část důležité.|  
|[~ critical_section – destruktor](#dtor)|Zničí kritická sekce.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[lock](#lock)|Získá tato část důležité.|  
|[native_handle –](#native_handle)|Pokud existuje, vrátí platformy konkrétní nativní popisovač.|  
|[try_lock –](#try_lock)|Pokusí se získat zámek bez blokování.|  
|[try_lock_for –](#try_lock_for)|Pokusí se získat zámek bez pro konkrétní počet milisekund blokování.|  
|[odemknutí](#unlock)|Odemkne kritická sekce.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [synchronizační datové struktury](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `critical_section`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a>critical_section 

 Vytvoří novou část důležité.  
  
```
critical_section();
```  
  
##  <a name="dtor"></a>~ critical_section 

 Zničí kritická sekce.  
  
```
~critical_section();
```  
  
### <a name="remarks"></a>Poznámky  
 Očekává se, že zámek trvá už při spuštění destruktoru. Povolení části kritické destruct s zámek stále uchovávat výsledky v nedefinované chování.  
  
##  <a name="lock"></a>Zámek 

 Získá tato část důležité.  
  
```
void lock();
```  
  
### <a name="remarks"></a>Poznámky  
 Je často bezpečnější využívat [scoped_lock](#critical_section__scoped_lock_class) konstrukce k získání a uvolněte `critical_section` objekt v výjimku bezpečným způsobem.  
  
 Pokud zámek již držené volání kontextu [improper_lock](improper-lock-class.md) dojde k výjimce.  
  
##  <a name="native_handle"></a>native_handle – 

 Pokud existuje, vrátí platformy konkrétní nativní popisovač.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na části důležité.  
  
### <a name="remarks"></a>Poznámky  
 A `critical_section` objekt není spojen s konkrétní nativní popisovač platformu pro operační systém Windows. Metoda jednoduše vrátí odkaz na odkaz sám na sebe.  
  
##  <a name="critical_section__scoped_lock_class"></a>critical_section::scoped_lock – třída  
 Obálku výjimka bezpečné RAII pro `critical_section` objektu.  
  
```
class scoped_lock;
```  
  
##  <a name="critical_section__scoped_lock_ctor"></a>scoped_lock::scoped_lock 

 Vytvoří `scoped_lock` objektů a získá `critical_section` objekt předaná `_Critical_section` parametr. Pokud kritická sekce trvá jiné vlákno, toto volání se zablokuje.  
  
```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```  
  
### <a name="parameters"></a>Parametry  
 `_Critical_section`  
 Kritická sekce se uzamknout.  
  
##  <a name="critical_section__scoped_lock_dtor"></a>scoped_lock –:: ~ scoped_lock – 

 Zničí `scoped_lock` objektu a uvolní kritická sekce zadaný v jeho konstruktoru.  
  
```
~scoped_lock();
```  
  
##  <a name="try_lock"></a>try_lock – 

 Pokusí se získat zámek bez blokování.  
  
```
bool try_lock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud se získal zámek, hodnota `true`, jinak hodnota `false`.  
  
##  <a name="try_lock_for"></a>try_lock_for – 

 Pokusí se získat zámek bez pro konkrétní počet milisekund blokování.  
  
```
bool try_lock_for(unsigned int _Timeout);
```  
  
### <a name="parameters"></a>Parametry  
 `_Timeout`  
 Počet milisekund čekání před vypršením časového limitu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud se získal zámek, hodnota `true`, jinak hodnota `false`.  
  
##  <a name="unlock"></a>odemknutí 

 Odemkne kritická sekce.  
  
```
void unlock();
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [reader_writer_lock – třída](reader-writer-lock-class.md)
