---
title: "C3709 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3709
dev_langs: C++
helpviewer_keywords: C3709
ms.assetid: d5576b04-2f93-420a-8f3e-8b8e987e8dab
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4d56a4c18543ad71e524a4cc08eecd35ab6e7e2e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3709"></a>C3709 chyby kompilátoru
'function': nesprávná syntaxe pro určení události v __hook /\__unhook  
  
 Pokud zadáte zdroje událostí s [__hook](../../cpp/hook.md) nebo [__unhook](../../cpp/unhook.md), první parametr musí být platný událostí metoda a druhý parametr musí být platný událostí zdrojový objekt (ne metoda).  
  
 Následující ukázka generuje C3709:  
  
```  
// C3709.cpp  
// compile with: /LD  
[event_source(native)]  
class CEventSrc  
{  
public:  
   __event void event1();  
};  
  
[event_receiver(native)]  
class CEventRec  
{  
public:  
   void handler1()  
   {  
   }  
  
   void HookEvents(CEventSrc* pSrc)  
   {  
      __hook(bad, pSrc, CEventRec::handler1);   // C3709  
      // Try the following line instead:  
      // __hook(&CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
  
   void UnhookEvents(CEventSrc* pSrc)  
   {  
      __unhook(&CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
};  
```