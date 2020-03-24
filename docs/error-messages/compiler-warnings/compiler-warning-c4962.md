---
title: Upozornění kompilátoru C4962
ms.date: 11/04/2016
f1_keywords:
- C4962
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
ms.openlocfilehash: a600c1875040e1076978bb80c467e6232303cd82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164843"
---
# <a name="compiler-warning-c4962"></a>Upozornění kompilátoru C4962

' function ': optimalizace na základě profilu jsou zakázané, protože optimalizace způsobily nekonzistenci dat profilu. "

Funkce nebyla zkompilována s/LTCG: PGO, protože data Count (Profile) pro tuto funkci byla nespolehlivá. Znovu vytvořte profilování pro opětovné vygenerování souboru. pgc, který obsahuje data nespolehlivého profilu pro tuto funkci.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
