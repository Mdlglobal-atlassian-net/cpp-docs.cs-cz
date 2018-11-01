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
ms.openlocfilehash: f932ba2d9b229d236270eb664ac1291725471706
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493818"
---
# <a name="exporting-from-a-dll"></a>Export z knihovny DLL

Soubor knihovny DLL má velmi podobně jako soubor .exe s jedním z důležitých rozdílů rozložení – soubor DLL obsahuje exportní tabulka. Exportní tabulka obsahuje název každé funkce, které knihovny DLL exportuje do další spustitelné soubory. Tyto funkce jsou vstupními body do knihovny DLL; Další spustitelné soubory je přístupný pouze funkcí v exportní tabulce. Další funkce v knihovně DLL jsou privátní pro knihovnu DLL. V tabulce exportů knihovny DLL lze zobrazit pomocí [DUMPBIN](../build/reference/dumpbin-reference.md) nástroje s možností/EXPORTS.

Export funkcí z knihovny DLL pomocí dvou metod:

- Vytvoření souboru modulu definice (.def) a použijte soubor .def při vytváření knihovny DLL. Tuto metodu použijte, pokud chcete [export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

- Pomocí klíčového slova **__declspec(dllexport)** v definici funkce.

Při exportu funkcí pomocí některé z metod, je nutné použít [__stdcall](../cpp/stdcall.md) konvence volání.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++ – jazyk](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [Určit, kterou exportovací metodu použít](../build/determining-which-exporting-method-to-use.md)

- [Určit, kterou propojovací metodu použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Import do aplikace](../build/importing-into-an-application.md)

- [Import a export vložených funkcí](../build/importing-and-exporting-inline-functions.md)

- [Vzájemné importy](../build/mutual-imports.md)

## <a name="see-also"></a>Viz také

[Import a export](../build/importing-and-exporting.md)