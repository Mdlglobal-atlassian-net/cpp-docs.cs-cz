---
title: Závažná chyba C1382 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1382
dev_langs:
- C++
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a5a6ce312c5ef886ef25e8de46e6d3376eded2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030642"
---
# <a name="fatal-error-c1382"></a>Závažná chyba C1382

soubor PCH 'file' byla znovu sestavena od 'obj' byla vygenerována. Změňte prosím tento objekt

Při použití [parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil souboru .pch, která je novější než soubor CIL se NAČTE .obj, odkazující na ni. Informace v souboru .obj soubor CIL se NAČTE je zastaralá. Znovu sestavte objekt.

C1382 může také dojít, pokud kompilujete s **/Yc**, ale také předat více zdrojových souborů s kódem pro kompilátor.  Pokud chcete vyřešit, nepoužívejte **/Yc** při předávání více zdrojových souborů s kódem pro kompilátor.  Další informace najdete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md).