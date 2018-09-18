---
title: Vyhodnocování výrazu CXX0030 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb2921013d116b7d8f02e1e29380ca3cd14086b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102806"
---
# <a name="expression-evaluator-error-cxx0030"></a>Chyba při vyhodnocování výrazu CXX0030

výraz není evaluatable

Chyba při vyhodnocování výrazů ladicího programu nelze získat hodnotu výrazu, jak je uvedená. Pravděpodobnou příčinou je, že výraz odkazuje na paměti, která je mimo Adresní prostor programu (přesměrování ukazatele null je jedním z příkladů). Windows neumožňuje přístup k paměti, která je mimo Adresní prostor virtuálních programu.

Můžete chtít přepsat pomocí závorek k řízení pořadí vyhodnocení výrazu.

Tato chyba se shoduje s CAN0030.