---
title: Vyhodnocování výrazu CXX0064 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0064
dev_langs:
- C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b16133484af5a2225f79c5d293a2c8edd948bdb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025890"
---
# <a name="expression-evaluator-error-cxx0064"></a>Chyba při vyhodnocování výrazu CXX0064

Nelze nastavit zarážku na vázaná virtuální členská funkce

Zarážka byla nastavena na virtuální členská funkce prostřednictvím ukazatele na objekt, jako například:

```
pClass->vfunc( int );
```

Zarážku lze nastavit na virtuální funkce tak, že zadáte třídy, jako například:

```
Class::vfunc( int );
```

Tato chyba se shoduje s CAN0064.