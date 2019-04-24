---
title: Chyba kompilátoru C2170
ms.date: 11/04/2016
f1_keywords:
- C2170
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
ms.openlocfilehash: 04d41a50bc0d5e811e47e5f9d146362a543f26f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174676"
---
# <a name="compiler-error-c2170"></a>Chyba kompilátoru C2170

'identifier': není deklarované jako funkce, nemůže jít o vnitřní typ.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Direktivy pragma `intrinsic` se používá pro položky než funkce.

1. Direktivy pragma `intrinsic` se používá pro funkce s žádná vnitřní formuláře.