---
title: "C3703 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3703
dev_langs: C++
helpviewer_keywords: C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50461e3fe9e6bd2da87f71d725f9e0f94bfa6df0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3703"></a>C3703 chyby kompilátoru
obslužné rutiny události: metodu obslužné rutiny události musí mít stejnou třídu úložiště jako zdroj 'událost'  
  
 [Událostí](../../cpp/event-handling.md) obsahuje třídu jiného úložiště, než ke které je byl zapojen obslužné rutiny události. Například tato chyba nastane, pokud obslužná rutina události je funkce statický člen a události nejsou statické. Pokud chcete vyřešit tuto chybu, poskytněte události a obslužné rutiny události stejnou třídu úložiště.  
  
 Následující ukázka generuje C3703:  
  
```  
// C3703.cpp  
// C3703 expected  
#include <stdio.h>  
  
[event_source(type=native)]  
class CEventSrc {  
public:  
   __event static void MyEvent();  
};  
  
[event_receiver(type=native)]  
class CEventHandler {  
public:  
   // delete the following line to resolve  
   void MyHandler() {}  
  
   // try the following line instead  
   // static void MyHandler() {}  
  
   void HookIt(CEventSrc* pSource) {  
      __hook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);  
   }  
  
   void UnhookIt(CEventSrc* pSource) {  
      __unhook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);  
   }  
};  
  
int main() {  
   CEventSrc src;  
   CEventHandler hnd;  
  
   hnd.HookIt(&src);  
   __raise src.MyEvent();  
   hnd.UnhookIt(&src);  
}  
```