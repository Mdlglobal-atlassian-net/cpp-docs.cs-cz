---
title: '&lt;condition_variable&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <condition_variable>
dev_langs:
- C++
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5bd3d3bd6ef4976f5f9c55d1905b02314a88438d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable&gt;
Definuje třídy [condition_variable](../standard-library/condition-variable-class.md) a [condition_variable_any](../standard-library/condition-variable-any-class.md) které se používají k vytváření objektů, které počkejte podmínku, kterou chcete přestat hodnotu true.  
  
 Tuto hlavičku použije Concurrency Runtime (ConcRT), takže ho můžete použít společně s jiným mechanismem ConcRT. Další informace o ConcRT najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#include <condition_variable>  
```  
  
> [!NOTE]
>  V kódu, který se zkompiluje pomocí **/CLR**, tuto hlavičku je blokovaný.  
  
### <a name="remarks"></a>Poznámky  
 Kód, který čeká pro proměnnou podmínku, musíte také použít `mutex`. Volající vlákno musí uzamčení `mutex` před zavoláním funkce, které čekat na proměnnou podmínku. `mutex` Je stanovena pevně po návratu volaná funkce. `mutex` Není uzamčený době vlákno čeká podmínku, která má být true. Tak, aby nebyly nalezeny žádné nepředvídatelné výsledky, každý podproces, který čeká na proměnnou podmínku musíte použít stejné `mutex` objektu.  
  
 Objekty typu `condition_variable_any` lze použít s mutex libovolného typu. Není nutné poskytnout typ mutex, který se používá `try_lock` metoda. Objekty typu `condition_variable` lze použít pouze s mutex typu `unique_lock<mutex>`. Objekty tohoto typu může být rychlejší než objekty typu `condition_variable_any<unique_lock<mutex>>`.  
  
 Čekání na událost, nejprve mutex Zamknout a pak volání jednoho z `wait` metody pro proměnnou podmínku. `wait` Volání bloky, dokud jiné vlákno signály proměnnou podmínku.  
  
 *Nesprávné wakeups* dojít, když vláken, které se mají pro proměnné podmínky stát odblokuje bez potřeby oznámení. Rozpoznat takové nesprávné wakeups, by měl kód, který čeká podmínku, kterou chcete přestat true explicitně kontrola této podmínky, při kód vrátí z funkce čekání. To se obvykle provádí pomocí smyčku; můžete použít `wait(unique_lock<mutex>& lock, Predicate pred)` k provedení této smyčky za vás.  
  
```cpp  
while (condition is false)
    wait for condition variable;
```  
  
 `condition_variable_any` a `condition_variable` třídy každý mají tři metody, které čekat na podmínce.  
  
- `wait` čeká bez vazby časové období.  
  
- `wait_until` počká, dokud nebude zadané `time`.  
  
- `wait_for` čeká na zadané `time interval`.  
  
 Každá z těchto metod má dvě přetížené verze. Jeden právě vyčká a k buzení spuriously. Druhá trvá další šablony argument, který definuje predikátu. Metoda nevrátí, dokud nebude predikát `true`.  
  
 Každá třída také obsahuje dvě metody, které slouží k upozornění podmínku proměnné, která je jeho stav `true`.  
  
- `notify_one` probudí jeden z vláken, která čeká na proměnnou podmínku.  
  
- `notify_all` probudí všechny podprocesy, které čekají na proměnnou podmínku.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [condition_variable – třída](../standard-library/condition-variable-class.md)   
 [condition_variable_any – třída](../standard-library/condition-variable-any-class.md)
