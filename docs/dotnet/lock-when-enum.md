---
title: "lock_when – výčet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::lock_when
- msclr.lock_when
- lock_when
dev_langs: C++
helpviewer_keywords: lock_when enum
ms.assetid: 6b87bbe9-63cd-450d-a02e-bb91ffd0dcea
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c13325f92f3b17f5881be1deffd9710108ecf4be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="lockwhen-enum"></a>lock_when – výčet
Určuje, odložené uzamčení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum lock_when {  
   lock_later  
};  
```  
  
## <a name="remarks"></a>Poznámky  
 Když předána [lock::lock](../dotnet/lock-lock.md), `lock_later` Určuje, že není mají být provedeny, nyní je zámek.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá jednu instanci třídy napříč více vláken.  Třída využívají k zajištění konzistentní pro každé vlákno přístupů k jeho interních datových zámek sám na sobě.  Hlavní vlákno aplikace používá zámek ve stejné instanci třídy k pravidelně kontrolovat, zda stále existují jakékoli pracovních vláken a čeká ukončíte až do všech pracovních vláken dokončili úkoly.  
  
```  
// msl_lock_lock_when.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
ref class CounterClass {  
private:  
   int Counter;     
  
public:  
   property int ThreadCount;  
  
   // function called by multiple threads, use lock to keep Counter consistent  
   // for each thread  
   void UseCounter() {  
      try {  
         lock l(this); // wait infinitely  
  
         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,   
            Counter);  
  
         for (int i = 0; i < 10; i++) {  
            Counter++;  
            Thread::Sleep(10);  
         }  
  
         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,   
            Counter);  
  
         Counter = 0;  
         // lock is automatically released when it goes out of scope and its destructor is called  
      }  
      catch (...) {  
         Console::WriteLine("Couldn't acquire lock!");  
      }  
  
      ThreadCount--;  
   }  
};  
  
int main() {  
   // create a few threads to contend for access to the shared data  
   CounterClass^ cc = gcnew CounterClass;  
   array<Thread^>^ tarr = gcnew array<Thread^>(5);  
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);  
   for (int i = 0; i < tarr->Length; i++) {  
      tarr[i] = gcnew Thread(startDelegate);  
      cc->ThreadCount++;  
      tarr[i]->Start();  
   }  
  
   // keep our main thread alive until all worker threads have completed  
   lock l(cc, lock_later); // don't lock now, just create the object  
   while (true) {  
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't  
         if (0 == cc->ThreadCount) {  
            Console::WriteLine("All threads completed.");  
            break; // all threads are gone, exit while  
         }  
         else {  
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);  
            l.release(); // some threads exist, let them do their work  
         }  
      }  
   }  
}  
```  
  
```Output  
In thread 3, Counter = 0  
In thread 3, Counter = 10  
In thread 5, Counter = 0  
In thread 5, Counter = 10  
In thread 7, Counter = 0  
In thread 7, Counter = 10  
In thread 4, Counter = 0  
In thread 4, Counter = 10  
In thread 6, Counter = 0  
In thread 6, Counter = 10  
All threads completed.  
```  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\lock.h >  
  
 **Namespace** msclr –  
  
## <a name="see-also"></a>Viz také  
 [Zámek](../dotnet/lock.md)