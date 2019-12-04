---
title: Chyba kompilátoru C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 810ec59a814b04349913648fb49a03eb63912cd9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757979"
---
# <a name="compiler-error-c3706"></a>Chyba kompilátoru C3706

' function ': musí být rozhraním COM pro vyvolání událostí COM

Rozhraní události, které použijete k vyvolání událostí modelu COM, musí být rozhraní modelu COM. V této situaci by rozhraní mělo být definováno buď pomocí vizuálního C++ atributu, nebo importováno pomocí [#import](../../preprocessor/hash-import-directive-cpp.md) z knihovny typů s atributem embedded_idl #import.

Všimněte si, že `#include` řádky hlavičkových souborů ATL zobrazených v níže uvedené ukázce jsou vyžadovány pro použití událostí COM. Chcete-li tuto chybu opravit, zajistěte, aby `IEvents` (rozhraní Event) rozhraní COM používalo jeden z následujících atributů pro definici rozhraní: [objekt](../../windows/object-cpp.md), [duální](../../windows/dual.md)nebo [odesílající](../../windows/dispinterface.md).

Pokud rozhraní pochází ze souboru hlaviček generovaného pomocí MIDL, kompilátor ho nebude rozpoznat jako rozhraní COM.

Následující ukázka generuje C3706:

```cpp
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
