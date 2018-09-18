---
title: Chyba matematické operace M6108 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1624a89b472733b4adb5563c8ba52e0b03dcaa2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048614"
---
# <a name="math-error-m6108"></a>Chyba matematické operace M6108

Druhá odmocnina

Operand v rámci operace druhou odmocninu byla záporná.

Program se ukončí s ukončovacím kódem 136.

> [!NOTE]
>  `sqrt` Funkce knihovny run-time jazyka C a vnitřní funkce až po FORTRAN **SQRT** negenerují k této chybě. C `sqrt` funkce zkontroluje argument před provedením operace a vrací chybovou hodnotu, pokud operand je záporný. FORTRAN **SQRT** funkce generuje chybu domény [operace M6201](../../error-messages/tool-errors/math-error-m6201.md) místo této chyby.