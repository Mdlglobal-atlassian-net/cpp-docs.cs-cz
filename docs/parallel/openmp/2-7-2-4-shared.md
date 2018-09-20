---
title: 2.7.2.4 sdílené | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d1a545f1c505f9f578cad682399c8d69a882824
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400143"
---
# <a name="2724-shared"></a>2.7.2.4 shared

Tato klauzule sdílí proměnné, které se zobrazují v *seznamu proměnné* mezi všemi vlákny v týmu. Všechna vlákna v rámci týmu přístup do stejné oblasti úložiště pro **sdílené** proměnné.

Syntaxe **sdílené** klauzule vypadá takto:

```
shared(variable-list)
```