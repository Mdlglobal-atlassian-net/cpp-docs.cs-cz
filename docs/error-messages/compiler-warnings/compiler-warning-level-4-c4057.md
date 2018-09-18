---
title: Upozornění (úroveň 4) C4057 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4057
dev_langs:
- C++
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b10ce6b67fd24b4b8db01177af0225deab9dba4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088004"
---
# <a name="compiler-warning-level-4-c4057"></a>Kompilátor upozornění (úroveň 4) C4057

'operator': "identifier1" dereference na mírně odlišnými základními typy z "identifier2"

Dvou výrazů ukazatele odkazují na různé základní typy. Výrazy se používají bez převodu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Kombinování typy se znaménkem a bez znaménka.

1. Kombinování **krátký** a **dlouhé** typy.