---
title: lock – třída
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::lock::lock
- msclr::lock::is_locked
- msclr::lock.is_locked
- msclr::lock::acquire
- msclr::lock::try_acquire
- msclr::lock::release
- msclr::lock::operator==
- msclr::lock::operator!=
helpviewer_keywords:
- msclr::lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: ea09dd3d4a2eaf4cf7708d09509cfecfa4a6c6d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373066"
---
# <a name="lock-class"></a>lock – třída

Tato třída automatizuje uzamčení pro synchronizaci přístupu k objektu z několika vláken.  Při konstrukci získá zámek a při zničení uvolní zámek.

## <a name="syntax"></a>Syntaxe

```cpp
ref class lock;
```

## <a name="remarks"></a>Poznámky

`lock`je k dispozici pouze pro objekty CLR a lze jej použít pouze v kódu CLR.

Interně třída lock <xref:System.Threading.Monitor> používá k synchronizaci přístupu. Další informace naleznete v odkazovaném článku.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejní konstruktéři

|Name (Název)|Popis|
|---------|-----------|
|[lock::lock](#lock)|Vytvoří `lock` objekt, volitelně čeká na získání zámku navždy, po určitou dobu nebo vůbec.|
|[zámek::~lock](#tilde-lock)|Zničí `lock` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|---------|-----------|
|[lock::acquire](#acquire)|Získá zámek na objekt, volitelně čeká na získání zámku navždy, po určitou dobu, nebo vůbec.|
|[lock::is_locked](#is-locked)|Označuje, zda je zámek držen.|
|[lock::release](#release)|Uvolní zámek.|
|[lock::try_acquire](#try-acquire)|Získá zámek na objekt, čekání na zadané množství času `bool` a vrácení a nahlásit úspěch akvizice namísto vyvolání výjimky.|

### <a name="public-operators"></a>Veřejní provozovatelé

|Name (Název)|Popis|
|---------|-----------|
|[zámek::operátor&nbsp;bool](#operator-bool)|Operátor pro `lock` použití v podmíněném výrazu.|
|[lock::operator==](#operator-equality)|Operátor rovnosti.|
|[zámek::operátor!=](#operator-inequality)|Operátor nerovnosti.|

## <a name="requirements"></a>Požadavky

**Soubor** \<záhlaví msclr\lock.h>

**Obor názvů** msclr

## <a name="locklock"></a><a name="lock"></a>zámek::zámek

Vytvoří `lock` objekt, volitelně čeká na získání zámku navždy, po určitou dobu nebo vůbec.

```cpp
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

### <a name="parameters"></a>Parametry

*_object*<br/>
Objekt, který má být uzamčen.

*_timeout*<br/>
Hodnota časového výpadku v milisekundách nebo jako <xref:System.TimeSpan>.

### <a name="exceptions"></a>Výjimky

<xref:System.ApplicationException> Vyvolá, pokud nedojde k pořízení zámku před časovým časem.

### <a name="remarks"></a>Poznámky

První tři formy konstruktoru se pokusí `_object` získat zámek v rámci <xref:System.Threading.Timeout.Infinite> zadaného časového období (nebo pokud není zadán žádný).

Čtvrtá forma konstruktoru nezíská zámek `_object`na . `lock_later`je členem [lock_when výčtu](../dotnet/lock-when-enum.md). Použijte [lock::acquire](../dotnet/lock-acquire.md) nebo [lock::try_acquire](../dotnet/lock-try-acquire.md) získat zámek v tomto případě.

Zámek se automaticky uvolní při volání destruktoru.

`_object`nemůže být <xref:System.Threading.ReaderWriterLock>.  Pokud ano, dojde k chybě kompilátoru.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy v několika vláknech. Třída používá zámek na sebe a ujistěte se, že přístupy k jeho vnitřní data jsou konzistentní pro každé vlákno. Hlavní podproces aplikace používá zámek na stejné instanci třídy pravidelně kontrolovat, zda existují ještě nějaké pracovní podprocesy. Hlavní aplikace pak čeká na ukončení, dokud všechny pracovní podprocesy dokončily své úkoly.

```cpp
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

## <a name="locklock"></a><a name="tilde-lock"></a>zámek::~lock

Zničí `lock` objekt.

```cpp
~lock();
```

### <a name="remarks"></a>Poznámky

Destruktor volá [lock::release](../dotnet/lock-release.md).

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy v několika vláknech.  Třída používá zámek na sebe a ujistěte se, že přístupy k jeho vnitřní data jsou konzistentní pro každé vlákno.  Hlavní podproces aplikace používá zámek na stejné instanci třídy pravidelně kontrolovat, zda existují ještě nějaké pracovní podprocesy. Hlavní aplikace pak čeká na ukončení, dokud všechny pracovní podprocesy dokončily své úkoly.

```cpp
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

## <a name="lockacquire"></a><a name="acquire"></a>zámek::získat

Získá zámek na objekt, volitelně čeká na získání zámku navždy, po určitou dobu, nebo vůbec.

```cpp
void acquire();
void acquire(
   int _timeout
);
void acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Parametry

*_timeout*<br/>
Hodnota časového času v milisekundách nebo jako <xref:System.TimeSpan>.

### <a name="exceptions"></a>Výjimky

<xref:System.ApplicationException> Vyvolá, pokud nedojde k pořízení zámku před časovým časem.

### <a name="remarks"></a>Poznámky

Pokud není zadána hodnota časového limitu, <xref:System.Threading.Timeout.Infinite>výchozí časový limit je .

Pokud již byl získán zámek, tato funkce neprovede žádné.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy v několika vláknech.  Třída používá zámek na sebe a ujistěte se, že přístupy k jeho vnitřní data jsou konzistentní pro každé vlákno. Hlavní podproces aplikace používá zámek na stejné instanci třídy pravidelně kontrolovat, zda existují ještě nějaké pracovní podprocesy. Hlavní aplikace pak čeká na ukončení, dokud všechny pracovní podprocesy dokončily své úkoly.

```cpp
// msl_lock_acquire.cpp
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

## <a name="lockis_locked"></a><a name="is-locked"></a>zámek::is_locked

Označuje, zda je zámek držen.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Návratová hodnota

`true`pokud je zámek `false` držen, jinak.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy v několika vláknech.  Třída používá zámek na sebe a ujistěte se, že přístupy k jeho vnitřní data jsou konzistentní pro každé vlákno.  Hlavní podproces aplikace používá zámek na stejné instanci třídy pravidelně kontrolovat, zda existují pracovní vlákna a čeká na ukončení, dokud všechna pracovní vlákna dokončí své úkoly.

```cpp
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

## <a name="lockoperator-bool"></a><a name="operator-bool"></a>zámek::operátor bool

Operátor pro `lock` použití v podmíněném výrazu.

```cpp
operator bool();
```

### <a name="return-value"></a>Návratová hodnota

`true`pokud je zámek `false` držen, jinak.

### <a name="remarks"></a>Poznámky

Tento operátor skutečně `_detail_class::_safe_bool` převede na `bool` který je bezpečnější než proto, že nelze převést na integrální typ.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy v několika vláknech.  Třída používá zámek na sebe a ujistěte se, že přístupy k jeho vnitřní data jsou konzistentní pro každé vlákno. Hlavní podproces aplikace používá zámek na stejné instanci třídy pravidelně kontrolovat, zda existují ještě nějaké pracovní podprocesy. Hlavní aplikace čeká na ukončení, dokud všechny pracovní podprocesy dokončí své úkoly.

```cpp
// msl_lock_op_bool.cpp
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
      if (l) { // use bool operator to check for lock
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

## <a name="lockrelease"></a><a name="release"></a>zámek::uvolnění

Uvolní zámek.

```cpp
void release();
```

### <a name="remarks"></a>Poznámky

Pokud není držen žádný `release` zámek, neprovede žádnou akci.

Tuto funkci nemusíte volat explicitně. Když `lock` objekt přejde mimo rozsah, jeho `release`destruktor volá .

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy v několika vláknech. Třída používá zámek na sebe a ujistěte se, že přístupy k jeho vnitřní data jsou konzistentní pro každé vlákno. Hlavní podproces aplikace používá zámek na stejné instanci třídy pravidelně kontrolovat, zda existují ještě nějaké pracovní podprocesy. Hlavní aplikace pak čeká na ukončení, dokud všechny pracovní podprocesy dokončily své úkoly.

```cpp
// msl_lock_release.cpp
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

## <a name="locktry_acquire"></a><a name="try-acquire"></a>zámek::try_acquire

Získá zámek na objekt, čekání na zadané množství času `bool` a vrácení a nahlásit úspěch akvizice namísto vyvolání výjimky.

```cpp
bool try_acquire(
   int _timeout_ms
);
bool try_acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Parametry

*_timeout*<br/>
Hodnota časového času v milisekundách nebo jako <xref:System.TimeSpan>.

### <a name="return-value"></a>Návratová hodnota

`true`pokud byl zámek `false` získán, jinak.

### <a name="remarks"></a>Poznámky

Pokud již byl získán zámek, tato funkce neprovede žádné.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy v několika vláknech. Třída používá zámek na sebe a ujistěte se, že přístupy k jeho vnitřní data jsou konzistentní pro každé vlákno. Hlavní podproces aplikace používá zámek na stejné instanci třídy pravidelně kontrolovat, zda existují ještě nějaké pracovní podprocesy. Hlavní aplikace pak čeká na ukončení, dokud všechny pracovní podprocesy dokončily své úkoly.

```cpp
// msl_lock_try_acquire.cpp
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

## <a name="lockoperator"></a><a name="operator-equality"></a>zámek::operátor==

Operátor rovnosti.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Parametry

*t*<br/>
Objekt porovnat rovnost.

### <a name="return-value"></a>Návratová hodnota

`true` Vrátí, `t` pokud je stejný jako objekt `false` zámku, jinak.

### <a name="example"></a>Příklad

```cpp
// msl_lock_op_eq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   lock l1(o1);
   if (l1 == o1) {
      Console::WriteLine("Equal!");
   }
}
```

```Output
Equal!
```

## <a name="lockoperator"></a><a name="operator-inequality"></a>zámek::operátor!=

Operátor nerovnosti.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parametry

*t*<br/>
Objekt porovnat pro nerovnost.

### <a name="return-value"></a>Návratová hodnota

`true` Vrátí, `t` pokud se liší od `false` objektu zámku, jinak.

### <a name="example"></a>Příklad

```cpp
// msl_lock_op_ineq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   Object^ o2 = gcnew Object;
   lock l1(o1);
   if (l1 != o2) {
      Console::WriteLine("Inequal!");
   }
}
```

```Output
Inequal!
```
