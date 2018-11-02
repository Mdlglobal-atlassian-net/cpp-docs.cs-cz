---
title: Chyba při vyhodnocování výrazu CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 1e52b238905fba5c310a89377b81548a1c6b5784
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500344"
---
# <a name="expression-evaluator-error-cxx0030"></a>Chyba při vyhodnocování výrazu CXX0030

výraz není evaluatable

Chyba při vyhodnocování výrazů ladicího programu nelze získat hodnotu výrazu, jak je uvedená. Pravděpodobnou příčinou je, že výraz odkazuje na paměti, která je mimo Adresní prostor programu (přesměrování ukazatele null je jedním z příkladů). Windows neumožňuje přístup k paměti, která je mimo Adresní prostor virtuálních programu.

Můžete chtít přepsat pomocí závorek k řízení pořadí vyhodnocení výrazu.

Tato chyba se shoduje s CAN0030.