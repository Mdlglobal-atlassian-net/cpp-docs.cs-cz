---
title: C++sestavení pro vydání – Visual Studio
ms.date: 12/10/2018
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 46ae5e0f3d545f0e3e004f612314ab416b270fd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168821"
---
# <a name="release-builds"></a>Sestavení pro vydání

Sestavení pro vydání používá optimalizace. Použijete-li optimalizace k vytvoření sestavení pro vydání, kompilátor nebude vytvářet symbolické informace o ladění. Absence symbolických ladicích informací spolu se skutečností, že kód není generován pro volání TRACE a ASSERT, znamená, že velikost spustitelného souboru je zmenšena a bude proto rychlejší.

## <a name="in-this-section"></a>V tomto oddílu

[Běžné problémy při vytváření sestavení pro vydání](common-problems-when-creating-a-release-build.md)<br/>
[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)<br/>
[Použití příkazu VERIFY místo ASSERT](using-verify-instead-of-assert.md)<br/>
[Kontrola přepisování paměti použitím ladění sestavení](using-the-debug-build-to-check-for-memory-overwrite.md)<br/>
[Postupy: Ladění sestavení pro vydání](how-to-debug-a-release-build.md)<br/>
[Kontrola přepisů paměti](checking-for-memory-overwrites.md)<br/>
[Optimalizace kódu](optimizing-your-code.md)

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](reference/c-cpp-building-reference.md)
