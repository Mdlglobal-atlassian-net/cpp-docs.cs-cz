---
title: Vyhodnocování výrazu CXX0025 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0025
dev_langs:
- C++
helpviewer_keywords:
- CAN0025
- CXX0025
ms.assetid: 3e2fb541-63b3-46ac-9f93-3dadb253bcf6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd89faa4de7b296d6a6771f857f3d16dbe2f94f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043700"
---
# <a name="expression-evaluator-error-cxx0025"></a>Chyba při vyhodnocování výrazu CXX0025

operátor musí struktury nebo sjednocení.

Operátor, který přijímá výraz `struct` nebo **sjednocení** typu byla použita ve výrazu, který není `struct` nebo **sjednocení**.

Součástí třídy, struktury nebo sjednocení proměnných musí mít plně kvalifikovaný název. Součásti nelze zadat bez úplnou specifikaci.

Tato chyba se shoduje s CAN0025.