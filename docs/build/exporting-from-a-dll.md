---
title: Export z knihovny DLL
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
ms.openlocfilehash: 6bdf5b86724ae07aa073a9feb1cc4d5723bc6e6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196739"
---
# <a name="exporting-from-a-dll"></a>Export z knihovny DLL

Soubor DLL má rozložení velmi podobné souboru. exe s důležitým rozdílem – soubor DLL obsahuje tabulku EXPORTS. Tabulka EXPORTS obsahuje název každé funkce, kterou knihovna DLL exportuje do jiných spustitelných souborů. Tyto funkce jsou vstupními body do knihovny DLL; pouze funkce v tabulce EXPORTS mohou být k dispozici v jiných spustitelných souborech. Všechny ostatní funkce v knihovně DLL jsou soukromé pro knihovnu DLL. Tabulku EXPORTS knihovny DLL lze zobrazit pomocí nástroje [DUMPBIN](reference/dumpbin-reference.md) s možností/EXPORTS.

Můžete exportovat funkce z knihovny DLL pomocí dvou metod:

- Vytvořte soubor definice modulu (. def) a při sestavování knihovny DLL použijte soubor. def. Tento postup použijte, pokud chcete [exportovat funkce z knihovny DLL podle pořadového čísla, nikoli podle názvu](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

- V definici funkce použijte klíčové slovo **__declspec (dllexport)** .

Při exportování funkcí pomocí obou metod nezapomeňte použít konvenci volání [__stdcall](../cpp/stdcall.md) .

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů. def](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Exportujte funkce z knihovny DLL podle pořadových čísel, nikoli podle názvu.](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [Inicializovat knihovnu DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Import do aplikace](importing-into-an-application.md)

- [Import a export vložených funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné importy](mutual-imports.md)

## <a name="see-also"></a>Viz také

[Import a export](importing-and-exporting.md)
