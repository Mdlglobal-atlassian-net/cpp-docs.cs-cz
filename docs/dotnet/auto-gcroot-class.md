---
title: auto_gcroot – třída
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot::auto_gcroot
- msclr::auto_gcroot::attach
- msclr::auto_gcroot::get
- msclr::auto_gcroot::release
- msclr::auto_gcroot::reset
- msclr::auto_gcroot::swap
- msclr::auto_gcroot::operator=
- msclr::auto_gcroot::operator->
- msclr::auto_gcroot::operator!
- msclr::auto_gcroot::operator auto_gcroot
helpviewer_keywords:
- msclr::auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
ms.openlocfilehash: 87e6703f759888b36ed89daed10df937701c6dbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372555"
---
# <a name="auto_gcroot-class"></a>auto_gcroot – třída

Automatická správa prostředků (například [auto_ptr Class),](../standard-library/auto-ptr-class.md)kterou lze použít k vložení virtuálního popisovače do nativního typu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename _element_type>
class auto_gcroot;
```

### <a name="parameters"></a>Parametry

*_element_type*<br/>
Spravovaný typ, který má být vložen.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejní konstruktéři

|Name (Název)|Popis|
|---------|-----------|
|[auto_gcroot::auto_gcroot](#auto-gcroot)|Konstruktor. `auto_gcroot`|
|[auto_gcroot::~auto_gcroot](#tilde-auto-gcroot)|Destruktor. `auto_gcroot`
|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|---------|-----------|
|[auto_gcroot::attach](#attach)|Připojte `auto_gcroot` k objektu.|
|[auto_gcroot::get](#get)|Získá obsažený objekt.|
|[auto_gcroot::release](#release)|Uvolní objekt ze `auto_gcroot` správy.|
|[auto_gcroot::reset](#reset)|Zničte aktuální vlastněný objekt a volitelně převezměte nový objekt.|
|[auto_gcroot::swap](#swap)|Zamění objekty `auto_gcroot`za jiné .|

### <a name="public-operators"></a>Veřejní provozovatelé

|Name (Název)|Popis|
|---------|-----------|
|[auto_gcroot::operátor-&gt;](#operator-arrow)|Operátor přístupu člena.|  
|[auto_gcroot::operator=](#operator-assign)|Operátor přiřazení.|
|[auto_gcroot::auto_gcroot&nbsp;operátora](#operator-auto-gcroot)|Operátor přetypového `auto_gcroot` přetypádku mezi a kompatibilní typy.|
|[auto_gcroot::operátor&nbsp;bool](#operator-bool)|Operátor pro `auto_gcroot` použití v podmíněném výrazu.|  
|[auto_gcroot::operátor!](#operator-logical-not)|Operátor pro `auto_gcroot` použití v podmíněném výrazu.|

## <a name="requirements"></a>Požadavky

**Soubor hlavičky** \<msclr\auto_gcroot.h>

**Obor názvů** msclr

## <a name="auto_gcrootauto_gcroot"></a><a name="auto-gcroot"></a>auto_gcroot::auto_gcroot

Konstruktor. `auto_gcroot`

```cpp
auto_gcroot(
   _element_type _ptr = nullptr
);
auto_gcroot(
   auto_gcroot<_element_type> & _right
);
template<typename _other_type>
auto_gcroot(
   auto_gcroot<_other_type> & _right
);
```

### <a name="parameters"></a>Parametry

*_ptr*<br/>
Objekt vlastnit.

*_right*<br/>
Existující `auto_gcroot`.

### <a name="remarks"></a>Poznámky

Při vytváření `auto_gcroot` z existující `auto_gcroot`, `auto_gcroot` existující uvolní svůj objekt před převodem `auto_gcroot`vlastnictví objektu na nový .

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_auto_gcroot.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class RefClassA {
protected:
   String^ m_s;
public:
   RefClassA(String^ s) : m_s(s) {
      Console::WriteLine( "in RefClassA constructor: " + m_s );
   }
   ~RefClassA() {
      Console::WriteLine( "in RefClassA destructor: " + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class RefClassB : RefClassA {
public:
   RefClassB( String^ s ) : RefClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

class ClassA { //unmanaged class
private:
   auto_gcroot<RefClassA^> m_a;

public:
   ClassA() : m_a( gcnew RefClassA( "unmanaged" ) ) {}
   ~ClassA() {} //no need to delete m_a

   void DoSomething() {
      m_a->PrintHello();
   }
};

int main()
{
   {
      ClassA a;
      a.DoSomething();
   } // a.m_a is automatically destroyed as a goes out of scope

   {
      auto_gcroot<RefClassA^> a(gcnew RefClassA( "first" ) );
      a->PrintHello();
   }

   {
      auto_gcroot<RefClassB^> b(gcnew RefClassB( "second" ) );
      b->PrintHello();
      auto_gcroot<RefClassA^> a(b); //construct from derived type
      a->PrintHello();
      auto_gcroot<RefClassA^> a2(a); //construct from same type
      a2->PrintHello();
   }

   Console::WriteLine("done");
}
```

```Output
in RefClassA constructor: unmanaged
Hello from unmanaged A!
in RefClassA destructor: unmanaged
in RefClassA constructor: first
Hello from first A!
in RefClassA destructor: first
in RefClassA constructor: second
Hello from second B!
Hello from second A!
Hello from second A!
in RefClassA destructor: second
done
```

## <a name="auto_gcrootauto_gcroot"></a><a name="tilde-auto-gcroot"></a>auto_gcroot::~auto_gcroot

Destruktor. `auto_gcroot`

```cpp
~auto_gcroot();
```

### <a name="remarks"></a>Poznámky

Destruktor také zničí vlastněný objekt.

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_dtor.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
public:
   ClassA() { Console::WriteLine( "ClassA constructor" ); }
   ~ClassA() { Console::WriteLine( "ClassA destructor" ); }
};

int main()
{
   // create a new scope for a:
   {
      auto_gcroot<ClassA^> a = gcnew ClassA;
   }
   // a goes out of scope here, invoking its destructor
   // which in turns destructs the ClassA object.

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor
ClassA destructor
done
```

## <a name="auto_gcrootattach"></a><a name="attach"></a>auto_gcroot::připojit

Připojte `auto_gcroot` k objektu.

```cpp
auto_gcroot<_element_type> & attach(
   _element_type _right
);
auto_gcroot<_element_type> & attach(
   auto_gcroot<_element_type> & _right
);
template<typename _other_type>
auto_gcroot<_element_type> & attach(
   auto_gcroot<_other_type> & _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Objekt připojit nebo `auto_gcroot` obsahující objekt připojit.

### <a name="return-value"></a>Návratová hodnota

Aktuální `auto_gcroot`.

### <a name="remarks"></a>Poznámky

Pokud `_right` je `auto_gcroot`, uvolní vlastnictví svého objektu před objekt je `auto_gcroot`připojen k aktuálnímu .

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_attach.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "in ClassA constructor:" + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor:" + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String ^ s) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main() {
   auto_gcroot<ClassA^> a( gcnew ClassA( "first" ) );
   a->PrintHello();
   a.attach( gcnew ClassA( "second" ) ); // attach same type
   a->PrintHello();
   ClassA^ ha = gcnew ClassA( "third" );
   a.attach( ha ); // attach raw handle
   a->PrintHello();
   auto_gcroot<ClassB^> b( gcnew ClassB("fourth") );
   b->PrintHello();
   a.attach( b ); // attach derived type
   a->PrintHello();
}
```

```Output
in ClassA constructor:first
Hello from first A!
in ClassA constructor:second
in ClassA destructor:first
Hello from second A!
in ClassA constructor:third
in ClassA destructor:second
Hello from third A!
in ClassA constructor:fourth
Hello from fourth B!
in ClassA destructor:third
Hello from fourth A!
in ClassA destructor:fourth
```

## <a name="auto_gcrootget"></a><a name="get"></a>auto_gcroot::získat

Získá obsažený objekt.

```cpp
_element_type get() const;
```

### <a name="return-value"></a>Návratová hodnota

Obsažený objekt.

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_get.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ){
      Console::WriteLine( "in ClassA constructor:" + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor:" + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

void PrintA( ClassA^ a ) {
   a->PrintHello();
}

int main() {
   auto_gcroot<ClassA^> a = gcnew ClassA( "first" );
   a->PrintHello();

   ClassA^ a2 = a.get();
   a2->PrintHello();

   PrintA( a.get() );
}
```

```Output
in ClassA constructor:first
Hello from first A!
Hello from first A!
Hello from first A!
in ClassA destructor:first
```

## <a name="auto_gcrootrelease"></a><a name="release"></a>auto_gcroot::vydání

Uvolní objekt ze `auto_gcroot` správy.

```cpp
_element_type release();
```

### <a name="return-value"></a>Návratová hodnota

Uvolněný objekt.

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_release.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   ClassA^ a;

   // create a new scope:
   {
      auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );
      auto_gcroot<ClassA^> agc2 = gcnew ClassA( "second" );
      a = agc1.release();
   }
   // agc1 and agc2 go out of scope here

   a->PrintHello();

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
ClassA constructor: second
ClassA destructor: second
Hello from first A!
done
```

## <a name="auto_gcrootreset"></a><a name="reset"></a>auto_gcroot::obnovit

Zničte aktuální vlastněný objekt a volitelně převezměte nový objekt.

```cpp
void reset(
   _element_type _new_ptr = nullptr
);
```

### <a name="parameters"></a>Parametry

*_new_ptr*<br/>
(Nepovinné) Nový objekt.

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_reset.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );
   agc1->PrintHello();

   ClassA^ ha = gcnew ClassA( "second" );
   agc1.reset( ha ); // release first object, reference second
   agc1->PrintHello();

   agc1.reset(); // release second object, set to nullptr

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
Hello from first A!
ClassA constructor: second
ClassA destructor: first
Hello from second A!
ClassA destructor: second
done
```

## <a name="auto_gcrootswap"></a><a name="swap"></a>auto_gcroot::swap

Zamění objekty `auto_gcroot`za jiné .

```cpp
void swap(
   auto_gcroot<_element_type> & _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
S `auto_gcroot` kterými chcete zaměnit objekty.

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_swap.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s1 = "string one";
   auto_gcroot<String^> s2 = "string two";

   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
   s1.swap( s2 );
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
}
```

```Output
s1 = 'string one', s2 = 'string two'
s1 = 'string two', s2 = 'string one'
```

## <a name="auto_gcrootoperator-gt"></a><a name="operator-arrow"></a>auto_gcroot::operátor-&gt;

Operátor přístupu člena.

```cpp
_element_type operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt, který je zabalen `auto_gcroot`.

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_op_arrow.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }

   int m_i;
};

int main() {
   auto_gcroot<ClassA^> a( gcnew ClassA( "first" ) );
   a->PrintHello();

   a->m_i = 5;
   Console::WriteLine( "a->m_i = {0}", a->m_i );
}
```

```Output
Hello from first A!
a->m_i = 5
```

## <a name="auto_gcrootoperator"></a><a name="operator-assign"></a>auto_gcroot::operátor=

Operátor přiřazení.

```cpp
auto_gcroot<_element_type> & operator=(
   _element_type _right
);
auto_gcroot<_element_type> & operator=(
   auto_gcroot<_element_type> & _right
);
template<typename _other_type>
auto_gcroot<_element_type> & operator=(
   auto_gcroot<_other_type> & _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Objekt nebo `auto_gcroot` chcete-li být `auto_gcroot`přiřazenk aktuálnímu .

### <a name="return-value"></a>Návratová hodnota

Aktuální `auto_gcroot`, nyní `_right`vlastnící .

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_operator_equals.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA(String^ s) : m_s(s) {
      Console::WriteLine( "in ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor: " + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String^ s ) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main()
{
   auto_gcroot<ClassA^> a;
   auto_gcroot<ClassA^> a2(gcnew ClassA( "first" ) );
   a = a2; // assign from same type
   a->PrintHello();

   ClassA^ ha = gcnew ClassA( "second" );
   a = ha; // assign from raw handle

   auto_gcroot<ClassB^> b(gcnew ClassB( "third" ) );
   b->PrintHello();
   a = b; // assign from derived type
   a->PrintHello();

   Console::WriteLine("done");
}
```

```Output
in ClassA constructor: first
Hello from first A!
in ClassA constructor: second
in ClassA destructor: first
in ClassA constructor: third
Hello from third B!
in ClassA destructor: second
Hello from third A!
done
in ClassA destructor: third
```

## <a name="auto_gcrootoperator-auto_gcroot"></a><a name="operator-auto-gcroot"></a>auto_gcroot::operátor auto_gcroot

Operátor přetypového `auto_gcroot` přetypádku mezi a kompatibilní typy.

```cpp
template<typename _other_type>
operator auto_gcroot<_other_type>();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální `auto_gcroot` přetypované na `auto_gcroot<_other_type>`.

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_op_auto_gcroot.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String ^ s) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main() {
   auto_gcroot<ClassB^> b = gcnew ClassB("first");
   b->PrintHello();
   auto_gcroot<ClassA^> a = (auto_gcroot<ClassA^>)b;
   a->PrintHello();
}
```

```Output
Hello from first B!
Hello from first A!
```

## <a name="auto_gcrootoperator-bool"></a><a name="operator-bool"></a>auto_gcroot::operátor bool

Operátor pro `auto_gcroot` použití v podmíněném výrazu.

```cpp
operator bool() const;
```

### <a name="return-value"></a>Návratová hodnota

`true`pokud je zabalený objekt platný; `false` v opačném případě.

### <a name="remarks"></a>Poznámky

Tento operátor ve `_detail_class::_safe_bool`skutečnosti převede `bool` na , což je bezpečnější než proto, že nelze převést na integrální typ.

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_operator_bool.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s;
   if ( s ) Console::WriteLine( "s is valid" );
   if ( !s ) Console::WriteLine( "s is invalid" );
   s = "something";
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
   s.reset();
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
}
```

```Output
s is invalid
now s is valid
now s is invalid
```

## <a name="auto_gcrootoperator"></a><a name="operator-logical-not"></a>auto_gcroot::operátor!

Operátor pro `auto_gcroot` použití v podmíněném výrazu.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Návratová hodnota

`true`pokud je zalomený objekt neplatný; `false` v opačném případě.

### <a name="example"></a>Příklad

```cpp
// msl_auto_gcroot_operator_not.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s;
   if ( s ) Console::WriteLine( "s is valid" );
   if ( !s ) Console::WriteLine( "s is invalid" );
   s = "something";
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
   s.reset();
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
}
```

```Output
s is invalid
now s is valid
now s is invalid
```
