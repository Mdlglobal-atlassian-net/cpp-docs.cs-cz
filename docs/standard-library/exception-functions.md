---
title: '&lt;&gt; funkce výjimky'
ms.date: 11/04/2016
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
ms.openlocfilehash: ede3c828437aab1759c6711fc40511c69646a133
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076572"
---
# <a name="ltexceptiongt-functions"></a>&lt;&gt; funkce výjimky

## <a name="current_exception"></a><a name="current_exception"></a>current_exception

Získá inteligentní ukazatel na aktuální výjimku.

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>Návratová hodnota

Objekt [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) ukazující na aktuální výjimku.

### <a name="remarks"></a>Poznámky

Volání funkce `current_exception` v bloku catch. Je-li výjimka v letu a blok catch může výjimku zachytit, funkce `current_exception` vrátí objekt `exception_ptr`, který na výjimku odkazuje. V opačném případě funkce vrátí objekt `exception_ptr` s hodnotou null.

Funkce `current_exception` zachycuje výjimku, která je v letadle bez ohledu na to, zda příkaz **catch** Určuje příkaz [deklarace výjimky](../cpp/try-throw-and-catch-statements-cpp.md) .

Destruktor pro aktuální výjimku je volána na konci bloku **catch** , pokud výjimku nevyvoláte znovu. Nicméně i v případě, že zavoláte funkci `current_exception` v destruktoru, funkce vrátí objekt `exception_ptr`, který odkazuje na aktuální výjimku.

Po sobě jdoucí volání funkce `current_exception` vrací objekty `exception_ptr`, které odkazují na různé kopie aktuální výjimky. V důsledku toho se objekty při porovnání jeví jako nerovné, protože odkazují na jiné kopie, i přesto, že kopie mají stejné binární hodnoty.

## <a name="make_exception_ptr"></a><a name="make_exception_ptr"></a>make_exception_ptr

Vytvoří objekt [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) , který obsahuje kopii výjimky.

```cpp
template <class E>
    exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>Parametry

*S výjimkou*\
Třída s výjimkou pro kopírování Obvykle určíte objekt [třídy výjimky](../standard-library/exception-class.md) jako argument funkce `make_exception_ptr`, i když libovolný objekt třídy může být argumentem.

### <a name="return-value"></a>Návratová hodnota

Objekt [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) , který odkazuje na kopii aktuální výjimky pro *s výjimkou*.

### <a name="remarks"></a>Poznámky

Volání funkce `make_exception_ptr` je ekvivalentní k vyvolání C++ výjimky, jejímu zachycení v bloku catch a následným voláním funkce [current_exception](../standard-library/exception-functions.md#current_exception) pro vrácení objektu `exception_ptr`, který na výjimku odkazuje. Implementace funkce `make_exception_ptr` od Microsoftu je efektivnější než vyvolání a pak zachytí výjimku.

Aplikace obvykle nevyžaduje funkci `make_exception_ptr` a neodrazí se k jejímu použití.

## <a name="rethrow_exception"></a><a name="rethrow_exception"></a>rethrow_exception

Vyvolá výjimku předanou jako parametr.

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>Parametry

*P*\
Zachycená výjimka, kterou chcete znovu vyvolat. Pokud *P* je [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)null, funkce vyvolá [std:: bad_exception](../standard-library/bad-exception-class.md).

### <a name="remarks"></a>Poznámky

Po uložení zachycené výjimky do objektu `exception_ptr` může primární vlákno objekt zpracovat. V primárním vlákně zavolejte funkci `rethrow_exception` společně s objektem `exception_ptr` jako jeho argument. Funkce `rethrow_exception` extrahuje výjimku z objektu `exception_ptr` a poté vyvolá výjimku v kontextu primárního vlákna.

## <a name="get_terminate"></a><a name="get_terminate"></a>get_terminate

Získá aktuální funkci `terminate_handler`.

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a><a name="set_terminate"></a>set_terminate

Vytvoří nový `terminate_handler`, který se má volat při ukončení programu.

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

*fnew*\
Funkce, která má být volána při ukončení.

### <a name="return-value"></a>Návratová hodnota

Adresa předchozí funkce, která se používá k volání při ukončení.

### <a name="remarks"></a>Poznámky

Funkce vytvoří novou [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) jako funkci * *fnew*. Proto *fnew* nesmí být ukazatel s hodnotou null. Funkce vrátí adresu předchozí obslužné rutiny ukončení.

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

## <a name="get_unexpected"></a><a name="get_unexpected"></a>get_unexpected

Získá aktuální funkci `unexpected_handler`.

```cpp
unexpected_handler get_unexpected();
```

## <a name="rethrow_if_nested"></a><a name="rethrow_if_nested"></a>rethrow_if_nested

```cpp
template <class E>
    void rethrow_if_nested(const E& e);
```

### <a name="remarks"></a>Poznámky

Pokud není typ polymorfní třídy nebo pokud je `nested_exception` nepřístupná nebo nejednoznačná, neexistuje žádný vliv. V opačném případě provede dynamické přetypování.

## <a name="set_unexpected"></a><a name="set_unexpected"></a>set_unexpected

Vytvoří nový `unexpected_handler`, který má být v případě, že došlo k neočekávané výjimce.

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

*fnew*\
Funkce, která má být volána, když dojde k neočekávané výjimce.

### <a name="return-value"></a>Návratová hodnota

Adresa předchozí `unexpected_handler`.

### <a name="remarks"></a>Poznámky

*fnew* nesmí být ukazatel s hodnotou null.

C++ Standard vyžaduje, aby `unexpected` volána, když funkce vyvolá výjimku, která není v seznamu throw. Aktuální implementace to nepodporuje. Následující příklad volá `unexpected` přímo, což pak volá `unexpected_handler`.

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

## <a name="terminate"></a><a name="terminate"></a>ruší

Zavolá obslužnou rutinu ukončení.

```cpp
void terminate();
```

### <a name="remarks"></a>Poznámky

Funkce volá obslužnou rutinu ukončení, funkci typu **void**. Pokud je `terminate` volána přímo programem, obslužná rutina ukončení je ta, která byla naposledy nastavena voláním [set_terminate](../standard-library/exception-functions.md#set_terminate). Pokud je při vyhodnocování výrazu throw volána metoda `terminate` pro některý z několika dalších důvodů, obslužná rutina ukončení je ta, která se projeví okamžitě po vyhodnocení výrazu throw.

Obslužná rutina ukončení se nemůže vrátit volajícímu. Při spuštění programu je obslužná rutina ukončení funkce, která volá `abort`.

### <a name="example"></a>Příklad

Příklad použití `terminate`naleznete v tématu [set_unexpected](../standard-library/exception-functions.md#set_unexpected) .

## <a name="throw_with_nested"></a><a name="throw_with_nested"></a>throw_with_nested

```cpp
template <class T> [[noreturn]]
    void throw_with_nested(T&& t);
```

### <a name="remarks"></a>Poznámky

Vyvolá výjimku s vnořenými výjimkami.

## <a name="uncaught_exception"></a><a name="uncaught_exception"></a>uncaught_exception

Vrátí **hodnotu true** pouze v případě, že právě probíhá zpracování vyvolané výjimky.

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu pravda** po dokončení vyhodnocení výrazu throw a před dokončením inicializace deklarace výjimky v rámci vyhovující obslužné rutiny nebo volání [neočekávaného](../standard-library/exception-functions.md#unexpected) jako výsledek výrazu throw. Konkrétně `uncaught_exception` vrátí **hodnotu true** při volání z destruktoru, který je vyvolán během výjimky unwind. V zařízeních se `uncaught_exception` podporuje jenom v systém Windows CE 5,00 a vyšších verzích, včetně platforem Windows Mobile 2005.

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

## <a name="unexpected"></a><a name="unexpected"></a>neočekávané

Volá neočekávanou obslužnou rutinu.

```cpp
void unexpected();
```

### <a name="remarks"></a>Poznámky

C++ Standard vyžaduje, aby `unexpected` volána, když funkce vyvolá výjimku, která není v seznamu throw. Aktuální implementace to nepodporuje. Příklad volá `unexpected` přímo, která volá neočekávanou obslužnou rutinu.

Funkce volá neočekávanou obslužnou rutinu, funkci typu **void**. Pokud je `unexpected` volána přímo programem, je neočekávaná obslužná rutina ta, která byla naposledy nastavena voláním [set_unexpected](../standard-library/exception-functions.md#set_unexpected).

Neočekávaná obslužná rutina se nemůže vrátit volajícímu. Může ukončit provádění pomocí:

- Vyvolání objektu typu uvedeného ve specifikaci výjimky nebo objektu libovolného typu, pokud je neočekávaná obslužná rutina volána přímo programem.

- Došlo k vyvolání objektu typu [bad_exception](../standard-library/bad-exception-class.md).

- Volání příkazu [ukončit](../standard-library/exception-functions.md#terminate), `abort` nebo **ukončit**(`int`).

Při spuštění programu je neočekávaná obslužná rutina funkce, která volá funkci [ukončit](../standard-library/exception-functions.md#terminate).

### <a name="example"></a>Příklad

Příklad použití `unexpected`naleznete v tématu [set_unexpected](../standard-library/exception-functions.md#set_unexpected) .
