---
title: "Holé funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- naked functions
- functions [C++], naked
- prolog code
- epilog code
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8998437389fecabb07293b1e1bb087fea8f39944
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="naked-functions"></a>Holé funkce
**Konkrétní Microsoft**  
  
 Atribut třídy úložiště `naked` je rozšíření jazyka C specifické pro společnost Microsoft. Pro funkce deklarované s atributem třídy úložiště `naked` generuje kompilátor kód bez kódu prologu a epilogu. Tuto funkci lze použít pro psaní vlastních sekvencí kódu epilogu nebo prologu pomocí vloženého kódu assembleru. Neviditelné funkce jsou zvláště užitečné při psaní ovladačů virtuálních zařízení.  
  
 Protože `naked` atribut je pouze relevantní pro definici funkce a není modifikátor typu, holé funkce použijte syntaxi rozšířených atributů, popsané v [rozšířené atributy třídy úložiště](../c-language/c-extended-storage-class-attributes.md).  
  
 Následující příklad definuje funkci s atributem `naked`:  
  
```  
__declspec( naked ) int func( formal_parameters )  
{  
   /* Function body */  
}  
```  
  
 Nebo alternativně:  
  
```  
#define Naked   __declspec( naked )  
  
Naked int func( formal_parameters )  
{  
   /* Function body */  
}  
```  
  
 Atribut `naked` ovlivňuje pouze povahu generování kódu kompilátoru pro sekvence prologu a epilogu funkce. Neovlivňuje kód, který je generován pro volání těchto funkcí. Navíc atribut `naked` není považován za součást typu funkce a ukazatele funkce nemohou mít atribut `naked`. Kromě toho nelze atribut `naked` použít pro definici dat. Například následující kód vygeneruje chyby:  
  
```  
__declspec( naked ) int i;  /* Error--naked attribute not */  
                            /* permitted on data declarations. */  
```  
  
 Atribut `naked` je relevantní pouze pro definici funkce a nemůže být zadán v prototypu funkce. Následující deklarace generuje chybu kompilátoru:  
  
```  
__declspec( naked ) int func();   /* Error--naked attribute not */  
                     /* permitted on function declarations.    */   \  
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Definice funkcí jazyka C](../c-language/c-function-definitions.md)