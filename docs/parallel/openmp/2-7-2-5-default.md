---
title: "2.7.2.5 výchozí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ee328be7f9f0c4876738f8179c26e700c57702c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="2725-default"></a>2.7.2.5 default
**Výchozí** klauzule umožňuje uživateli ovlivnit atributy sdílení dat proměnných. Syntaxe **výchozí** klauzule vypadá takto:  
  
```  
default(shared | none)  
```  
  
 Určení **default(shared)** je ekvivalentní explicitně výpis každou aktuálně viditelné proměnnou v **sdílené** klauzule, pokud je **threadprivate** nebo **cons**`t`-kvalifikovaný. Bez explicitního **výchozí** klauzule, výchozí chování je stejné jako v případě **default(shared)** byly zadány.  
  
 Určení **default(none)** vyžaduje, že aspoň jeden z následujících musí být pro každý odkaz na proměnnou v lexikální rozsah paralelní konstrukce na hodnotu true:  
  
-   Proměnná je explicitně uvedena v klauzuli atribut sdílení dat konstruktor, který obsahuje odkaz na.  
  
-   Proměnná je deklarované v rámci paralelní konstrukce.  
  
-   Proměnná je **threadprivate**.  
  
-   Má proměnná **const**-kvalifikovaný typ.  
  
-   Proměnná je řídicí proměnná smyčky pro **pro** smyčky, který následuje **pro** nebo **paralelní pro** směrnice a odkaz na proměnnou se zobrazí uvnitř smyčky .  
  
 Zadání proměnné na **firstprivate**, **lastprivate**, nebo **snížení** klauzule závorkách – direktiva způsobí implicitní odkaz na proměnnou uzavření kontext. Implicitní odkazu si také vztahují požadavky uvedené výše.  
  
 Jediným **výchozí** může být zadána klauzule na **paralelní** – direktiva.  
  
 Výchozí proměnná atributů pro sdílení dat lze přepsat pomocí **privátní**, **firstprivate**, **lastprivate**, **snížení**, a **sdílené** klauzule, jak je ukázáno v následujícím příkladu:  
  
```  
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\  
   private(x)  private(r)  lastprivate(i)  
```