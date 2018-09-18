---
title: Chyba kompilátoru C3707 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3707
dev_langs:
- C++
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d18d4a82d06018cdba6147ba6756b1718648847a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052778"
---
# <a name="compiler-error-c3707"></a>Chyba kompilátoru C3707

'function': metoda dispinterface musí mít dispid

Pokud používáte `dispinterface` metoda, je nutné ji přiřadit `dispid`. Chcete-li tuto chybu opravit, přiřaďte `dispid` k `dispinterface` metody, například podle odstraňuje se komentování `id` atributu v metodě v následující ukázce. Další informace najdete v tématu atributy [dispinterface](../../windows/dispinterface.md) a [id](../../windows/id.md).

Následující ukázka generuje C3707:

```
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```