---
title: "Import pomocí souborů DEF | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 81148525b70f3c5ff351feb9561699f3b9b5e932
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="importing-using-def-files"></a>Import pomocí souborů DEF
Pokud chcete použít **deklarace __declspec(dllimport)** společně s .def souboru, měli byste změnit soubor .def pomocí dat místo KONSTANTA sníží pravděpodobnost, že nesprávné kódování může dojít k potížím:  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   DATA  
```  
  
 V následující tabulce jsou uvedeny důvod, proč.  
  
|– Klíčové slovo|Vysílá v knihovně importu|Export|  
|-------------|---------------------------------|-------------|  
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|  
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|  
  
 Pomocí **deklarace __declspec(dllimport)** a KONSTANTA uvádí, jak `imp` verze a názvu bez upraveného v .lib DLL importovat knihovny, která je vytvořena za účelem povolení explicitní propojení. Pomocí **deklarace __declspec(dllimport)** a zobrazí DATA jenom na `imp` verzi název.  
  
 Pokud používáte KONSTANTA, následující konstrukce kódu lze použít pro přístup k `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 -nebo-  
  
```  
ULONG *ulDataInDll;      /*prototype*/  
if (*ulDataInDll == 0L)  /*sample code fragment*/  
```  
  
 Pokud používáte DATA v souboru .def, ale mají pouze zkompilování kódu s následující definici přístup k proměnné `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll;  
  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 Použití KONSTANTA je více rizikové, protože pokud zapomenete použít vyšší úroveň dereference, může potenciálně přístup k tabulce importovaných adres ukazatel na proměnnou – není proměnné. Tento typ problému můžete často manifest jako narušení přístupu, protože tabulku importních adres je aktuálně jen pro čtení k kompilátoru a linkeru.  
  
 Aktuální linkeru jazyka Visual C++ vydá upozornění, pokud nalezne CONSTANT v souboru .def k účtu pro tento případ. Pouze skutečný důvod pro použití KONSTANTA je, pokud nemůžete překompilovat některý objekt souboru, kde soubor hlaviček není seznamu **deklarace __declspec(dllimport)** na prototypu.  
  
## <a name="see-also"></a>Viz také  
 [Import do aplikace](../build/importing-into-an-application.md)