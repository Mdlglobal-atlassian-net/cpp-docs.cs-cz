---
title: C3714 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3714
dev_langs:
- C++
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0046463b7354d0b764e29701bddb117496858e14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266396"
---
# <a name="compiler-error-c3714"></a>C3714 chyby kompilátoru
"metody": metodu obslužné rutiny události musí mít stejné konvence volání jako zdroj 'metodu.  
  
 Jste definovali metodu obslužné rutiny události, který jako metodu zdroj události nepoužili stejné konvence volání. Pro tuto chybu opravit, získat obslužná rutina události se stejnými volání názvů jako metodu zdroje událostí. Například v následujícím kódu zkontrolujte volání konvencí `handler1` a `event1` odpovídat ([__cdecl](../../cpp/cdecl.md) nebo [__stdcall](../../cpp/stdcall.md) nebo jiné). Odebrání volání konvence klíčová slova z obou deklarace rovněž problém vyřešit a způsobit `event1` a `handler1` na výchozí nastavení [thiscall](../../cpp/thiscall.md) konvence volání. V tématu [konvence volání](../../cpp/calling-conventions.md) Další informace.  
  
 Následující ukázka generuje C3714:  
  
```  
// C3714.cpp  
// compile with: /c  
// processor: x86  
[event_source(native)]  
class CEventSrc {  
public:  
   __event void __cdecl event1();  
   // try the following line instead  
   // __event void __stdcall event1();  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   void __stdcall handler1() {}  
  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3714  
   }  
  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3714  
   }  
};  
```