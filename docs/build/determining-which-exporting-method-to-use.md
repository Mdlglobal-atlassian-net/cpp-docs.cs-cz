---
title: Určit, kterou exportovací metodu použít
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
ms.openlocfilehash: 974c32cef87801599ba0d14fd146e84ad874467f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816292"
---
# <a name="determine-which-exporting-method-to-use"></a>Určit, kterou exportovací metodu použít

Můžete exportovat funkce v některém ze dvou způsobů – soubor .def nebo `__declspec(dllexport)` – klíčové slovo. Chcete-li pomoci při rozhodování, jakým způsobem je lepší pro vaši knihovnu DLL, zvažte tyto otázky:

- Chystáte se exportovat později další funkce?

- Je vaše knihovna DLL použita pouze u aplikací, které můžete znovu sestavit nebo se používá u aplikací, které nelze znovu sestavit, například aplikace, které jsou vytvořené třetími stranami?

## <a name="pros-and-cons-of-using-def-files"></a>Výhody a nevýhody pomocí souborů .def

Export funkcí v .def souboru získáte tak kontrolu nad řadové číslovky exportu. Když přidáte exportované funkce knihovny DLL, ji můžete přiřadit ordinální vyšší hodnotu než ostatní exportované funkce. Když toto provedete, není potřeba znovu propojit s importovanou knihovnou, která obsahuje nové funkce aplikace, které používají implicitní propojení. To je velmi vhodné, pokud navrhujete knihovny DLL pro použití mnoha aplikacemi vzhledem k tomu, že můžete přidat nové funkce a také se ujistěte, že i nadále fungovat správně s aplikacemi, které už jsou na něm závislí. Například knihovny DLL MFC jsou vytvořeny pomocí souborů .def.

Další výhodou použití .def souboru je, že můžete použít `NONAME` atribut exportovat funkce. To umístí pouze pořadí v tabulce exportů v knihovně DLL. Pro knihovny DLL, které mají velký počet exportovaných funkcí pomocí `NONAME` atribut můžete zmenšit velikost souboru knihovny DLL. Informace o tom, jak psát modulu definice příkazu najdete v tématu [pravidla pro příkazy definice modulu](reference/rules-for-module-definition-statements.md). Informace o ordinální export najdete v tématu [export funkcí z DLL Knihovny podle řádu, než podle názvu](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

Pomocí souboru .def nevýhodou je, že pokud exportujete funkce v souboru jazyka C++, je buď potřeba umístit .def dekorované názvy souborů nebo definovat exportované funkce tak, že používání příkazu extern "C", aby názvovou dekoraci, která se má provést kompilátorem MSVC.

Když vložíte do .def souboru dekorované názvy, můžete je získat pomocí [DUMPBIN](reference/dumpbin-reference.md) nástroj nebo pomocí volby propojovacího programu [/MAP](reference/map-generate-mapfile.md) možnost. Dekorované názvy, které jsou produkované kompilátorem jsou specifické pro kompilátor; Proto pokud umístíte dekorované názvy, které jsou vytvářeny pomocí kompilátoru do souboru .def, aplikace, které na knihovnu DLL musí také být sestaveny pomocí stejné verze kompilátoru tak, aby dekorované názvy ve volání aplikace odpovídaly exportovaný názvy i n souboru .def knihovny DLL.

## <a name="pros-and-cons-of-using-declspecdllexport"></a>Výhody a nevýhody pomocí deklarace __declspec(dllexport)

Pomocí `__declspec(dllexport)` je pohodlné, protože není nutné se starat o údržbu souboru .def a získání dekorované názvy exportovaných funkcí. Užitečnost tímto způsobem exportu je však omezen počet propojených aplikací, které jste ochotni znovu sestavit. Pokud je znovu sestavit knihovnu DLL s novými exporty, máte také znovu sestavit aplikace, protože dekorované názvy pro exportované funkce jazyka C++ může změnit, pokud používáte jinou verzi kompilátoru její opětovné sestavení.

### <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí. DEF soubory](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++ – jazyk](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializace knihovny DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Import a export vložených funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné importy](mutual-imports.md)

- [Dekorované názvy](reference/decorated-names.md)

## <a name="see-also"></a>Viz také:

[Export z knihovny DLL](exporting-from-a-dll.md)
