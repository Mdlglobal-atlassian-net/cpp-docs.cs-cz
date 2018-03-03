---
title: struktura RUNTIME_FUNCTION | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c05dcd516af5c078b4e4e664bae16f65370ca117
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="struct-runtimefunction"></a>struct RUNTIME_FUNCTION
Zpracování výjimek tabulky vyžaduje záznam tabulky pro všechny funkce, které přidělit prostor v zásobníku nebo volat jinou funkci (například ke funkce). Funkce tabulky položky mají formát:  
  
|||  
|-|-|  
|ULONG –|Počáteční adresa funkce|  
|ULONG –|Koncová adresa funkce|  
|ULONG –|Adresa unwind info|  
  
 Struktura RUNTIME_FUNCTION musí být typu DWORD v paměti. Všechny adresy jsou relativní bitové kopie, to znamená, že jsou 32-bit posun od počáteční adresa bitové kopie, který obsahuje záznam tabulky funkcí. Tyto položky jsou seřazené a vložit do části .pdata bitové kopie PE32 +. Pro dynamicky generovaném funkcí [JIT překladače] modulu runtime pro podporu těchto funkcí nutné použít RtlInstallFunctionTableCallback nebo RtlAddFunctionTable poskytnout tyto informace do operačního systému. Tak neučiníte způsobí nespolehlivé zpracování výjimek a ladění procesů.  
  
## <a name="see-also"></a>Viz také  
 [Unwind data pro zpracování výjimek, podpora ladění](../build/unwind-data-for-exception-handling-debugger-support.md)