---
title: Chyba při vyhodnocování výrazu CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: 71e4e3e87b33849e6b487b79268ebc9574c2e5a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299475"
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