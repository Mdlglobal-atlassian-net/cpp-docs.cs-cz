---
title: C3706 Chyba kompilátoru | Microsoft Docs
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
ms.openlocfilehash: 8cb54dfce6a6974fcf09886f2d13047cdab53ced
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265243"
---
# <a name="compiler-error-c3706"></a>C3706 chyby kompilátoru
'function': musí být rozhraní modelu COM k vyvolání události COM  
  
 Události rozhraní, které můžete použít k vyvolání události COM musí být rozhraní modelu COM. V takovém případě by měl být buď definován atribut Visual C++ pomocí rozhraní, nebo importován pomocí [#import](../../preprocessor/hash-import-directive-cpp.md) z knihovny typů s #import na embedded_idl – atribut.  
  
 Všimněte si, že `#include` řádky soubory hlaviček ATL uvedené v následující ukázce jsou požadované pro použití COM události. Chcete-li tuto chybu opravit, ujistěte se, `IEvents` (eventing rozhraní) rozhraní modelu COM s použitím jednu z těchto atributů k definici rozhraní: [objekt](../../windows/object-cpp.md), [duální](../../windows/dual.md), nebo [ dispinterface](../../windows/dispinterface.md).  
  
 Pokud z hlavičky souboru generované MIDL je rozhraní, kompilátor nebude rozpoznat jako rozhraní modelu COM.  
  
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