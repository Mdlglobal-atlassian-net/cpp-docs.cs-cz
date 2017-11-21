---
title: "&lt;mutex&gt; funkce a proměnné | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
caps.latest.revision: "11"
manager: ghogen
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.openlocfilehash: a81d134a4fb49f9123dbed5b4146976d5c676379
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;mutex&gt; funkce a proměnné
||||  
|-|-|-|  
|[adopt_lock –](#adopt_lock)|[call_once –](#call_once)|[defer_lock –](#defer_lock)|  
|[Zámek](#lock)|[try_to_lock –](#try_to_lock)|  
  
##  <a name="adopt_lock"></a>adopt_lock – proměnná  
 Představuje objekt, který se dá předat do konstruktory pro [lock_guard](../standard-library/lock-guard-class.md) a [unique_lock](../standard-library/unique-lock-class.md) k označení, že objekt mutex, který je také se předaný konstruktoru je uzamčen.  
  
```cpp  
const adopt_lock_t adopt_lock;
```  
  
##  <a name="call_once"></a>call_once –  
 Poskytuje mechanismus pro volání právě jednou na zadaný objekt s během provádění.  
  
```
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```  
  
### <a name="parameters"></a>Parametry  
 `Flag`  
 A [once_flag –](../standard-library/once-flag-structure.md) objekt, který zajistí, že objekt s je volána pouze jednou.  
  
 `F`  
 Objekt s.  
  
 `A`  
 Seznam argumentů.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `Flag` není platný, funkce vyvolá [system_error –](../standard-library/system-error-class.md) s kódem chyby `invalid_argument`. Jinak funkce šablony použije jeho `Flag` argument zajistit, že volá `F(A...)` úspěšně právě jednou, bez ohledu na to, kolikrát je volána funkce šablony. Pokud `F(A...)` ukončí podle došlo k výjimce, volání nebyla úspěšná.  
  
##  <a name="defer_lock"></a>defer_lock – proměnná  
 Představuje objekt, který lze předat v konstruktoru pro [unique_lock](../standard-library/unique-lock-class.md). To znamená, že by neměl konstruktoru zamknout objekt mutex, který je také předávána k němu.  
  
```cpp  
const defer_lock_t defer_lock;
```  
  
##  <a name="lock"></a>Zámek  
 Pokusí se uzamknout všechny argumenty bez vzájemného zablokování.  
  
```cpp  
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```  
  
### <a name="remarks"></a>Poznámky  
 Argumenty funkce šablony musí být *mutex typy*, s výjimkou toho, který volá, aby se `try_lock` může vyvolat výjimky.  
  
 Všechny argumenty bez zablokování funkce zamkne voláním `lock`, `try_lock`, a `unlock`. Pokud volání `lock` nebo `try_lock` vyvolá výjimku, volání funkce `unlock` na žádném z mutex objekty, které byly úspěšně uzamčena před opětné vyvolání výjimky.  
  
##  <a name="try_to_lock"></a>try_to_lock – proměnná  
 Představuje objekt, který lze předat v konstruktoru pro [unique_lock](../standard-library/unique-lock-class.md) k označení, že konstruktoru opakovat odemknutí `mutex` také se předá do něj bez blokování.  
  
```cpp  
const try_to_lock_t try_to_lock;
```  
  
## <a name="see-also"></a>Viz také  
 [\<mutex >](../standard-library/mutex.md)



