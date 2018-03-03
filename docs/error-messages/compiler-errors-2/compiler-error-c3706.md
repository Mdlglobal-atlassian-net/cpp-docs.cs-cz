---
title: "C3706 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3706
dev_langs:
- C++
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b33ea3c7de9afc605622cc55f4a45f73350d7db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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