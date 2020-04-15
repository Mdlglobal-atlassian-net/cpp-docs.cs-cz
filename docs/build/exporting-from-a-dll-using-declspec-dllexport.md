---
title: Export z knihovny DLL pomocí deklarace __declspec(dllexport)
ms.date: 05/06/2019
f1_keywords:
- dllexport
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 075962758773660085ae0b98b668c264524cc6aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328585"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>Export z knihovny DLL pomocí deklarace __declspec(dllexport)

Data, funkce, třídy nebo členské funkce třídy můžete exportovat z dll pomocí klíčového slova **__declspec(dllexport).** **__declspec(dllexport)** přidá direktivu exportu do souboru objektu, takže není nutné používat soubor DEF.

Toto pohodlí je nejvíce zřejmé při pokusu o export dekorované názvy funkcí jazyka C++. Vzhledem k tomu, že neexistuje žádná standardní specifikace pro dekoraci názvu, název exportované funkce se může změnit mezi verzemi kompilátoru. Pokud používáte **__declspec(dllexport)**, je změna souboru DLL a závislých souborů EXE nutná pouze k zohlednění všech změn konvencí pojmenování.

Mnoho exportních směrnic, jako jsou řadové číslovky, NONAME a PRIVATE, lze provést pouze v souboru DEF a neexistuje žádný způsob, jak zadat tyto atributy bez souboru DEF. Použití **__declspec(dllexport)** kromě použití souboru .def však nezpůsobí chyby sestavení.

Chcete-li exportovat funkce, musí se klíčové slovo **__declspec(dllexport)** zobrazit vlevo od klíčového slova konvence volání, pokud je zadáno klíčové slovo. Příklad:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Chcete-li exportovat všechny členy veřejných dat a členské funkce ve třídě, musí být klíčové slovo zobrazeno vlevo od názvu třídy takto:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`nelze použít na funkci `__clrcall` s konvencí volání.

Při vytváření dll, obvykle vytvořit soubor záhlaví, který obsahuje prototypy funkce nebo třídy, které exportujete a přidat **__declspec(dllexport)** do deklarací v souboru záhlaví. Chcete-li, aby byl kód čitelnější, definujte makro pro **__declspec(dllexport)** a použijte makro s každým exportujícím symbolem:

```
#define DllExport   __declspec( dllexport )
```

**__declspec(dllexport)** ukládá názvy funkcí v tabulce exportu dll. Pokud chcete optimalizovat velikost tabulky, přečtěte si část [Export funkcí z dll podle ordinální místo podle názvu](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z dll pomocí souborů .def](exporting-from-a-dll-using-def-files.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí Jazyka C pro použití ve spustitelných souborech jazyka C nebo C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializovat dll](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>O čem chcete vědět více?

- [Klíčové slovo __declspec](../cpp/declspec.md)

- [Import a export vřádkových funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné dovozy](mutual-imports.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](exporting-from-a-dll.md)
