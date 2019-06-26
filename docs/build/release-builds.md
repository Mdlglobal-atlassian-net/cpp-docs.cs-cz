---
title: Sestavení C++ verze – Visual Studio
ms.date: 12/10/2018
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: b1db396136af4a6ce8cc005753dded9eea2bfbeb
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400471"
---
# <a name="release-builds"></a>Sestavení pro vydání

Sestavení pro vydání používá optimalizace. Při použití optimalizací na vytváření sestavení pro vydání, kompilátor nevytvoří symbolické ladicí informace. Neexistence symbolické ladicí informace, společně s faktem, že kód nebude vygenerován pro TRASOVACÍHO a kontrolní VÝRAZ volá znamená, že velikost spustitelný soubor je omezeno a proto bude rychlejší.

## <a name="in-this-section"></a>V tomto oddílu

[Běžné problémy při vytváření sestavení pro vydání](common-problems-when-creating-a-release-build.md)<br/>
[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)<br/>
[Použití příkazu VERIFY místo ASSERT](using-verify-instead-of-assert.md)<br/>
[Kontrola přepisování paměti použitím ladění sestavení](using-the-debug-build-to-check-for-memory-overwrite.md)<br/>
[Postupy: Ladění sestavení pro vydání](how-to-debug-a-release-build.md)<br/>
[Kontrola přepisů paměti](checking-for-memory-overwrites.md)<br/>
[Optimalizace kódu](optimizing-your-code.md)

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](reference/c-cpp-building-reference.md)