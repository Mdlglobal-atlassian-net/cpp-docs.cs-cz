---
title: Závažná chyba C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 056db975fecef4e101dbbba7e2084236489498c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202862"
---
# <a name="fatal-error-c1853"></a>Závažná chyba C1853

> soubor předkompilované hlavičky*filename*je z předchozí verze kompilátoru, nebo je C++ Předkompilovaná hlavička a Vy ji používáte z C (nebo naopak).

Možné příčiny:

- Předkompilovaná hlavička byla zkompilována s předchozí verzí kompilátoru. Zkuste znovu zkompilovat hlavičku s aktuálním kompilátorem.

- Předkompilovaná hlavička je C++ a Vy ji používáte z C. zkuste znovu zkompilovat hlavičku pro použití s c tím, že zadáte jednu z možností kompilátoru [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) nebo změníte příponu zdrojového souboru na "C". Další informace naleznete v tématu [dvě možnosti pro předkompilování kódu](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).
