---
title: "Výhody vloženého sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60b8d458212cd2175f2460c1382ed7f8c2c269bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="advantages-of-inline-assembly"></a>Výhody inline assembleru
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Protože vložený assembler nevyžaduje samostatné kroky sestavení a propojení, je pohodlnější než samostatný assembler. Kód vloženého sestavení může použít název proměnné nebo funkce jazyka C, který je v rozsahu, takže jej lze snadno integrovat do kódu jazyka C programu. Protože kód sestavení můžete kombinovat vložené s příkazy jazyka C nebo C++, můžete provést úkoly, které jsou komplikované nebo dokonce znemožňují v jazyka C nebo C++.  
  
 Použití vloženého sestavení patří:  
  
-   Funkce zápisu v jazyce sestavení.  
  
-   Optimalizace místo rychlost kritické oddíly kódu.  
  
-   Provedení hardwaru přímý přístup pro ovladače zařízení.  
  
-   Psaní kódu prolog a epilog pro "holé" volání.  
  
 Vnořené sestavení je nástroj pro zvláštní účely. Pokud máte v plánu k portu aplikace na různé počítače, budete pravděpodobně chtít umístit samostatný modul kódu pro konkrétní počítač. Vložený assembler nepodporuje všechny programu Microsoft Macro Assembler na (MASM) direktivy makra a data, může být pohodlnější použití MASM pro tyto moduly.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vkládaný assembler](../../assembler/inline/inline-assembler.md)