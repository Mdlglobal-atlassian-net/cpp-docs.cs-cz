---
title: "Důležité informace o další spuštění | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 57b1de8fbbdb3d969dca8e84e57e18b81749d944
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="additional-startup-considerations"></a>Další důležité informace o spuštění
V jazyce C++ může tvorba a rušení objektů zahrnovat spouštění uživatelského kódu. Proto je důležité si uvědomit, které inicializacích dojít před vstupem do **hlavní** a které destruktory jsou vyvolány po ukončení z **hlavní**. (Podrobné informace o vytváření a odstraňování objektů najdete v tématu [konstruktory](../cpp/constructors-cpp.md) a [destruktory](../cpp/destructors-cpp.md).)  
  
 Následující inicializacích provést před zápisem na **hlavní**:  
  
-   Výchozí inicializace statických dat na hodnotu nula. Všechna statická data bez explicitních inicializátorů jsou před spuštěním jakéhokoli jiného kódu nastaveny na hodnotu nula, včetně inicializací za běhu. Statické datové členy musí být explicitně definovány.  
  
-   Inicializace globálních statických objektů v jednotce převodu. K tomu může dojít, buď před vstupem do **hlavní** nebo před prvním použití jakékoli funkce nebo objekt v objektu překlad jednotky.  
  
 **Konkrétní Microsoft**  
  
 V aplikaci Microsoft C++ jsou globální statické objekty inicializovat před vstupem do **hlavní**.  
  
 **Konkrétní Microsoft END**  
  
 Globální statické objekty jsou vzájemně závislé, v jiných jednotkách převodu však mohou zapříčinit nesprávné chování.  
  
## <a name="see-also"></a>Viz také  
 [Spuštění a ukončení](../cpp/startup-and-termination-cpp.md)