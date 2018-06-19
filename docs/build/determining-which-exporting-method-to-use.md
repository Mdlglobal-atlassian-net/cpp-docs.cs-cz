---
title: Výběr použité metody exportu pro použití | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03c88cee3504d8efef8f9ca19073ed06b66f6aeb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368756"
---
# <a name="determining-which-exporting-method-to-use"></a>Výběr použité metody exportu
Můžete exportovat funkce v některém ze dvou způsobů – soubor .def nebo `__declspec(dllexport)` – klíčové slovo. Chcete-li vám pomohou rozhodnout, který způsob je lepší pro vaši knihovnu DLL, zvažte tyto otázky:  
  
-   Máte v úmyslu další funkce exportu později?  
  
-   Je vaše knihovna DLL používat jenom aplikace, které se používá aplikace, které nelze znovu sestavit nebo můžete znovu sestavit – například aplikace, které jsou vytvořené pomocí třetích stran?  
  
## <a name="pros-and-cons-of-using-def-files"></a>Výhody a nevýhody pomocí souborů .def  
 Export funkcí v souboru umožňuje .def, ovládat řadové číslovky export. Když přidáte exportované funkce knihovny DLL, můžete ho přiřadit pořadí vyšší hodnotu než jiných exportovaných funkcí. Když to uděláte, aplikace, které používají implicitní propojení není nutné znovu propojit s knihovnou importu, který obsahuje nové funkce. To je velmi vhodné, pokud navrhujete knihovnu DLL pro použití mnoha aplikacemi protože můžete přidat další nové funkce a ujistěte se také, zda je nadále fungovat správně s aplikacemi, které už na ni tedy spoléhat. Například knihovny MFC DLL jsou vytvořeny pomocí souborů .def.  
  
 Další výhodou použití souboru .def je, že můžete použít `NONAME` atribut export funkce. To vloží pouze řadová číslovka exportní tabulka v knihovně DLL. Pro knihovny DLL, které mají velký počet exportovaných funkcí, pomocí `NONAME` atributu můžete snížit velikost souboru DLL. Informace o tom, jak psát příkazů definice modulu najdete v tématu [pravidla pro příkazy definice modulu](../build/reference/rules-for-module-definition-statements.md). Informace o pořadí export najdete v tématu [export funkcí z knihovny DLL podle pořadí, nikoli podle názvu](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
 Nevýhodou pomocí souborů .def je, že pokud exportujete funkce v souboru C++, můžete buď mít se umístí .def dekorované názvy souborů nebo definujte exportovaných funkcí používání příkazu extern "C", aby se zabránilo dekorování názvů, který se má provést ve Visual C++ compiler.  
  
 Když vložíte dekorované názvy souboru .def, můžete je získat pomocí [DUMPBIN](../build/reference/dumpbin-reference.md) nástroje nebo pomocí linkeru [/MAP](../build/reference/map-generate-mapfile.md) možnost. Dekorované názvy, které vytváří kompilátorem jsou specifické pro kompilátoru; Proto když vložíte dekorované názvy, které jsou vytvářeny v kompilátoru do souboru .def, aplikací, které odkazují na knihovnu DLL musí také sestavit pomocí stejnou verzi kompilátoru tak, aby odpovídaly exportovaný dekorované názvy ve volání aplikace názvy i n .def soubor knihovny DLL.  
  
## <a name="pros-and-cons-of-using-declspecdllexport"></a>Výhody a nevýhody pomocí deklarace __declspec(dllexport)  
 Pomocí `__declspec(dllexport)` je vhodné, protože není nutné udržovat soubor .def a získávat dekorované názvy exportovaných funkcí. Ale užitečnost tímto způsobem exportu je omezen počet propojených aplikací, které chcete znovu sestavit. Pokud je znovu sestavit knihovnu DLL s novými exporty, máte také znovu sestavit aplikace, protože dekorované názvy pro exportované funkce C++ mohou změnit, pokud používáte jinou verzi kompilátor znovu sestavit.  
  
### <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Export z knihovny DLL pomocí. DEF soubory](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Export z knihovny DLL pomocí deklarace __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Export a import pomocí třídy AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo jazyka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Import do aplikace pomocí deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Import a export vložených funkcí](../build/importing-and-exporting-inline-functions.md)  
  
-   [Vzájemné importy](../build/mutual-imports.md)  
  
-   [Dekorované názvy](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>Viz také  
 [Export z knihovny DLL](../build/exporting-from-a-dll.md)