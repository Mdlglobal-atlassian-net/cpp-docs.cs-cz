---
title: Sestavení pro vydání
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 346beace1979871cfd9bf4ee0d487e7f85a26eaa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426092"
---
# <a name="release-builds"></a>Sestavení pro vydání

Sestavení pro vydání používá optimalizace. Při použití optimalizací na vytváření sestavení pro vydání, kompilátor nevytvoří symbolické ladicí informace. Neexistence symbolické ladicí informace, společně s faktem, že kód nebude vygenerován pro TRASOVACÍHO a kontrolní VÝRAZ volá znamená, že velikost spustitelný soubor je omezeno a proto bude rychlejší.

Tato část představuje informace o tom, proč a kdy chcete změnit ze sestavení pro ladění k sestavení pro vydání. Také popisuje některé z problémů, na které můžete narazit při změně z ladění na sestavení pro vydání:

- [Vytváření sestavení pro vydání](../../build/reference/how-to-create-a-release-build.md)

- [Běžné problémy při vytváření sestavení pro vydání](../../build/reference/common-problems-when-creating-a-release-build.md)

- [Oprava problémů se sestavením pro vydání](../../build/reference/fixing-release-build-problems.md)

   - [Zkoumání Assert – příkazy](../../build/reference/using-verify-instead-of-assert.md)

   - [Přepisování paměti použitím ladění sestavení ke kontrole](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)

   - [Ladění sestavení pro vydání](../../build/reference/how-to-debug-a-release-build.md)

   - [Kontrola přepisů paměti](../../build/reference/checking-for-memory-overwrites.md)

## <a name="see-also"></a>Viz také:

[Sestavení projektů C++ v sadě Visual Studio](../../ide/building-cpp-projects-in-visual-studio.md)<br/>
[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)
