---
title: Závažná chyba C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: ec2d6bf6bac46cca8bdc2e3b8fe7cc6b7799d78a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820725"
---
# <a name="fatal-error-c1853"></a>Závažná chyba C1853

> "*filename*" soubor předkompilované hlavičky je z předchozí verze kompilátoru, nebo předkompilované hlavičky je C++ a vy ji používáte z C (nebo naopak)

Možné příčiny:

- Předkompilované hlavičky byl zkompilován pomocí předchozí verze kompilátoru. Zkuste rekompilace záhlaví s aktuální kompilátorem.

- Předkompilovaná hlavička v C++ a vy ji používáte z c zkuste rekompilace zadáním jedné z hlaviček pro použití s C [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) – možnosti kompilátoru, nebo změnit příponu souboru zdroje na "c". Další informace najdete v tématu [dvě možnosti pro předkompilaci kódu](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).