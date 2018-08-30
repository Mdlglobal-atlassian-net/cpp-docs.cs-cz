---
title: Upozornění (úroveň 1) C4952 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4952
dev_langs:
- C++
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f62f4c18380d89eb516a5fa49ef63e92ab79a6f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207148"
---
# <a name="compiler-warning-level-1-c4952"></a>Kompilátor upozornění (úroveň 1) C4952

> "*funkce*': nenašla se žádná data profilu v databázi programu"*pgd_file*.

Při použití [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil vstupní modul, který byl znovu zkompilovat po `/LTCG:PGINSTRUMENT` a obsahuje novou funkci (*funkce*) k dispozici.

Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, spusťte `/LTCG:PGINSTRUMENT`, znovu všech testů běží a spusťte `/LTCG:PGOPTIMIZE`.

Toto upozornění by měl být nahrazen chybu, pokud `/LTCG:PGOPTIMIZE` nepoužilo.