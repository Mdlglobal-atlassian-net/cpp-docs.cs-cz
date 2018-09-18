---
title: Chyba kompilátoru C3706 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3706
dev_langs:
- C++
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbebf5752a9ed42ea4af8d3a13e45c78fc1753ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110507"
---
# <a name="compiler-error-c3706"></a>Chyba kompilátoru C3706

'function': musí být rozhraní modelu COM, aby se mohly aktivovat události COM

Rozhraní událostí, které vám mohly aktivovat události COM musí být rozhraní modelu COM. V takovém případě rozhraní by měla být buď definovány pomocí atributu Visual C++, nebo importovat pomocí [#import](../../preprocessor/hash-import-directive-cpp.md) z knihovny typů s atributem společnosti #import embedded_idl.

Všimněte si, `#include` řádky hlavičkové soubory ATL. je znázorněno v následující ukázce jsou požadované pro použití událostí modelu COM. Chcete-li tuto chybu opravit, ujistěte se, `IEvents` (rozhraní eventing) rozhraní modelu COM s použitím jedné z následujících atributů do definice rozhraní: [objekt](../../windows/object-cpp.md), [duální](../../windows/dual.md), nebo [ dispinterface](../../windows/dispinterface.md).

Pokud rozhraní je ze souboru hlaviček generovaných jazykem MIDL, kompilátor jej nerozpozná jako rozhraní modelu COM.

Následující ukázka generuje C3706:

```
// C3706.cpp
// compile with: /c
// C3706 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];

// Uncomment the following line to resolve.
// [object, uuid="12341234-1234-1234-1234-123412341237"]
__interface IEvents : IUnknown {
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]
};

[dual, uuid="12341234-1234-1234-1234-123412341235"]
__interface IBase {
   HRESULT fireEvents();
};

[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]
class CEventSrc : public IBase {
   public:
   __event __interface IEvents;

   HRESULT fireEvents() {
      HRESULT hr = IEvents_event1(123);
      return hr;
   }
};
```