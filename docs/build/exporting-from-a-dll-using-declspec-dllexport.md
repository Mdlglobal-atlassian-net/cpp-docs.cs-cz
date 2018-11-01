---
title: Export z knihovny DLL pomocí deklarace __declspec(dllexport)
ms.date: 11/04/2016
f1_keywords:
- dllexport
- __declspec
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: effefa2c370634c450b03ed18187769e12e40adf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500383"
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>Export z knihovny DLL pomocí deklarace __declspec(dllexport)

Společnost Microsoft zavedla **__export** ve verzi 16-bit kompilátor Visual C++ za účelem povolení kompilátoru generovat automaticky exportní názvy a umístit je do souboru LIB. Tento .lib soubor pak lze stejně jako statický .lib propojení s knihovnou DLL.

V novějších verzích kompilátoru můžete exportovat data, funkce, třídy nebo členské funkce tříd z knihovny DLL pomocí **__declspec(dllexport)** – klíčové slovo. **__declspec(dllexport)** přidá exportní směrnici do souboru objektu, takže nepotřebujete použít soubor .def.

Tato výhoda je nejviditelnější při pokusu o export dekorovaných názvů funkcí jazyka C++. Protože neexistuje žádná standardní specifikace pro název dekorace, může být název exportované funkce změněn mezi verzemi kompilátoru. Pokud používáte **__declspec(dllexport)**, rekompilace DLL Knihovnu a závislé .exe soubory je potřeba pouze účet pro všechny změny zásady vytváření názvů.

Mnoho exportních směrnic, jako například řadové číslovky, NONAME a PRIVATE, lze provést pouze v .def souborech a neexistuje žádný způsob specifikace těchto atributů bez použití .def souboru. Avšak použití **__declspec(dllexport)** souboru kromě použití .def nezpůsobí chyby sestavení.

Chcete-li exportovat funkce, **__declspec(dllexport)** musí být klíčové slovo nalevo od klíčového slova konvence volání, pokud je klíčové slovo specifikováno. Příklad:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Pokud chcete exportovat všechny veřejné datové členy a členské funkce ve třídě, klíčové slovo musí být uvedena nalevo od názvu třídy následujícím způsobem:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
>  `__declspec(dllexport)` nelze použít pro funkce s `__clrcall` konvence volání.

Při sestavování DLL Knihovny obvykle vytvoříte soubor hlaviček, který obsahuje prototypy funkcí a/nebo třídy se exportováním a přidat **__declspec(dllexport)** do deklarací v souboru hlaviček. Aby byl kód čitelnější, definujte makro pro **__declspec(dllexport)** a použijte makro s každým symbolem, který exportujete:

```
#define DllExport   __declspec( dllexport )
```

**__declspec(dllexport)** uloží názvy funkcí v exportní tabulce knihovny DLL. Pokud chcete optimalizovat velikost tabulky, přečtěte si téma [export funkcí z DLL Knihovny podle pořadí, než podle názvu](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

> [!NOTE]
>  Pokud přenášíte zdrojový kód knihovny DLL z Win16 na Win32, nahraďte každou instanci **__export** s **__declspec(dllexport)**.

Jako odkaz Hledat v souboru hlaviček Win32 Winbase.h. Obsahuje příklady **__declspec(dllimport)** využití.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md)

- [Export a import pomocí AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++ – jazyk](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určit, kterou exportovací metodu použít](../build/determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [__Declspec – klíčové slovo](../cpp/declspec.md)

- [Import a export vložených funkcí](../build/importing-and-exporting-inline-functions.md)

- [Vzájemné importy](../build/mutual-imports.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](../build/exporting-from-a-dll.md)