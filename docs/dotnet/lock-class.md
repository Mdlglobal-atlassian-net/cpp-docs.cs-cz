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
ms.openlocfilehash: c8056146998443f4e24169a4464b834d8eff29b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208512"
---
# <a name="lock-class"></a>lock – třída

Tato třída automatizuje zámek pro synchronizaci přístupu k objektu z několika vláken.  Když je vytvořen, získá zámek a při jeho zničení uvolní zámek.

## <a name="syntax"></a>Syntaxe

```cpp
ref class lock;
```

## <a name="remarks"></a>Poznámky

`lock` je k dispozici pouze pro objekty CLR a lze je použít pouze v kódu CLR.

Interně, třída Lock používá <xref:System.Threading.Monitor> k synchronizaci přístupu. Další informace najdete v odkazovaném článku.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|---------|-----------|
|[lock::lock](#lock)|Vytvoří objekt `lock`, volitelně čeká na získání zámku, po zadanou dobu nebo vůbec ne.|
|[lock::~lock](#tilde-lock)|Destrukturuje objekt `lock`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|---------|-----------|
|[lock::acquire](#acquire)|Získá zámek objektu, volitelně čeká na získání zámku, po zadanou dobu nebo vůbec ne.|
|[lock::is_locked](#is-locked)|Určuje, zda se má zámek uchovávat.|
|[lock::release](#release)|Uvolní zámek.|
|[lock::try_acquire](#try-acquire)|Získá zámek objektu, počká na určenou dobu a vrátí `bool`, aby nahlásila úspěch získání namísto vyvolání výjimky.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|---------|-----------|
|[Lock:: operator&nbsp;bool](#operator-bool)|Operátor pro použití `lock` v podmíněném výrazu.|
|[lock::operator==](#operator-equality)|Operátor rovnosti|
|[lock::operator!=](#operator-inequality)|Operátor nerovnosti|

## <a name="requirements"></a>Požadavky

**Hlavičkový soubor** \<msclr\lock.h >

Msclr – **oboru názvů**

## <a name="locklock"></a><a name="lock"></a>Lock:: Lock

Vytvoří objekt `lock`, volitelně čeká na získání zámku, po zadanou dobu nebo vůbec ne.

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
Hodnota časového limitu v milisekundách nebo jako <xref:System.TimeSpan>.

### <a name="exceptions"></a>Výjimky

Vyvolá <xref:System.ApplicationException>, pokud k získání zámku nedochází před vypršením časového limitu.

### <a name="remarks"></a>Poznámky

První tři formy konstruktoru se pokusí získat zámek `_object` v rámci zadaného časového limitu (nebo <xref:System.Threading.Timeout.Infinite>, pokud není zadán).

Čtvrtý tvar konstruktoru nezíská zámek na `_object`. `lock_later` je členem [výčtu lock_when](../dotnet/lock-when-enum.md). Pro získání zámku v tomto případě použijte [zámek:: získat](../dotnet/lock-acquire.md) nebo [uzamknout:: try_acquire](../dotnet/lock-try-acquire.md) .

Zámek bude automaticky uvolněn při volání destruktoru.

`_object` nelze <xref:System.Threading.ReaderWriterLock>.  Pokud je to, výsledkem bude chyba kompilátoru.

### <a name="example"></a>Příklad

V tomto příkladu se používá jedna instance třídy napříč několika vlákny. Třída používá zámek sebe sama k zajištění, že přístup k vnitřním datům je konzistentní pro každé vlákno. Hlavní vlákno aplikace používá zámek na stejné instanci třídy, aby pravidelně kontroloval, zda nějaká pracovní vlákna stále existují. Hlavní aplikace pak počká na ukončení, dokud všechna pracovní vlákna nedokončí své úkoly.

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

## <a name="locklock"></a><a name="tilde-lock"></a>Lock:: ~ Lock

Destrukturuje objekt `lock`.

```cpp
~lock();
```

### <a name="remarks"></a>Poznámky

Destruktor volá metodu [Lock:: Release](../dotnet/lock-release.md).

### <a name="example"></a>Příklad

V tomto příkladu se používá jedna instance třídy napříč několika vlákny.  Třída používá zámek sebe sama k zajištění, že přístup k vnitřním datům je konzistentní pro každé vlákno.  Hlavní vlákno aplikace používá zámek na stejné instanci třídy, aby pravidelně kontroloval, zda nějaká pracovní vlákna stále existují. Hlavní aplikace pak počká na ukončení, dokud všechna pracovní vlákna nedokončí své úkoly.

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

## <a name="lockacquire"></a><a name="acquire"></a>Lock:: získat

Získá zámek objektu, volitelně čeká na získání zámku, po zadanou dobu nebo vůbec ne.

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
Hodnota časového limitu v milisekundách nebo jako <xref:System.TimeSpan>.

### <a name="exceptions"></a>Výjimky

Vyvolá <xref:System.ApplicationException>, pokud k získání zámku nedochází před vypršením časového limitu.

### <a name="remarks"></a>Poznámky

Pokud není zadána hodnota časového limitu, výchozí časový limit je <xref:System.Threading.Timeout.Infinite>.

Pokud byl zámek již získán, tato funkce neprovede žádnou akci.

### <a name="example"></a>Příklad

V tomto příkladu se používá jedna instance třídy napříč několika vlákny.  Třída používá zámek sebe sama k zajištění, že přístup k vnitřním datům je konzistentní pro každé vlákno. Hlavní vlákno aplikace používá zámek na stejné instanci třídy, aby pravidelně kontroloval, zda nějaká pracovní vlákna stále existují. Hlavní aplikace pak počká na ukončení, dokud všechna pracovní vlákna nedokončí své úkoly.

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

## <a name="lockis_locked"></a><a name="is-locked"></a>zámek:: is_locked

Určuje, zda se má zámek uchovávat.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Návratová hodnota

`true`, pokud je držen zámek, `false` jinak.

### <a name="example"></a>Příklad

V tomto příkladu se používá jedna instance třídy napříč několika vlákny.  Třída používá zámek sebe sama k zajištění, že přístup k vnitřním datům je konzistentní pro každé vlákno.  Hlavní vlákno aplikace používá zámek na stejné instanci třídy, aby pravidelně kontroloval, zda nějaká pracovní vlákna stále existují, a čeká na ukončení, dokud všechna pracovní vlákna nedokončí své úkoly.

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

## <a name="lockoperator-bool"></a><a name="operator-bool"></a>Lock:: operator bool

Operátor pro použití `lock` v podmíněném výrazu.

```cpp
operator bool();
```

### <a name="return-value"></a>Návratová hodnota

`true`, pokud je držen zámek, `false` jinak.

### <a name="remarks"></a>Poznámky

Tento operátor ve skutečnosti převádí na `_detail_class::_safe_bool`, což je bezpečnější než `bool`, protože nemůže být převeden na integrální typ.

### <a name="example"></a>Příklad

V tomto příkladu se používá jedna instance třídy napříč několika vlákny.  Třída používá zámek sebe sama k zajištění, že přístup k vnitřním datům je konzistentní pro každé vlákno. Hlavní vlákno aplikace používá zámek na stejné instanci třídy, aby pravidelně kontroloval, zda nějaká pracovní vlákna stále existují. Hlavní aplikace počká na ukončení, dokud všechna pracovní vlákna nedokončí své úkoly.

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

## <a name="lockrelease"></a><a name="release"></a>Lock:: Release

Uvolní zámek.

```cpp
void release();
```

### <a name="remarks"></a>Poznámky

Pokud se žádný zámek nedrží, `release` neprovede žádnou akci.

Tuto funkci nemusíte explicitně volat. Když `lock` objekt přejde mimo rozsah, jeho destruktor volá `release`.

### <a name="example"></a>Příklad

V tomto příkladu se používá jedna instance třídy napříč několika vlákny. Třída používá zámek sebe sama k zajištění, že přístup k vnitřním datům je konzistentní pro každé vlákno. Hlavní vlákno aplikace používá zámek na stejné instanci třídy, aby pravidelně kontroloval, zda nějaká pracovní vlákna stále existují. Hlavní aplikace pak počká na ukončení, dokud všechna pracovní vlákna nedokončí své úkoly.

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

## <a name="locktry_acquire"></a><a name="try-acquire"></a>zámek:: try_acquire

Získá zámek objektu, počká na určenou dobu a vrátí `bool`, aby nahlásila úspěch získání namísto vyvolání výjimky.

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
Hodnota časového limitu v milisekundách nebo jako <xref:System.TimeSpan>.

### <a name="return-value"></a>Návratová hodnota

`true`, jestli se získal zámek, `false` jinak.

### <a name="remarks"></a>Poznámky

Pokud byl zámek již získán, tato funkce neprovede žádnou akci.

### <a name="example"></a>Příklad

V tomto příkladu se používá jedna instance třídy napříč několika vlákny. Třída používá zámek sebe sama k zajištění, že přístup k vnitřním datům je konzistentní pro každé vlákno. Hlavní vlákno aplikace používá zámek na stejné instanci třídy, aby pravidelně kontroloval, zda nějaká pracovní vlákna stále existují. Hlavní aplikace pak počká na ukončení, dokud všechna pracovní vlákna nedokončí své úkoly.

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

## <a name="lockoperator"></a><a name="operator-equality"></a>Lock:: operator = = – operátor

Operátor rovnosti

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Parametry

*š*<br/>
Objekt, který má být porovnán s rovností.

### <a name="return-value"></a>Návratová hodnota

Vrátí `true`, jsou-li `t` stejné jako objekt zámku, `false` jinak.

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

## <a name="lockoperator"></a><a name="operator-inequality"></a>Lock:: operator! = – operátor

Operátor nerovnosti

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parametry

*š*<br/>
Objekt, který se má porovnat s nerovností.

### <a name="return-value"></a>Návratová hodnota

Vrátí `true`, pokud `t` se liší od objektu zámku, `false` jinak.

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
