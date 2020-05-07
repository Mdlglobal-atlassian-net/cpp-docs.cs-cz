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

Můžete exportovat data, funkce, třídy nebo členské funkce třídy z knihovny DLL pomocí klíčového slova **__declspec (dllexport)** . **__declspec (dllexport)** přidá direktivu export do souboru objektu, takže nemusíte používat soubor. def.

Tato pohodlí je nejužitečnější při pokusu o export dekorací názvů funkcí jazyka C++. Vzhledem k tomu, že neexistuje žádná standardní specifikace pro dekorace názvu, může se název exportované funkce změnit mezi verzemi kompilátoru. Použijete-li **__declspec (dllexport)**, je nutné znovu zkompilovat soubory DLL a závislé. exe pouze pro všechny změny konvence pojmenování.

Mnoho direktiv exportu, jako jsou řadové číslovky, NONAME a PRIVATE, lze vytvořit pouze v souboru. def a neexistuje žádný způsob, jak tyto atributy zadat bez souboru. def. Nicméně použití **__declspec (dllexport)** Kromě použití souboru. def nezpůsobí chyby sestavení.

Chcete-li exportovat funkce, musí být klíčové slovo **__declspec (dllexport)** nalevo od klíčového slova konvence volání, pokud je klíčové slovo zadáno. Příklad:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Chcete-li exportovat všechny veřejné datové členy a členské funkce ve třídě, klíčové slovo se musí nacházet vlevo od názvu třídy následujícím způsobem:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`nelze použít pro funkci s konvencí `__clrcall` volání.

Při sestavování knihovny DLL obvykle vytvoříte hlavičkový soubor, který obsahuje prototypy funkce nebo třídy, které exportujete, a přidáte **__declspec (dllexport)** do deklarací v souboru hlaviček. Chcete-li zvýšit čitelnost kódu, definujte makro pro **__declspec (dllexport)** a použijte makro s každým symbolem, který exportujete:

```
#define DllExport   __declspec( dllexport )
```

**__declspec (dllexport)** ukládá názvy funkcí v exportní tabulce knihovny DLL. Pokud chcete optimalizovat velikost tabulky, přečtěte si téma [Export funkcí z knihovny DLL podle pořadového čísla, nikoli podle názvu](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů. def](exporting-from-a-dll-using-def-files.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializovat knihovnu DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Klíčové slovo __declspec](../cpp/declspec.md)

- [Import a export vložených funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné importy](mutual-imports.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](exporting-from-a-dll.md)
