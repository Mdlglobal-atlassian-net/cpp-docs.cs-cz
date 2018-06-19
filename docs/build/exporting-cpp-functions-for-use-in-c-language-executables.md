---
title: Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf5f348675752ff9c0b548693c442812fa6be697
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367583"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C  
  
Pokud máte funkce v knihovně DLL napsané v jazyce C++, ke kterému chcete přistupovat z modulu jazyka C, by měly deklarovat tyto funkce C propojení namísto c++. Pokud není uvedeno jinak, používá kompilátor C++ bezpečnost typů pojmenování (také označované jako dekorování názvů) a konvence volání C++, což může být obtížné volat z C.  
  
Pokud chcete zadat C propojení, zadejte `extern "C"` pro deklarace funkcí. Příklad:  
  
```  
extern "C" __declspec( dllexport ) int MyFunc(long parm1);  
```  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Export z knihovny DLL pomocí deklarace __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Export a import pomocí třídy AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo jazyka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Určení použité metody exportu](../build/determining-which-exporting-method-to-use.md)  
  
-   [Import do aplikace pomocí deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Dekorované názvy](../build/reference/decorated-names.md)  
  
-   [Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)  
  
## <a name="see-also"></a>Viz také  
 [Export z knihovny DLL](../build/exporting-from-a-dll.md)