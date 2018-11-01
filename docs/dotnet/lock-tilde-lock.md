---
title: lock::~lock
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ~lock
- msclr.lock.~lock
- lock.~lock
- msclr::lock::~lock
- lock::~lock
helpviewer_keywords:
- ~lock destructor
ms.assetid: 55fa9f6c-d7a6-48ef-9236-ee03342c1d20
ms.openlocfilehash: a545cf6a60b6eb52df416d89308719b67f041f29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575263"
---
# <a name="locklock"></a>lock::~lock

Destructs `lock` objektu.

## <a name="syntax"></a>Syntaxe

```
~lock();
```

## <a name="remarks"></a>Poznámky

Volání destruktoru [lock::release](../dotnet/lock-release.md).

## <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy napříč více vlákny.  K zajištění, že jsou přístupy k jeho vnitřní data konzistentní vzhledem k aplikacím pro každé vlákno používá třídu zámek na sobě.  Hlavního vlákna aplikace používá zámek na stejnou instanci třídy, aby pravidelně kontrolovaly, zda stále existují jakékoli pracovní vlákna a čekání na ukončení až do všech pracovních vláken dokončení jejich úloh.

```
// msl_lock_dtor.cpp
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

[lock – členy](../dotnet/lock-members.md)<br/>
[lock::lock](../dotnet/lock-lock.md)