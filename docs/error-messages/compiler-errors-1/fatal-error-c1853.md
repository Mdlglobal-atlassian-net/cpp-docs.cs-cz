---
title: Závažná chyba C1853 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 016e5bbf064643ddff0f63c5e16a967ed914f3e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044948"
---
# <a name="fatal-error-c1853"></a>Závažná chyba C1853

> "*filename*" soubor předkompilované hlavičky je z předchozí verze kompilátoru, nebo předkompilované hlavičky je C++ a vy ji používáte z C (nebo naopak)

Možné příčiny:

- Předkompilované hlavičky byl zkompilován pomocí předchozí verze kompilátoru. Zkuste rekompilace záhlaví s aktuální kompilátorem.

- Předkompilovaná hlavička v C++ a vy ji používáte z c zkuste rekompilace zadáním jedné z hlaviček pro použití s C [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) – možnosti kompilátoru, nebo změnit příponu souboru zdroje na "c". Další informace najdete v tématu [dvě možnosti pro předkompilaci kódu](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).