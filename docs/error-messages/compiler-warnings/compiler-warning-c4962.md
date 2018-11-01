---
title: Upozornění kompilátoru C4962
ms.date: 11/04/2016
f1_keywords:
- C4962
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
ms.openlocfilehash: e3f7b715da3774d8289fdd526cf1fa0b5bdddba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585312"
---
# <a name="compiler-warning-c4962"></a>Upozornění kompilátoru C4962

"function': profilováním řízené optimalizace zakázány, protože optimalizace způsobily nekonzistenci dat profilu"

Funkce se nezkompilovalo s /LTCG:PGO, protože údaje o počtu (profil) pro tuto funkci nespolehlivá. Znovu provést profilování se znova vygenerovat soubor .pgc, který obsahuje data nespolehlivé profilu pro tuto funkci.

Toto upozornění je vypnuto ve výchozím nastavení. Další informace najdete v tématu [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).