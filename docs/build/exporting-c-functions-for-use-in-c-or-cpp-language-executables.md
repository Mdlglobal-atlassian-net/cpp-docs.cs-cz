---
title: Export funkcí jazyka C pro použití v jazyka C nebo spustitelných souborech jazyka C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee1d572bbfaa31ac626bfeb2b6ed7f61604628c8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367703"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++  
  
Pokud máte funkce v knihovně DLL napsané v jazyce C, kterému chcete přistupovat z jazyka C nebo modulu jazyka C++, měli byste použít **__cplusplus** makro preprocesoru určit jazyk, který se bude kompilovat a pak tyto deklarace Funkce C propojení, pokud je používán z modulu jazyka C++. Pokud tento postup použít a zadejte soubory hlaviček pro knihovny DLL, lze tyto funkce C a C++ uživatelé beze změny.  
  
Následující kód ukazuje soubor hlaviček, který lze použít v klientských aplikacích C a C++:  
  
```h  
// MyCFuncs.h  
#ifdef __cplusplus  
extern "C" {  // only need to export C interface if  
              // used by C++ source code  
#endif  
  
__declspec( dllimport ) void MyCFunc();  
__declspec( dllimport ) void AnotherCFunc();  
  
#ifdef __cplusplus  
}  
#endif  
```  
  
Budete muset propojit váš C++ spustitelné funkcí jazyka C a soubory hlaviček deklarace funkce nepoužili techniky popsané výše v C++ zdrojový soubor, zabránit architekturu názvy funkcí C kompilátor následujícím postupem:  
  
```cpp  
extern "C" {  
#include "MyCHeader.h"  
}  
```  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Export z knihovny DLL pomocí deklarace __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Export a import pomocí třídy AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Určení použité metody exportu](../build/determining-which-exporting-method-to-use.md)  
  
-   [Import do aplikace pomocí deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Dekorované názvy](../build/reference/decorated-names.md)  
  
-   [Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)  
  
## <a name="see-also"></a>Viz také  
 [Export z knihovny DLL](../build/exporting-from-a-dll.md)