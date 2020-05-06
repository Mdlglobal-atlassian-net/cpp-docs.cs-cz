---
title: Výběr použité metody exportu
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
ms.openlocfilehash: 974c32cef87801599ba0d14fd146e84ad874467f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273734"
---
# <a name="determine-which-exporting-method-to-use"></a>Výběr použité metody exportu

Funkce můžete exportovat jedním ze dvou způsobů – souboru. def nebo `__declspec(dllexport)` klíčovým slovem. Pro snazší rozhodování o tom, jaký je lepší pro vaši knihovnu DLL, zvažte tyto otázky:

- Plánujete export dalších funkcí později?

- Je vaše knihovna DLL používána pouze aplikacemi, které lze znovu sestavit, nebo je používá aplikace, které nelze znovu sestavit – například aplikace, které jsou vytvořeny třetími stranami?

## <a name="pros-and-cons-of-using-def-files"></a>Specialisté a nevýhody používání souborů. def

Exportování funkcí v souboru. def vám umožní řídit pořadí exportu. Když do své knihovny DLL přidáte exportovanou funkci, můžete jí přiřadit vyšší pořadové číslo než jakákoli jiná exportovaná funkce. Když to uděláte, aplikace, které používají implicitní propojení, se nemusí znovu propojit s knihovnou import, která obsahuje novou funkci. To je velmi užitečné, pokud navrhujete knihovnu DLL pro použití v mnoha aplikacích, protože můžete přidat nové funkce a také zajistit, aby i nadále fungovaly správně s aplikacemi, které už na ně spoléhají. Například knihovny MFC DLL jsou sestaveny pomocí souborů. def.

Další výhodou použití souboru. def je, že můžete použít `NONAME` atribut k exportu funkce. Tím se v knihovně DLL vloží pouze ordinální číslo v tabulce EXPORTS. V případě knihoven DLL, které mají velký počet exportovaných funkcí, `NONAME` lze pomocí atributu zmenšit velikost souboru DLL. Informace o tom, jak napsat příkaz definice modulu, najdete v tématu [pravidla pro příkazy definice modulu](reference/rules-for-module-definition-statements.md). Informace o ordinálním exportu naleznete v tématu [Export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

Nevýhodou použití souboru. def je, že pokud exportujete funkce v souboru jazyka C++, je buď nutné umístit dekorované názvy do souboru. def, nebo definovat exportované funkce pomocí extern "C", abyste se vyhnuli dekorování názvů, které provádí kompilátor MSVC.

Pokud vložíte dekorované názvy do souboru. def, můžete je získat pomocí nástroje [DUMPBIN](reference/dumpbin-reference.md) nebo pomocí možnosti linker [/map](reference/map-generate-mapfile.md) . Dekorované názvy, které jsou vytvořeny kompilátorem, jsou specifické pro kompilátor; Proto pokud vložíte dekorované názvy, které jsou vyprodukovány kompilátorem, do souboru. def, aplikace, které odkazují na knihovnu DLL, musí být také sestaveny pomocí stejné verze kompilátoru, aby dekorované názvy v volající aplikaci odpovídaly exportovaným názvům v souboru. def knihovny DLL.

## <a name="pros-and-cons-of-using-__declspecdllexport"></a>Specialisté a nevýhody použití __declspec (dllexport)

Použití `__declspec(dllexport)` je pohodlné, protože se nemusíte starat o údržbu souboru. def a získat dekorované názvy exportovaných funkcí. Nicméně užitečnost tohoto způsobu exportu je omezená počtem propojených aplikací, které jste ochotni znovu sestavit. Při opětovném sestavení knihovny DLL s novými exporty je také nutné znovu sestavit aplikace, protože dekorované názvy pro exportované funkce jazyka C++ mohou být změněny, pokud použijete jinou verzi kompilátoru pro opětovné sestavení.

### <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Exportujte z knihovny DLL pomocí. Soubory DEF](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializovat knihovnu DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Import a export vložených funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné importy](mutual-imports.md)

- [Dekorované názvy](reference/decorated-names.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](exporting-from-a-dll.md)
