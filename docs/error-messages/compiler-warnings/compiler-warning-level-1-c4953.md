---
title: Upozornění (úroveň 1) C4953 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e53808d4ad97bad4eccdf81b0a863277f8f7796
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194629"
---
# <a name="compiler-warning-level-1-c4953"></a>Kompilátor upozornění (úroveň 1) C4953

> Inlinee "*funkce*' byl upraven od shromáždění dat profilu data profilu se nepoužívá

Při použití [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil vstupní modul, který byl znovu zkompilovat po `/LTCG:PGINSTRUMENT` a má funkci (*funkce*), který byl upraven a kde existující testovací běhy identifikované fungovat jako kandidátem pro vkládání. Ale v důsledku z rekompilace modulu, funkce nebude kandidátem pro vkládání.

Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, spusťte `/LTCG:PGINSTRUMENT`, znovu všech testů běží a spusťte `/LTCG:PGOPTIMIZE`.

Toto upozornění by měl být nahrazen chybu, pokud `/LTCG:PGOPTIMIZE` nepoužilo.