---
title: Definice modulu (. Soubory def) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49f5eb5b75bad22b59cb4fbb98554bbfd44d13b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="module-definition-def-files"></a>Soubory definice modulu (.Def)
Soubory definice modulu (.def) zadejte linkeru s informacemi o export, atributy a další informace o program, který má být propojena. Soubor .def je velmi užitečné při vytváření knihovny DLL. Protože nejsou k dispozici [možnosti linkeru](../../build/reference/linker-options.md) který lze použít místo příkazy definice modulu .def soubory jsou obecně není nutné. Můžete také použít [__declspec(dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md) jako způsob, jak určit exportovaných funkcí.  
  
 Soubor .def můžete vyvolat během fáze linkeru s [/def (zadat soubor definice modulu)](../../build/reference/def-specify-module-definition-file.md) – možnost linkeru.  
  
 Pokud vytváříte soubor .exe, který nelze exportovat, pomocí souborů .def budou načítání vaše výstupní soubor větší a pomalejší.  
  
 Příklad, naleznete v části [export z knihovny DLL pomocí souborů DEF](../../build/exporting-from-a-dll-using-def-files.md).  
  
 Najdete v následujících částech Další informace:  
  
-   [Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)  
  
-   [EXPORTY](../../build/reference/exports.md)  
  
-   [VELIKOST HALDY](../../build/reference/heapsize.md)  
  
-   [KNIHOVNA](../../build/reference/library.md)  
  
-   [JMÉNO](../../build/reference/name-c-cpp.md)  
  
-   [ODDÍLY](../../build/reference/sections-c-cpp.md)  
  
-   [VELIKOST ZÁSOBNÍKU](../../build/reference/stacksize.md)  
  
-   [ZÁSTUPNÁ PROCEDURA](../../build/reference/stub.md)  
  
-   [VERZE](../../build/reference/version-c-cpp.md)  
  
-   [Vyhrazená slova](../../build/reference/reserved-words.md)  
  
## <a name="see-also"></a>Viz také  
 [Odkaz sestavení C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)  