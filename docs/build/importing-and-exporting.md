---
title: Import a export | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc07ba1de15795e99a5e2ed75a5df9752026d08e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716999"
---
# <a name="importing-and-exporting"></a>Import a export

Chcete-li import veřejných symbolů do aplikace nebo export funkcí z knihovny DLL pomocí dvou metod:

- Při sestavování knihovny DLL pomocí souboru modulu definice (.def)

- Pomocí klíčových slov **__declspec(dllimport)** nebo **__declspec(dllexport)** v definici funkce v hlavní aplikaci

## <a name="using-a-def-file"></a>Pomocí souboru .def

Soubor definice modulu (.def) je textový soubor obsahující jeden nebo více příkazů modulu, které popisují různé atributy knihovny DLL. Pokud nepoužijete **__declspec(dllimport)** nebo **__declspec(dllexport)** pro export funkcí knihovny DLL, pak vyžaduje knihovna DLL .def souboru.

Pomocí souborů .def k [import do aplikace](../build/importing-using-def-files.md) nebo [export z knihovny DLL](../build/exporting-from-a-dll-using-def-files.md).

## <a name="using-declspec"></a>Pomocí __declspec

Visual C++ používá **__declspec(dllimport)** a **__declspec(dllexport)** nahradit **__export** – klíčové slovo předtím používal v 16bitovou verzí jazyka Visual C++.

Není potřeba použít **__declspec(dllimport)** váš kód mohl zkompilovat správně, ale to umožňuje kompilátoru generovat lepší kód. Kompilátor je schopen vygenerovat lepší kód, protože ho můžete určit, zda funkce existuje v knihovně DLL nebo Ne, což umožňuje kompilátoru vytvořit kód, který přeskočí určitou úroveň dereference, který bude obvykle k dispozici ve volání funkce, která překračuje hranice knihovny DLL. Nicméně je nutné použít **__declspec(dllimport)** import proměnné používané v knihovně DLL.

Pomocí části správné .def souboru EXPORTŮ **__declspec(dllexport)** se nevyžaduje. **__declspec(dllexport)** byl přidán do poskytují snadný způsob, jak exportovat funkce ze souboru .exe nebo .dll bez použití .def souboru.

Ve formátu přenosného spustitelného souboru Win32 je určená k minimalizaci počtu stránek, které musí být dotčená opravit importy. K tomu, umístí všechny adresy import pro libovolné aplikace na jednom místě názvem tabulky importu adres. To umožňuje upravovat pouze jednu nebo dvě stránky při přístupu k těmto importy zavaděči.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Import do aplikace](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Export z knihovny DLL](../build/exporting-from-a-dll.md)

## <a name="see-also"></a>Viz také

[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)