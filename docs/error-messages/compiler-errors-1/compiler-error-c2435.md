---
title: Chyba kompilátoru C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 7ef22711884dabb83efa8c7ebfdb7648316c12ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205410"
---
# <a name="compiler-error-c2435"></a>Chyba kompilátoru C2435

> *var*: Dynamická inicializace vyžaduje spravovanou CRT, nemůže kompilovat s/CLR: safe.

## <a name="remarks"></a>Poznámky

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Inicializace proměnné domény globální aplikace vyžaduje, aby byl objekt CRT kompilován s `/clr:pure`, který nevytváří ověřitelný obrázek.

Další informace naleznete v tématu [AppDomain](../../cpp/appdomain.md) a [Process](../../cpp/process.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2435:

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```
