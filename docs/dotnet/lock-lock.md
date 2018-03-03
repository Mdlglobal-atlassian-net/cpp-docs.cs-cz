---
title: Lock::LOCK | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- lock::lock
- lock.lock
- msclr.lock.lock
- msclr::lock::lock
dev_langs:
- C++
helpviewer_keywords:
- lock constructor
ms.assetid: c9ad6c71-36ec-49c5-8ebd-f5c3a0cc94f0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5148da4421b24a64dca97288975af42b9688e4ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="locklock"></a>lock::lock
Vytvoří `lock` objekt, volitelně čeká na získání zámku navždy, po zadanou dobu, nebo vůbec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class T> lock(  
   T ^ _object  
);  
template<class T> lock(  
   T ^ _object,  
   int _timeout  
);  
template<class T> lock(  
   T ^ _object,  
   System::TimeSpan _timeout  
);  
template<class T> lock(  
   T ^ _object,  
   lock_later  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_object`  
 Objekt, který má být uzamčena.  
  
 `_timeout`  
 Hodnota časového limitu v milisekundách, nebo jako <xref:System.TimeSpan>.  
  
## <a name="exceptions"></a>Výjimky  
 Vyvolá <xref:System.ApplicationException> Pokud získávání zámku nedochází před vypršením časového limitu.  
  
## <a name="remarks"></a>Poznámky  
 První tři formy konstruktoru pokusí získat zámek na `_object` během zadaného časového limitu (nebo <xref:System.Threading.Timeout.Infinite> Pokud není zadaný žádný).  
  
 Čtvrtý formu konstruktoru není získat zámek na `_object`. `lock_later`je členem skupiny [lock_when – výčet](../dotnet/lock-when-enum.md). Použití [lock::acquire](../dotnet/lock-acquire.md) nebo [lock::try_acquire](../dotnet/lock-try-acquire.md) v tomto případě získat zámek.  
  
 Zámek, budou vydané automaticky při volání destruktoru.  
  
 `_object`nemůže být <xref:System.Threading.ReaderWriterLock>.  Pokud se jedná, dojde k chybě kompilátoru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá jednu instanci třídy napříč více vláken.  Třída využívají k zajištění konzistentní pro každé vlákno přístupů k jeho interních datových zámek sám na sobě.  Hlavní vlákno aplikace používá zámek ve stejné instanci třídy k pravidelně kontrolovat, zda stále existují jakékoli pracovních vláken a čeká ukončíte až do všech pracovních vláken dokončili úkoly.  
  
```  
// msl_lock_lock.cpp  
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
 [Lock – členy třídy](../dotnet/lock-members.md)   
 [zámek:: ~ zámku](../dotnet/lock-tilde-lock.md)   
 [Lock::Acquire](../dotnet/lock-acquire.md)   
 [lock::try_acquire](../dotnet/lock-try-acquire.md)