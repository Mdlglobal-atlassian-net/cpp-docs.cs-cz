---
title: "Export z knihovny DLL pomocí deklarace __declspec(dllexport) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- dllexport
- __declspec
dev_langs: C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51f20e47724a6d32dad014fbaf025cd283112c54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>Export z knihovny DLL pomocí deklarace __declspec(dllexport)
Microsoft zavedená **__export** v kompilátoru 16bitové verzi Visual C++ pro povolení kompilátoru automaticky generovat názvy exportu a umístit je soubor LIB. Tento soubor .lib pak lze stejně jako statické .lib propojit s knihovny DLL.  
  
 V novější verzi kompilátoru, můžete exportovat data, funkce, třídy nebo členské funkce třídy z knihovny DLL pomocí **__declspec(dllexport)** – klíčové slovo. **__declspec(dllexport)** , není potřeba použít soubor .def přidá – direktiva export do souboru objektu.  
  
 Tato výhoda jde nejvíce poznat, při pokusu o export dekorované názvy funkcí jazyka C++. Protože neexistuje žádná standardní specifikace pro dekorování názvů, může mezi verzemi kompilátoru změnit název exportované funkce. Pokud používáte **__declspec(dllexport)**, nutnosti rekompilace DLL a závislé .exe soubory je nezbytné pouze k účtu pro všechny změny zásady vytváření názvů.  
  
 Mnoho exportovat direktivy, například řadové číslovky, NONAME a PRIVÁTNÍ, můžete provést pouze v souboru .def a neexistuje žádný způsob, jak určit tyto atributy bez souboru .def. Však pomocí **__declspec(dllexport)** kromě používání .def souboru nezpůsobí chyby sestavení.  
  
 Export funkcí, **__declspec(dllexport)** musí být klíčové slovo nalevo od konvence volání klíčové slovo, pokud je zadané klíčové slovo. Příklad:  
  
```  
__declspec(dllexport) void __cdecl Function1(void);  
```  
  
 Pokud chcete exportovat všechny členy veřejná data a členské funkce ve třídě, klíčové slovo musí zobrazit nalevo od názvu třídy takto:  
  
```  
class __declspec(dllexport) CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
> [!NOTE]
>  `__declspec(dllexport)`nelze použít pro funkci s `__clrcall` konvence volání.  
  
 Při vytváření knihovny DLL, obvykle vytvoříte soubor hlaviček, který obsahuje prototypy funkcí nebo třídy, které jste exportovali a přidat **__declspec(dllexport)** deklaracích v záhlaví souboru. Aby byl váš kód čitelnější, definujte makro pro **__declspec(dllexport)** a použijte makro každý symbolem exportujete:  
  
```  
#define DllExport   __declspec( dllexport )   
```  
  
 **__declspec(dllexport)** úložiště funkce názvy v tabulce export knihovny DLL. Pokud chcete optimalizovat velikost tabulky, přečtěte si téma [export funkcí z knihovny DLL podle pořadí, než podle názvu](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
> [!NOTE]
>  Když portování zdrojový kód knihovny DLL z Win16 do Win32, nahraďte každý výskyt položky **__export** s **__declspec(dllexport)**.  
  
 Jako odkaz hledání v souboru hlaviček Win32 Winbase.h. Obsahuje příklady **deklarace __declspec(dllimport)** využití.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Export a import pomocí třídy AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo jazyka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Určení použité metody exportu](../build/determining-which-exporting-method-to-use.md)  
  
-   [Import do aplikace pomocí deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [__Declspec – klíčové slovo](../cpp/declspec.md)  
  
-   [Import a export vložených funkcí](../build/importing-and-exporting-inline-functions.md)  
  
-   [Vzájemné importy](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Viz také  
 [Export z knihovny DLL](../build/exporting-from-a-dll.md)