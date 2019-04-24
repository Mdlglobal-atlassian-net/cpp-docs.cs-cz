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
ms.openlocfilehash: 43418da36aa2d87608a9d672e4345d24011be0b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153436"
---
# <a name="lock-class"></a>lock – třída

Tato třída automatizuje trvá zámek pro synchronizaci přístupu k objektu z více vláken.  Když se získá zámek a při jeho zničení verze zámku.

## <a name="syntax"></a>Syntaxe

```cpp
ref class lock;
```

## <a name="remarks"></a>Poznámky

`lock` je k dispozici pouze pro objekty CLR a jde použít jenom v kódu CLR.

Interně používá třídy zámku <xref:System.Threading.Monitor> k synchronizaci přístupu. Další informace najdete v odkazovaných článku.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|---------|-----------|
|[lock::lock](#lock)|Vytvoří `lock` objektu, volitelně čekají na získání zámku forever, po zadanou dobu času, nebo dokonce vůbec.|
|[lock::~lock](#tilde-lock)|Destructs `lock` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|---------|-----------|
|[lock::acquire](#acquire)|Získá zámek na objekt, volitelně čekají na získání zámku forever, po zadanou dobu času, nebo dokonce vůbec.|
|[lock::is_locked](#is-locked)|Určuje, zda se koná zámek.|
|[lock::release](#release)|Uvolní zámek.|
|[lock::try_acquire](#try-acquire)|Získá zámek na objekt, čekající na určenou dobu a vrácení `bool` oznamuje úspěch pořízení namísto vyvolání výjimky.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|---------|-----------|
|[Lock::Operator&nbsp;bool](#operator-bool)|Operátor pro používání `lock` v podmíněných výrazech.|
|[lock::operator==](#operator-equality)|Operátor rovnosti.|
|[lock::operator!=](#operator-inequality)|Operátor nerovnosti.|

## <a name="requirements"></a>Požadavky

**Soubor hlaviček** \<msclr\lock.h >

**Namespace** msclr –



## <a name="lock"></a>Lock::LOCK

Vytvoří `lock` objektu, volitelně čekají na získání zámku forever, po zadanou dobu času, nebo dokonce vůbec.

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

*d_ostupné*<br/>
Objekt, který chcete zamknout.

*_timeout*<br/>
Hodnota časového limitu v milisekundách, nebo jako <xref:System.TimeSpan>.

### <a name="exceptions"></a>Výjimky

Vyvolá <xref:System.ApplicationException> Pokud nedojde, získání zámku než časový limit.

### <a name="remarks"></a>Poznámky

První tři formy konstruktoru se snaží získat zámek na `_object` během zadaného časového limitu (nebo <xref:System.Threading.Timeout.Infinite> Pokud se nezadá žádný).

Čtvrtý formu konstruktoru nelze získat zámek na `_object`. `lock_later` je členem skupiny [lock_when – výčet](../dotnet/lock-when-enum.md). Použití [lock::acquire](../dotnet/lock-acquire.md) nebo [lock::try_acquire](../dotnet/lock-try-acquire.md) v tomto případě získání zámku.

Zámek se automaticky uvolněn, pokud je volán destruktor.

`_object` nemůže být <xref:System.Threading.ReaderWriterLock>.  Pokud se jedná, způsobí chybu kompilátoru.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy napříč několika vlákny. Třída používá zámek sám na sobě, abyste měli jistotu, že jsou přístupy k jeho vnitřní data konzistentní vzhledem k aplikacím pro každé vlákno. Pomocí zámku na stejné instanci třídy hlavního vlákna aplikace pravidelně zaškrtněte, pokud chcete zjistit, zda stále existují jakékoli pracovních vláken. Hlavní aplikace pak čeká na ukončení, dokud všechna vlákna pracovního procesu dokončení jejich úloh.

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

## <a name="tilde-lock"></a>lock::~lock

Destructs `lock` objektu.

```cpp
~lock();
```

### <a name="remarks"></a>Poznámky

Volání destruktoru [lock::release](../dotnet/lock-release.md).

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy napříč několika vlákny.  Třída používá zámek sám na sobě, abyste měli jistotu, že jsou přístupy k jeho vnitřní data konzistentní vzhledem k aplikacím pro každé vlákno.  Pomocí zámku na stejné instanci třídy hlavního vlákna aplikace pravidelně zaškrtněte, pokud chcete zjistit, zda stále existují jakékoli pracovních vláken. Hlavní aplikace pak čeká na ukončení, dokud všechna vlákna pracovního procesu dokončení jejich úloh.

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

## <a name="acquire"></a>Lock::Acquire

Získá zámek na objekt, volitelně čekají na získání zámku forever, po zadanou dobu času, nebo dokonce vůbec.

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
Hodnota časového limitu v milisekundách, nebo jako <xref:System.TimeSpan>.

### <a name="exceptions"></a>Výjimky

Vyvolá <xref:System.ApplicationException> Pokud nedojde, získání zámku než časový limit.

### <a name="remarks"></a>Poznámky

Pokud není zadána hodnota časového limitu, je výchozí hodnota časového limitu <xref:System.Threading.Timeout.Infinite>.

Pokud již byl získán zámek, tato funkce nemá žádný účinek.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy napříč několika vlákny.  Třída používá zámek sám na sobě, abyste měli jistotu, že jsou přístupy k jeho vnitřní data konzistentní vzhledem k aplikacím pro každé vlákno. Pomocí zámku na stejné instanci třídy hlavního vlákna aplikace pravidelně zaškrtněte, pokud chcete zjistit, zda stále existují jakékoli pracovních vláken. Hlavní aplikace pak čeká na ukončení, dokud všechna vlákna pracovního procesu dokončení jejich úloh.

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

## <a name="is-locked"></a>Lock::is_locked

Určuje, zda se koná zámek.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud je držen zámek, `false` jinak.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy napříč několika vlákny.  Třída používá zámek sám na sobě, abyste měli jistotu, že jsou přístupy k jeho vnitřní data konzistentní vzhledem k aplikacím pro každé vlákno.  Hlavního vlákna aplikace používá zámek na stejnou instanci třídy, aby pravidelně kontrolovaly, zda stále existují jakékoli pracovní vlákna a čekání na ukončení až do všech pracovních vláken dokončení jejich úloh.

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

## <a name="operator-bool"></a>Lock::Operator bool

Operátor pro používání `lock` v podmíněných výrazech.

```cpp
operator bool();
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud je držen zámek, `false` jinak.

### <a name="remarks"></a>Poznámky

Tento operátor převede ve skutečnosti na `_detail_class::_safe_bool` což je bezpečnější než `bool` vzhledem k tomu, že jej nelze převést na celočíselný typ.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy napříč několika vlákny.  Třída používá zámek sám na sobě, abyste měli jistotu, že jsou přístupy k jeho vnitřní data konzistentní vzhledem k aplikacím pro každé vlákno. Pomocí zámku na stejné instanci třídy hlavního vlákna aplikace pravidelně zaškrtněte, pokud chcete zjistit, zda stále existují jakékoli pracovních vláken. Hlavní aplikace čeká na ukončení, dokud všechna vlákna pracovního procesu dokončení jejich úloh.

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

## <a name="release"></a>Lock::Release

Uvolní zámek.

```cpp
void release();
```

### <a name="remarks"></a>Poznámky

Pokud se právě nachází žádný zámek, `release` nemá žádný účinek.

Není nutné explicitně voláním této funkce. Když `lock` objekt dostane mimo rozsah, její volání destruktoru `release`.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy napříč několika vlákny. Třída používá zámek sám na sobě, abyste měli jistotu, že jsou přístupy k jeho vnitřní data konzistentní vzhledem k aplikacím pro každé vlákno. Pomocí zámku na stejné instanci třídy hlavního vlákna aplikace pravidelně zaškrtněte, pokud chcete zjistit, zda stále existují jakékoli pracovních vláken. Hlavní aplikace pak čeká na ukončení, dokud všechna vlákna pracovního procesu dokončení jejich úloh.

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

## <a name="try-acquire"></a>Lock::try_acquire

Získá zámek na objekt, čekající na určenou dobu a vrácení `bool` oznamuje úspěch pořízení namísto vyvolání výjimky.

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
Hodnota časového limitu v milisekundách, nebo jako <xref:System.TimeSpan>.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud byl získán zámek, `false` jinak.

### <a name="remarks"></a>Poznámky

Pokud již byl získán zámek, tato funkce nemá žádný účinek.

### <a name="example"></a>Příklad

Tento příklad používá jednu instanci třídy napříč několika vlákny. Třída používá zámek sám na sobě, abyste měli jistotu, že jsou přístupy k jeho vnitřní data konzistentní vzhledem k aplikacím pro každé vlákno. Pomocí zámku na stejné instanci třídy hlavního vlákna aplikace pravidelně zaškrtněte, pokud chcete zjistit, zda stále existují jakékoli pracovních vláken. Hlavní aplikace pak čeká na ukončení, dokud všechna vlákna pracovního procesu dokončení jejich úloh.

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

## <a name="operator-equality"></a>Lock::Operator ==

Operátor rovnosti.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Parametry

*t*<br/>
Objekt k porovnání rovnosti.

### <a name="return-value"></a>Návratová hodnota

Vrátí `true` Pokud `t` je stejný jako objekt na uzamčení, `false` jinak.

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

## <a name="operator-inequality"></a>Lock::Operator! =

Operátor nerovnosti.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parametry

*t*<br/>
Objekt k porovnání nerovnost.

### <a name="return-value"></a>Návratová hodnota

Vrátí `true` Pokud `t` se liší od zamknout objekt `false` jinak.

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