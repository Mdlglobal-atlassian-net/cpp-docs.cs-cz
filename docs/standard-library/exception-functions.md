---
title: '&lt;výjimka&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- exception/std::current_exception
- exception/std::get_terminate
- exception/std::get_unexpected
- exception/std::make_exception_ptr
- exception/std::rethrow_exception
- exception/std::set_terminate
- exception/std::set_unexpected
- exception/std::terminate
- exception/std::uncaught_exception
- exception/std::unexpected
ms.assetid: c09ac569-5e35-4fe8-872d-ca5810274dd7
caps.latest.revision: 12
manager: ghogen
helpviewer_keywords:
- std::current_exception [C++]
- std::get_terminate [C++]
- std::get_unexpected [C++]
- std::make_exception_ptr [C++]
- std::rethrow_exception [C++]
- std::set_terminate [C++]
- std::set_unexpected [C++]
- std::terminate [C++]
- std::uncaught_exception [C++]
- std::unexpected [C++]
ms.openlocfilehash: 465c5b523855ea9a0cb89a3e27ed5e99d3f3f1da
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltexceptiongt-functions"></a>&lt;výjimka&gt; funkce

||||
|-|-|-|
|[current_exception](#current_exception)|[get_terminate –](#get_terminate)|[get_unexpected](#get_unexpected)|
|[make_exception_ptr](#make_exception_ptr)|[rethrow_exception](#rethrow_exception)|[set_terminate](#set_terminate)|
|[set_unexpected](#set_unexpected)|[Ukončení](#terminate)|[uncaught_exception](#uncaught_exception)|
|[unexpected](#unexpected)|

## <a name="current_exception"></a>  current_exception

Získá inteligentní ukazatel na aktuální výjimku.

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>Návratová hodnota

[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) objekt odkazující na aktuální výjimku.

### <a name="remarks"></a>Poznámky

Volání `current_exception` funkce v bloku catch. Pokud je k výjimce v cestě a výjimku, můžete zachytit blok catch `current_exception` funkce vrátí `exception_ptr` objekt, který odkazuje na výjimku. Funkce, jinak vrátí hodnotu null `exception_ptr` objektu.

`current_exception` Funkce zaznamená výjimka, která je na cestě bez ohledu na to, jestli `catch` Určuje příkaz [výjimka deklarace](../cpp/try-throw-and-catch-statements-cpp.md) příkaz.

Na konci se nazývá destruktor pro aktuální výjimky `catch` blokování, pokud není opětovné výjimku. Ale i v případě, že zavoláte `current_exception` fungovat v destruktoru, funkce vrátí hodnotu `exception_ptr` objekt, který odkazuje na aktuální výjimku.

Následná volání `current_exception` funkce vrátí `exception_ptr` objekty, které odkazují na různé kopie aktuální výjimku. V důsledku toho se objekty při porovnání jeví jako nerovné, protože odkazují na jiné kopie, i přesto, že kopie mají stejné binární hodnoty.

## <a name="make_exception_ptr"></a>  make_exception_ptr

Vytvoří [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) objekt, který obsahuje kopii výjimku.

```cpp
template <class E>
exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>Parametry

`Except` Třída s výjimkou ke kopírování. Obvykle, zadejte [třídy výjimek](../standard-library/exception-class.md) jako argument pro objekt `make_exception_ptr` fungovat, i když všechny třídy objektu může být argument.

### <a name="return-value"></a>Návratová hodnota

[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) objekt odkazující na kopii aktuální výjimky pro `Except`.

### <a name="remarks"></a>Poznámky

Volání `make_exception_ptr` funkce je ekvivalentní volání pro vyvolání výjimky C++, zachytávání v bloku catch a pak volání [current_exception](../standard-library/exception-functions.md#current_exception) funkci vrátíte `exception_ptr` objekt, který odkazuje na výjimku. Implementace společnosti Microsoft `make_exception_ptr` funkce je efektivnější než vyvolání a potom zachytávání výjimku.

Aplikace obvykle nevyžaduje, aby `make_exception_ptr` funkce a budeme bránit jeho použití.

## <a name="rethrow_exception"></a>  rethrow_exception

Vyvolá výjimku předanou jako parametr.

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>Parametry

`P` Zachycená výjimka znovu vyvolat. Pokud `P` je null [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr), funkce vyvolá [std::bad_exception](../standard-library/bad-exception-class.md).

### <a name="remarks"></a>Poznámky

Po uložení zachycená výjimka v `exception_ptr` objektu primární vlákno může zpracovat objekt. Ve vaší primární vláknu volání `rethrow_exception` fungovat společně s `exception_ptr` objektu jako její argument. `rethrow_exception` Extrahuje výjimky z funkce `exception_ptr` objekt a potom v kontextu primární vlákno vyvolá výjimku.

## <a name="get_terminate"></a>  get_terminate –

Získá aktuální `terminate_handler` funkce.

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a>  set_terminate –

Vytvoří nový `terminate_handler` má být volána v ukončení programu.

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

`fnew` Funkce, která se má volat při ukončení.

### <a name="return-value"></a>Návratová hodnota

Adresa předchozí funkce, která používá k volání na ukončení.

### <a name="remarks"></a>Poznámky

Vytvoří novou funkci [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) jako funkce * `fnew`. Proto `fnew` nesmí být nulový ukazatel. Funkce vrátí adresu předchozí ukončit obslužné rutiny.

### <a name="example"></a>Příklad

```cpp
// exception_set_terminate.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void termfunction()
{
    cout << "My terminate function called." << endl;
    abort();
}

int main()
{
    terminate_handler oldHandler = set_terminate(termfunction);

    // Throwing an unhandled exception would also terminate the program
    // or we could explicitly call terminate();

    //throw bad_alloc();
    terminate();
}

```

## <a name="get_unexpected"></a>  get_unexpected –

Získá aktuální `unexpected_handler` funkce.

```cpp
unexpected_handler get_unexpected();
```

## <a name="set_unexpected"></a>  set_unexpected –

Vytvoří nový `unexpected_handler` být, když je k neočekávané výjimce došlo.

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

`fnew` Funkce, která se má volat, když je došlo k neočekávané výjimce.

### <a name="return-value"></a>Návratová hodnota

Adresa předchozí `unexpected_handler`.

### <a name="remarks"></a>Poznámky

`fnew` nesmí být nulový ukazatel.

Standardní C++ vyžaduje, aby `unexpected` je volána, když funkce vyvolá výjimku, která není v seznamu throw. Aktuální implementace nepodporují. Následující příklad volání `unexpected` přímo, který potom volá `unexpected_handler`.

### <a name="example"></a>Příklad

```cpp
// exception_set_unexpected.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void uefunction()
{
    cout << "My unhandled exception function called." << endl;
    terminate(); // this is what unexpected() calls by default
}

int main()
{
    unexpected_handler oldHandler = set_unexpected(uefunction);

    unexpected(); // library function to force calling the
                  // current unexpected handler
}

```

## <a name="terminate"></a>  Ukončení

Zavolá obslužnou rutinu ukončení.

```cpp
void terminate();
```

### <a name="remarks"></a>Poznámky

Funkce volá obslužnou rutinu ukončit, funkci typu `void`. Pokud **ukončit** volá přímo programu, obslužné rutiny ukončení je ten naposledy nastavit voláním [set_terminate –](../standard-library/exception-functions.md#set_terminate). Pokud **ukončit** je volána pro některý z několika důvodů při vyhodnocování výrazu throw obslužné rutiny ukončení je ten, platit okamžitě po vyhodnocení výrazu throw.

Obslužné rutiny ukončení nemusí vracet jeho volajícího. Při spuštění programu, obslužné rutiny ukončení je funkce, která volá **abort**.

### <a name="example"></a>Příklad

V tématu [set_unexpected –](../standard-library/exception-functions.md#set_unexpected) příklad použití **ukončit**.

## <a name="uncaught_exception"></a>  uncaught_exception

Vrátí `true` pouze v případě, že vyvolaná výjimka je aktuálně zpracovávána.

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `true` po dokončení vyhodnocení výrazu throw a před dokončením inicializace deklarace výjimka v odpovídající obslužná rutina nebo volání [neočekávané](../standard-library/exception-functions.md#unexpected) v důsledku throw výraz. Konkrétně `uncaught_exception` vrátí `true` při volání z destruktor, který je volané během unwind výjimka. Na zařízeních `uncaught_exception` je podporován pouze na systém Windows CE 5.00 a vyšší verze, včetně platformy Windows Mobile 2005.

### <a name="example"></a>Příklad

```cpp
// exception_uncaught_exception.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>
#include <string>

class Test
{
public:
   Test( std::string msg ) : m_msg( msg )
   {
      std::cout << "In Test::Test(\"" << m_msg << "\")" << std::endl;
   }
   ~Test( )
   {
      std::cout << "In Test::~Test(\"" << m_msg << "\")" << std::endl
         << "        std::uncaught_exception( ) = "
         << std::uncaught_exception( )
         << std::endl;
   }
private:
    std::string m_msg;
};

// uncaught_exception will be true in the destructor
// for the object created inside the try block because
// the destructor is being called as part of the unwind.

int main( void )
   {
      Test t1( "outside try block" );
      try
      {
         Test t2( "inside try block" );
         throw 1;
      }
      catch (...) {
   }
}
```

```Output
In Test::Test("outside try block")
In Test::Test("inside try block")
In Test::~Test("inside try block")
        std::uncaught_exception( ) = 1
In Test::~Test("outside try block")
        std::uncaught_exception( ) = 0
```

## <a name="unexpected"></a>  neočekávané

Volá obslužnou rutinu neočekávané.

```cpp
void unexpected();
```

### <a name="remarks"></a>Poznámky

Standardní C++ vyžaduje, aby `unexpected` je volána, když funkce vyvolá výjimku, která není v seznamu throw. Aktuální implementace nepodporují. Příklad volání `unexpected` přímo, která volá neočekávané obslužná rutina.

Funkce volá obslužnou rutinu neočekávané, funkci typu `void`. Pokud `unexpected` volá přímo programu neočekávané obslužná rutina je ten naposledy nastavit voláním [set_unexpected –](../standard-library/exception-functions.md#set_unexpected).

Obslužné rutiny neočekávané nemusí vracet jeho volajícího. Spuštění s ho může ukončit:

- Vyvolání objekt typu uvedené v specifikace výjimek nebo objekt jakéhokoli typu, pokud je volána obslužná rutina neočekávané přímo pomocí programu.

- Vyvolání objekt typu [bad_exception](../standard-library/bad-exception-class.md).

- Volání metody [ukončit](../standard-library/exception-functions.md#terminate), **abort** nebo **ukončete**( `int`).

Při spuštění programu neočekávané obslužná rutina je funkce, která volá [ukončit](../standard-library/exception-functions.md#terminate).

### <a name="example"></a>Příklad

V tématu [set_unexpected –](../standard-library/exception-functions.md#set_unexpected) příklad použití **neočekávané.**

## <a name="see-also"></a>Viz také

[\<Výjimka >](../standard-library/exception.md)<br/>
