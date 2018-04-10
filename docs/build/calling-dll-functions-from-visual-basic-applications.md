---
title: Volání funkcí knihovny DLL z aplikací jazyka Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed99b0ebe41a8f1bc9684638fa74e18556dd51f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Volání funkcí knihovny DLL z aplikací jazyka Visual Basic
Pro aplikace Visual Basic (nebo aplikací v jiných jazycích, jako je například Pascal nebo Fortran) k volání funkce v knihovně DLL C/C++ musí být exportován funkce pomocí správné konvence volání bez jakékoli dekorování názvů kompilátorem.  
  
 `__stdcall`Vytvoří správnou konvenci volání funkce (volaná funkce vyčistí zásobník a parametry se jí předávají zprava doleva), ale název funkce upraví odlišně. Pokud ano, **__declspec(dllexport)** se používá na exportované funkce v knihovně DLL, se exportují upravený název.  
  
 `__stdcall` Dekorování názvů předpony název symbol podtržítko (_) a připojí symbol znaku zavináče (@) následovaný počet bajtů v seznamu argumentů (požadované místo v zásobníku). V důsledku toho, když je funkce deklarována jako:  
  
```  
int __stdcall func (int a, double b)  
```  
  
 je upravena následovně:  
  
```  
_func@12  
```  
  
 Konvence volání jazyka C (`__cdecl`) upraví název jako `_func`.  
  
 Chcete-li získat upravený název, použijte [/MAP](../build/reference/map-generate-mapfile.md). Použití **__declspec(dllexport)** provede následující akce:  
  
-   Pokud je funkce exportovaný s konvence volání jazyka C (**_cdecl**), odstraní vedoucí znak podtržítko (_), při exportu název.  
  
-   Pokud funkce, která je exportována nepoužívá konvence volání jazyka C (například `__stdcall`), exportuje upravený název.  
  
 Protože neexistuje žádný způsob, jak přepsat, kde dojde k vyčištění zásobníku, je nutné použít `__stdcall`. Chcete-li odstaranit úpravy názvů pomocí `__stdcall`, je nutné je zadat pomocí aliasů v části Export souboru .def. Tuto situaci znázorňuje takto na deklaraci následující funkce:  
  
```  
int  __stdcall MyFunc (int a, double b);  
void __stdcall InitCode (void);  
```  
  
 V. DEF soubor:  
  
```  
EXPORTS  
   MYFUNC=_MyFunc@12  
   INITCODE=_InitCode@0  
```  
  
 Pro knihovny DLL, která se má volat programy, které jsou napsané v jazyce Visual Basic je v souboru .def potřeba alias techniku, uvedené v tomto tématu. Pokud alias se provádí v programu jazyka Visual Basic, použití v souboru .def není nutné. Toto můžete provést, v programu jazyka Visual Basic přidáte klauzuli alias k [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) příkaz.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Export z knihovny DLL](../build/exporting-from-a-dll.md)  
  
-   [Export z knihovny DLL pomocí. DEF soubory](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Export z knihovny DLL pomocí deklarace __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Výběr použité metody exportu používat](../build/determining-which-exporting-method-to-use.md)  
  
-   [Dekorované názvy](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)