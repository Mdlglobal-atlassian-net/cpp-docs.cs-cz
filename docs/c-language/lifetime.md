---
title: Doba platnosti | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ce98025001529313260f62e8f45e85add148c77
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="lifetime"></a>Doba platnosti
„Životnost“ je doba provádění při vykonávání programu, ve které existuje proměnná nebo funkce. Doba trvání úložiště identifikátoru určuje jeho životnost.  
  
 Identifikátor deklarovat s *specifikátor třídy úložiště* **statické** má úložiště se statickými doba trvání. Identifikátory se statickou dobou úložiště (nazývané také „globální“) mají úložiště a definovanou hodnotu po dobu vykonávání programu. Úložiště je vyhrazeno a uložená hodnota identifikátoru je inicializována pouze jednou, před spuštěním programu. Identifikátor deklarovat s vnější nebo vnitřní propojení má také doba trvání úložiště se statickými (viz [propojení](../c-language/linkage.md)).  
  
 Identifikátor deklarovaná bez **statické** – specifikátor třídy úložiště má trvání uložení automatické, pokud je deklarovaná uvnitř funkce. Identifikátor s automatickou dobou trvání úložiště („místní identifikátor“) má úložiště a definovanou hodnotou pouze v rámci bloku, kde je identifikátor definován nebo deklarován. Automatickému identifikátoru je přiděleno nové úložiště pokaždé, když program přejde do tohoto bloku a ztratí své úložiště (a jeho hodnotu) při opuštění bloku programem. Identifikátory, které jsou deklarovány ve funkci bez propojení, mají také automatickou dobu trvání úložiště.  
  
 Následující pravidla určují, zda má identifikátor globální (statickou) nebo místní (automatickou) životnost:  
  
-   Všechny funkce mají statickou životnost. A proto existují po celou dobu při provádění programu. Identifikátory deklarované na vnější úrovni (tedy mimo všechny bloky v programu na stejné úrovni definic funkcí) mají vždy globální (statickou) životnost.  
  
-   Pokud místní proměnné inicializátoru, proměnné se inicializuje pokaždé, když je vytvořen (Pokud je deklarován jako **statické**). Parametry funkce mají také místní životnost. Můžete zadat globální doba platnosti pro identifikátor v rámci bloku včetně **statické** specifikátor třídy úložiště v jeho deklaraci. Jednou deklarovaný **statické**, proměnná uchovává svou hodnotu z jedna položka bloku na další.  
  
 I když existuje identifikátor s globální doba platnosti v průběhu provádění zdrojový program (například externě deklarované proměnné nebo místní proměnné deklarovat s **statické** – klíčové slovo), nemusí být viditelné ve všech součásti programu. V tématu [rozsah a viditelnost](../c-language/scope-and-visibility.md) informace o viditelnost a zjistit, [třídy úložiště](../c-language/c-storage-classes.md) diskuzi o *specifikátor třídy úložiště* nonterminal.  
  
 Paměť lze rozdělit podle potřeby (dynamicky), pokud je vytvářena pomocí speciálních rutin knihovny, jako je `malloc`. Jelikož dynamické přidělování paměti používá rutiny knihoven, není považováno za součást jazyka. Najdete v článku [malloc –](../c-runtime-library/reference/malloc.md) v fungovat *referenční dokumentace běhové knihovny*.  
  
## <a name="see-also"></a>Viz také  
 [Doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md)