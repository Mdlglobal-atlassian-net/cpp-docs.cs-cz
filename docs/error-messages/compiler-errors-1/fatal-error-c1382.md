---
title: Závažná chyba C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 2b7f6fd878f0d0ba6cde19a3a316a01c390e954a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600600"
---
# <a name="fatal-error-c1382"></a>Závažná chyba C1382

soubor PCH 'file' byla znovu sestavena od 'obj' byla vygenerována. Změňte prosím tento objekt

Při použití [parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil souboru .pch, která je novější než soubor CIL se NAČTE .obj, odkazující na ni. Informace v souboru .obj soubor CIL se NAČTE je zastaralá. Znovu sestavte objekt.

C1382 může také dojít, pokud kompilujete s **/Yc**, ale také předat více zdrojových souborů s kódem pro kompilátor.  Pokud chcete vyřešit, nepoužívejte **/Yc** při předávání více zdrojových souborů s kódem pro kompilátor.  Další informace najdete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md).