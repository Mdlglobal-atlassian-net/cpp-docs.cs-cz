---
title: Další nástroje pro sestavení MSVC
ms.date: 08/28/2019
f1_keywords:
- c.build
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
ms.openlocfilehash: 53c7c2f8c162cd851b4612e75ba14b019d9cbd63
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177292"
---
# <a name="additional-msvc-build-tools"></a>Další nástroje pro sestavení MSVC

Visual Studio poskytuje následující nástroje příkazového řádku pro zobrazení nebo manipulaci s výstupem sestavení:

- [Lib. EXE](lib-reference.md) slouží k vytvoření a správě knihovny souborů objektů formátu COFF (Common Object File Format). Dá se použít i k vytvoření souborů exportu a importu knihoven pro odkazování na exportované definice.

- [Nástroje Editbin. EXE](editbin-reference.md) slouží k úpravě binárních souborů COFF.

- [DUMPBIN. EXE](dumpbin-reference.md) zobrazuje informace o binárních souborech COFF (například tabulka symbolů).

- [NMAKE](nmake-reference.md) čte a spouští soubory pravidel.

- [ERRLOOK](value-edit-control.md), nástroj pro vyhledávání chyb, načte chybovou zprávu systému nebo chybovou zprávu modulu na základě zadané hodnoty.

- [Xdcmake](xdcmake-reference.md). Nástroj pro zpracování souborů zdrojového kódu, které obsahují komentáře k dokumentaci označené značkami XML.

- [BSCMAKE. EXE](bscmake-reference.md) (poskytuje se jenom pro zpětnou kompatibilitu) vytvoří soubor s informacemi o procházení (. BSC), který obsahuje informace o symbolech (třídy, funkce, data, makra a typy) v programu. Tyto informace si zobrazíte v oknech Procházet ve vývojovém prostředí. (Soubor. BSC se dá sestavit taky ve vývojovém prostředí.)

Windows SDK má také několik nástrojů sestavení, včetně [RC. EXE](/windows/win32/menurc/resource-compiler), který C++ kompilátor vyvolá k kompilování nativních prostředků Windows, jako jsou dialogy, stránky vlastností, bitmapy, tabulky řetězců a tak dále.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)<br/>
[Dekorované názvy](decorated-names.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
