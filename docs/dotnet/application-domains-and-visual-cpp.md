---
title: "Aplikační domény a Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 57a45bd6f73040623fe90626b1c3896df3258dd8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="application-domains-and-visual-c"></a>Domény aplikace a jazyk Visual C++
Pokud máte `__clrcall` virtuální funkce tabulce vtable bude podle domény aplikace (appdomain). Pokud vytvoříte objekt v jedné doméně aplikace, může volat pouze virtuální funkci z této domény. Všechny funkce, které jsou definované v **/CLR: pure** používají konvenci `__clrcall` konvence volání. Proto všechny virtuálních tabulek definované v **/CLR: pure** souborech určených ke kompilaci jsou jednotlivé domény aplikace. Ve smíšeném režimu (**/CLR**) bude mít za virtuálních proces tabulek, pokud váš typ nemá žádné `__clrcall` virtuální funkce. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 Další informace naleznete v tématu  
  
-   [domény aplikace](../cpp/appdomain.md)  
  
-   [__clrcall](../cpp/clrcall.md)  
  
-   [Postupy: přechod na/CLR: pure (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [proces](../cpp/process.md)  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)