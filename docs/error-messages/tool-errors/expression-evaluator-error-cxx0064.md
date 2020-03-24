---
title: Chyba při vyhodnocování výrazu CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: f763754299ed9257fb909b49a7a19c6f3ad58681
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184460"
---
# <a name="expression-evaluator-error-cxx0064"></a>Chyba při vyhodnocování výrazu CXX0064

Nejde nastavit zarážku u vázané virtuální členské funkce.

Zarážka byla nastavena u virtuální členské funkce prostřednictvím ukazatele na objekt, například:

```
pClass->vfunc( int );
```

Zarážku lze nastavit na virtuální funkci zadáním třídy, například:

```
Class::vfunc( int );
```

Tato chyba je shodná s CAN0064.
