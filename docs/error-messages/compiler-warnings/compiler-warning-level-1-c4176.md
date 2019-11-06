---
title: Upozornění kompilátoru (úroveň 1) C4176
ms.date: 11/04/2016
f1_keywords:
- C4176
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
ms.openlocfilehash: 6e0f7ab75309994ab306f5caed54724f32e388b1
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624803"
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