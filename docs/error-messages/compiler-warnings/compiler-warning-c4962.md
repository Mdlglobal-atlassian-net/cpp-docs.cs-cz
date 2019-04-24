---
title: Upozornění kompilátoru C4962
ms.date: 11/04/2016
f1_keywords:
- C4962
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
ms.openlocfilehash: e3f7b715da3774d8289fdd526cf1fa0b5bdddba6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280799"
---
# <a name="compiler-warning-c4962"></a>Upozornění kompilátoru C4962

'function': Profilováním řízené optimalizace zakázány, protože optimalizace způsobily nekonzistenci dat profilu"

Funkce se nezkompilovalo s /LTCG:PGO, protože údaje o počtu (profil) pro tuto funkci nespolehlivá. Znovu provést profilování se znova vygenerovat soubor .pgc, který obsahuje data nespolehlivé profilu pro tuto funkci.

Toto upozornění je vypnuto ve výchozím nastavení. Další informace najdete v tématu [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).