---
title: Upozornění kompilátoru (úroveň 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: b75b6bee88d0b72e77b32e58ae2f4634a9c30fa0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186995"
---
# <a name="compiler-warning-level-1-c4377"></a>Upozornění kompilátoru (úroveň 1) C4377

nativní typy jsou ve výchozím nastavení privátní; -d1PrivateNativeTypes je zastaralé

V předchozích verzích byly nativní typy v sestaveních ve výchozím nastavení veřejné a pro jejich soukromé použití byla použita interní, nedokumentovaná možnost kompilátoru ( **/d1PrivateNativeTypes**).

Všechny typy, Native a CLR jsou nyní privátní ve výchozím nastavení v sestavení, takže **/d1PrivateNativeTypes** již není potřeba.

## <a name="example"></a>Příklad

Následující ukázka generuje C4377.

```cpp
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```
