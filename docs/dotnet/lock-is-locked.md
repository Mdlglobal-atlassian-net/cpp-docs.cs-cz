---
title: Lock::is_locked | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- is_locked
- msclr::lock::is_locked
- lock::is_locked
- msclr::lock.is_locked
- lock.is_locked
dev_langs:
- C++
helpviewer_keywords:
- lock::is_locked
ms.assetid: d888827c-8052-47c6-87a2-8c42f60a688d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: de4f7a3c92ccace542a4588b0278fd4f799459c2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="lockislocked"></a>lock::is_locked
Určuje, zda zámek čeká.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool is_locked();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je blokován zámek, `false` jinak.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá jednu instanci třídy napříč více vláken.  Třída využívají k zajištění konzistentní pro každé vlákno přístupů k jeho interních datových zámek sám na sobě.  Hlavní vlákno aplikace používá zámek ve stejné instanci třídy k pravidelně kontrolovat, zda stále existují jakékoli pracovních vláken a čeká ukončíte až do všech pracovních vláken dokončili úkoly.  
  
```  
// msl_lock_is_locked.cpp  
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
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't  
      if (l.is_locked()) { // check if we got the lock  
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
In thread 4, Counter = 0  
In thread 4, Counter = 10  
In thread 7, Counter = 0  
In thread 7, Counter = 10  
In thread 6, Counter = 0  
In thread 6, Counter = 10  
All threads completed.  
```  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\lock.h >  
  
 **Namespace** msclr –  
  
## <a name="see-also"></a>Viz také  
 [Lock – členy třídy](../dotnet/lock-members.md)   
 [lock::operator bool](../dotnet/lock-operator-bool.md)