---
title: Lock::LOCK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 128a86b59ebf43ab87b0f4f4bcb7e9c684e4ad07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051815"
---
# <a name="locklock"></a>lock::lock
Vytvoří `lock` objektu, volitelně čekají na získání zámku forever, po zadanou dobu času, nebo dokonce vůbec.  
  
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
*d_ostupné*<br/>
Objekt, který chcete zamknout.  
  
*_vypršení časového limitu*<br/>
Hodnota časového limitu v milisekundách, nebo jako <xref:System.TimeSpan>.  
  
## <a name="exceptions"></a>Výjimky  
 Vyvolá <xref:System.ApplicationException> Pokud získání zámku se nevyskytuje před vypršením časového limitu.  
  
## <a name="remarks"></a>Poznámky  
 První tři formy konstruktoru se pokouší získat zámek na `_object` během zadaného časového limitu (nebo <xref:System.Threading.Timeout.Infinite> Pokud se nezadá žádný).  
  
 Čtvrtý formu konstruktoru nelze získat zámek na `_object`. `lock_later` je členem skupiny [lock_when – výčet](../dotnet/lock-when-enum.md). Použití [lock::acquire](../dotnet/lock-acquire.md) nebo [lock::try_acquire](../dotnet/lock-try-acquire.md) v tomto případě získání zámku.  
  
 Zámek se automaticky uvolněn, pokud je volán destruktor.  
  
 `_object` nemůže být <xref:System.Threading.ReaderWriterLock>.  Pokud se jedná, způsobí chybu kompilátoru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá jednu instanci třídy napříč více vlákny.  K zajištění, že jsou přístupy k jeho vnitřní data konzistentní vzhledem k aplikacím pro každé vlákno používá třídu zámek na sobě.  Hlavního vlákna aplikace používá zámek na stejnou instanci třídy, aby pravidelně kontrolovaly, zda stále existují jakékoli pracovní vlákna a čekání na ukončení až do všech pracovních vláken dokončení jejich úloh.  
  
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
 [Lock – členy](../dotnet/lock-members.md)   
 [zámek:: ~ lock](../dotnet/lock-tilde-lock.md)   
 [Lock::Acquire](../dotnet/lock-acquire.md)   
 [lock::try_acquire](../dotnet/lock-try-acquire.md)