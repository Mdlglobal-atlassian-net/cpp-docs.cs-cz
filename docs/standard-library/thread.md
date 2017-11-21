---
title: "&lt;vlákno&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <thread>
dev_langs: C++
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7685bd1c112651b07540fefd2a28be91c9671706
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltthreadgt"></a>&lt;přístup z více vláken&gt;
Zahrnují standardní hlavičku \<vlákno > pro definování třídy `thread` a různé podpůrné funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  V kódu, který se zkompiluje pomocí **/CLR**, tuto hlavičku je blokovaný.  
  
 `__STDCPP_THREADS__` Makro je definován jako nenulovou hodnotu indikující, že vláken podporuje tuto hlavičku.  
  
## <a name="members"></a>Členové  
  
### <a name="public-classes"></a>Veřejné třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[Thread – třída](../standard-library/thread-class.md)|Definuje objekt, který se používá k sledovat a spravovat vlákno při provádění v aplikaci.|  
  
### <a name="public-structures"></a>Veřejné struktury  
  
|Název|Popis|  
|----------|-----------------|  
|[hash – struktura (standardní knihovna C++)](../standard-library/hash-structure-stl.md)|Definuje členské funkce, která vrátí hodnotu, která je jednoznačně dáno `thread::id`. Definuje – členská funkce [hash](../standard-library/hash-class.md) funkce, který je vhodný pro mapování hodnoty typu `thread::id` k distribučnímu index hodnot.|  
  
### <a name="public-functions"></a>Veřejné funkce  
  
|Název|Popis|  
|----------|-----------------|  
|[get_id –](../standard-library/thread-functions.md#get_id)|Jednoznačně identifikuje aktuální vlákno provádění.|  
|[sleep_for –](../standard-library/thread-functions.md#sleep_for)|Blokuje volající vlákno.|  
|[sleep_until –](../standard-library/thread-functions.md#sleep_until)|Volající vlákno blokuje alespoň do zadané doby.|  
|[swap](../standard-library/thread-functions.md#swap)|Výměny stavy dva `thread` objekty.|  
|[YIELD –](../standard-library/thread-functions.md#yield)|Signály operačního systému spustit jiná vlákna i v případě, že aktuální vlákno by normálně nadále fungoval.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Operator > = – operátor](../standard-library/thread-operators.md#op_gt_eq)|Určuje, zda jeden `thread::id` je větší než nebo rovna hodnotě jiný objekt.|  
|[Operator > – operátor](../standard-library/thread-operators.md#op_gt)|Určuje, zda jeden `thread::id` je větší než druhý objekt.|  
|[Operator < = – operátor](../standard-library/thread-operators.md#op_lt_eq)|Určuje, zda jeden `thread::id` objektu je menší než nebo rovna do jiného.|  
|[Operator < – operátor](../standard-library/thread-operators.md#op_lt)|Určuje, zda jeden `thread::id` objektu je menší než jiné.|  
|[Operator! = – operátor](../standard-library/thread-operators.md#op_neq)|Porovná dva `thread::id` objekty nerovnost.|  
|[Operator == – operátor](../standard-library/thread-operators.md#op_eq_eq)|Porovná dva `thread::id` objekty rovnosti.|  
|[operátor << – operátor](../standard-library/thread-operators.md#op_lt_lt)|Vloží text reprezentace `thread::id` objektu do datového proudu.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

