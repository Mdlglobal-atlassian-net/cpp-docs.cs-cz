---
title: Upozornění kompilátoru C4962 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4962
dev_langs:
- C++
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caff08744497936839e1021cef8fc86e0e8aa7e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066255"
---
# <a name="compiler-warning-c4962"></a>Upozornění kompilátoru C4962

"function': profilováním řízené optimalizace zakázány, protože optimalizace způsobily nekonzistenci dat profilu"

Funkce se nezkompilovalo s /LTCG:PGO, protože údaje o počtu (profil) pro tuto funkci nespolehlivá. Znovu provést profilování se znova vygenerovat soubor .pgc, který obsahuje data nespolehlivé profilu pro tuto funkci.

Toto upozornění je vypnuto ve výchozím nastavení. Další informace najdete v tématu [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).