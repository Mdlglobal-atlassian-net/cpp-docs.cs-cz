---
title: Upozornění kompilátoru (úroveň 1) C4176
ms.date: 11/04/2016
f1_keywords:
- C4176
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
ms.openlocfilehash: e7efe17b9840179bd21a432c2654fadd7e9230c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199989"
---
# <a name="compiler-warning-level-1-c4176"></a>Upozornění kompilátoru (úroveň 1) C4176

' subcomponent ': Neznámá dílčí komponenta pro #pragma prohlížeč součástí

Direktiva pragma **komponenty** obsahuje neplatnou dílčí komponentu. Chcete-li vyloučit odkazy na konkrétní název, je nutné použít možnost **odkazy** před názvem.

## <a name="example"></a>Příklad

```cpp
// C4176.cpp
// compile with: /W1 /LD
#pragma component(browser, off, i)  // C4176
#pragma component(browser, off, references, i) // ok
```
