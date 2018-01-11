---
title: "C3714 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3714
dev_langs: C++
helpviewer_keywords: C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69f3f5c90524b02cad8a36babaceeb32544e7aff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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