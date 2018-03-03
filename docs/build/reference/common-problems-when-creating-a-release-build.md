---
title: "Běžné problémy při vytváření sestavení pro vydání | Microsoft Docs"
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
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting Visual C++
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44b5528a2d6bedaaaa7ddce582f58042e084b3d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="common-problems-when-creating-a-release-build"></a>Běžné problémy při vytváření sestavení pro vydání
Během vývoje bude obvykle sestavení a testů s sestavení ladicí verze projektu. Pokud potom vytvoříte aplikaci pro sestavení pro vydání, může dojít k porušení přístupu.  
  
 Níže uvedeného seznamu uvedeny primární rozdíly mezi ladění a sestavení pro vydání (nondebug). Existují další rozdíly, ale toto jsou primární rozdíly, které by způsobily selhání aplikace v sestavení pro vydání, když v sestavení ladicí verze funguje.  
  
-   [Rozložení haldy](#_core_heap_layout)  
  
-   [Kompilace](#_core_compilation)  
  
-   [Podpora ukazatele](#_core_pointer_support)  
  
-   [Optimalizace](#_core_optimizations)  
  
 Najdete v článku [/GZ (Catch sestavení pro vydání chyby v ladění sestavení)](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md) chyby v sestavení pro ladění – možnost kompilátoru informace o tom, jak zachytit verzi sestavení.  
  
##  <a name="_core_heap_layout"></a>Rozložení haldy  
 Rozložení haldy bude příčina přibližně 90 % zřejmá problémy, když aplikace funguje v ladění, ale není verze.  
  
 Při sestavování projektu pro ladění, používáte ladění přidělení paměti. To znamená, že všechny přidělení paměti mít ochrana bajtů umístit je obcházet. Tato ochrana bajtů zjistit přepisování paměti. Protože rozložení haldy se liší verze a ladicí verze, přepisování paměti nemusí vytvářet všechny problémy v sestavení ladicí verze, ale mohou mít závažné účinky v sestavení pro vydání.  
  
 Další informace najdete v tématu [zkontrolujte přepsání paměti](../../build/reference/checking-for-memory-overwrites.md) a [použít ladění sestavení do zkontrolujte pro přepsání paměti](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md).  
  
##  <a name="_core_compilation"></a>Kompilace  
 Mnoho v makrech MFC a většinu změn implementace MFC při sestavení pro vydání. Konkrétně makra ASSERT vyhodnotí jako ustanovení v sestavení pro vydání, tak bude proveden žádný kód v nepodmíněné výrazy nalezen. Další informace najdete v tématu [zkontrolujte ASSERT – příkazy](../../build/reference/using-verify-instead-of-assert.md).  
  
 Některé funkce jsou vložená pro vyšší rychlost v sestavení pro vydání. Optimalizace jsou obecně zapnuté v sestavení pro vydání. Přidělení různých paměti se také používá.  
  
##  <a name="_core_pointer_support"></a>Podpora ukazatele  
 Chybí informace o ladění Odebere odsazení z vaší aplikace. V sestavení pro vydání mít ukazatele stray zvyšuje pravděpodobnost odkazující na neinicializované paměti místo odkazující na informace o ladění.  
  
##  <a name="_core_optimizations"></a>Optimalizace  
 V závislosti na povaze určité segmenty kódu může generovat optimalizace kompilátoru neočekávaný kód. Toto je alespoň pravděpodobnou příčinou problémů se sestavením pro vydání, ale v některých případech způsobit. Řešení, najdete v části [optimalizace si kód](../../build/reference/optimizing-your-code.md).  
  
## <a name="see-also"></a>Viz také  
 [Sestavení pro vydání](../../build/reference/release-builds.md)   
 [Oprava problémů se sestavením pro vydání](../../build/reference/fixing-release-build-problems.md)