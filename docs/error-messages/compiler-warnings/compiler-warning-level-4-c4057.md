---
title: Kompilátor upozornění (úroveň 4) C4057
ms.date: 11/04/2016
f1_keywords:
- C4057
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
ms.openlocfilehash: 234223ee7b6a031dd9e2c0fc88ccbbdba05beb3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401433"
---
# <a name="compiler-warning-level-4-c4057"></a>Kompilátor upozornění (úroveň 4) C4057

'operator': "identifier1" dereference na mírně odlišnými základními typy z "identifier2"

Dvou výrazů ukazatele odkazují na různé základní typy. Výrazy se používají bez převodu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Kombinování typy se znaménkem a bez znaménka.

1. Kombinování **krátký** a **dlouhé** typy.