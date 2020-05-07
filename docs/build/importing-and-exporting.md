---
title: Import a export
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 03931f7f128ab0666890bb8e76677db67dda8fc7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220637"
---
# <a name="importing-and-exporting"></a>Import a export

Můžete importovat veřejné symboly do aplikace nebo exportovat funkce z knihovny DLL pomocí dvou metod:

- Při sestavování knihovny DLL použít soubor definice modulu (. def)

- Použijte klíčová slova **__declspec (dllimport)** nebo **__declspec (dllexport)** v definici funkce v hlavní aplikaci.

## <a name="using-a-def-file"></a>Použití souboru. def

Soubor definice modulu (. def) je textový soubor obsahující jeden nebo více příkazů modulu, které popisují různé atributy knihovny DLL. Pokud nepoužíváte **__declspec (dllimport)** nebo **__declspec (dllexport)** k exportu funkcí knihovny DLL, knihovna DLL vyžaduje soubor. def.

Soubory. def můžete použít pro [Import do aplikace](importing-using-def-files.md) nebo pro [Export z knihovny DLL](exporting-from-a-dll-using-def-files.md).

## <a name="using-__declspec"></a>Použití __declspec

Pro správné kompilování kódu není nutné použít **__declspec (dllimport)** , ale v takovém případě umožňuje kompilátoru generovat lepší kód. Kompilátor je schopen generovat lepší kód, protože může určit, zda funkce existuje v knihovně DLL, nebo ne, což umožňuje kompilátoru vytvořit kód, který přeskočí úroveň dereference, která by obvykle existovala ve volání funkce, které překračuje hranice knihovny DLL. Je však nutné použít **__declspec (dllimport)** pro import proměnných používaných v knihovně DLL.

Se správným oddílem pro EXPORTy souborů. def není **__declspec (dllexport)** vyžadován. byl přidán **__declspec (dllexport)** , který poskytuje snadný způsob exportu funkcí ze souboru. exe nebo. dll bez použití souboru. def.

Formát přenositelného spustitelného souboru Win32 je navržený tak, aby minimalizoval počet stránek, které je potřeba napravit při opravě importu. Chcete-li to provést, umístí všechny adresy pro import každého programu na jednom místě, které se nazývá tabulka importních adres. To umožňuje zavaděči při přístupu k těmto importům upravovat pouze jednu nebo dvě stránky.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Import do aplikace](importing-into-an-application-using-declspec-dllimport.md)

- [Export z knihovny DLL](exporting-from-a-dll.md)

## <a name="see-also"></a>Viz také

[Vytváření knihoven DLL jazyka C/C++ v aplikaci Visual Studio](dlls-in-visual-cpp.md)
