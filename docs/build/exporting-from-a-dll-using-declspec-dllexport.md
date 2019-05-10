---
title: Export z knihovny DLL pomocí deklarace __declspec(dllexport)
ms.date: 05/06/2019
f1_keywords:
- dllexport
- __declspec
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 167060d0270004b8648d32af206865bfe66c3b4b
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220788"
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>Export z knihovny DLL pomocí deklarace __declspec(dllexport)

Můžete exportovat data, funkce, třídy nebo členské funkce tříd z knihovny DLL pomocí **__declspec(dllexport)** – klíčové slovo. **__declspec(dllexport)** přidá exportní směrnici do souboru objektu, takže nepotřebujete použít soubor .def.

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

**__declspec(dllexport)** uloží názvy funkcí v exportní tabulce knihovny DLL. Pokud chcete optimalizovat velikost tabulky, přečtěte si téma [export funkcí z DLL Knihovny podle pořadí, než podle názvu](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů .def](exporting-from-a-dll-using-def-files.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++ – jazyk](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určit, kterou exportovací metodu použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializace knihovny DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [__Declspec – klíčové slovo](../cpp/declspec.md)

- [Import a export vložených funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné importy](mutual-imports.md)

## <a name="see-also"></a>Viz také:

[Export z knihovny DLL](exporting-from-a-dll.md)
