---
title: '&lt;paměť&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::default_delete
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
- memory/std::get_temporary_buffer
- memory/std::return_temporary_buffer
dev_langs:
- C++
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.workload:
- cplusplus
ms.openlocfilehash: 676f6522a5625103a00310c6ce5353ce40da9359
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltmemorygt-functions"></a>&lt;paměť&gt; funkce

||||
|-|-|-|
|[addressof](#addressof)|[align](#align)|[allocate_shared](#allocate_shared)|
|[const_pointer_cast](#const_pointer_cast)|[declare_no_pointers](#declare_no_pointers)|[declare_reachable](#declare_reachable)|
|[default_delete](#default_delete)|[dynamic_pointer_cast](#dynamic_pointer_cast)|[get_deleter](#get_deleter)|
|[get_pointer_safety](#get_pointer_safety)|[get_temporary_buffer](#get_temporary_buffer)|[make_shared](#make_shared)|
|[make_unique](#make_unique)|[owner_less –](#owner_less)|[return_temporary_buffer](#return_temporary_buffer)|
|[static_pointer_cast](#static_pointer_cast)|[swap (standardní knihovna C++)](#swap)|[undeclare_no_pointers](#undeclare_no_pointers)|
|[undeclare_reachable](#undeclare_reachable)|[uninitialized_copy](#uninitialized_copy)|[uninitialized_copy_n](#uninitialized_copy_n)|
|[uninitialized_fill](#uninitialized_fill)|[uninitialized_fill_n](#uninitialized_fill_n)|

## <a name="addressof"></a>  AddressOf

Získá adresu true objektu.

```cpp
template <class T>
T* addressof(T& Val);
```

### <a name="parameters"></a>Parametry

`Val` Objekt nebo funkce, pro které chcete získat adresu hodnotu true.

### <a name="return-value"></a>Návratová hodnota

Skutečná adresa objektu nebo funkce odkazuje `Val`, i když přetížené `operator&()` existuje.

### <a name="remarks"></a>Poznámky

## <a name="align"></a>  Zarovnat

Přizpůsobí úložiště určité velikosti, zarovnané danou specifikací zarovnání, do první možné adresy daného úložiště.

```cpp
void* align(
    size_t Alignment, // input
    size_t Size,      // input
    void*& Ptr,        // input/output
    size_t& Space     // input/output
);
```

### <a name="parameters"></a>Parametry

`Alignment` Zarovnání vázána k pokusu o.

`Size` Velikost v bajtech pro zarovnaný úložiště.

`Ptr` Počáteční adresa fondu úložiště k dispozici souvislý se mají použít. Tento parametr je také výstupní parametr a je nastaven tak, aby obsahovala nové počáteční adresa Pokud zarovnání úspěšné. Pokud `align()` je úspěšné, tento parametr se nemění.

`Space` Celkové místo k dispozici pro `align()` používat při vytváření zarovnán úložiště. Tento parametr je také výstupní parametr a obsahuje zbývající upravené místo ve vyrovnávací paměti úložiště po odečtení zarovnaného úložiště a veškeré přidružené režie.

Pokud `align()` je úspěšné, tento parametr se nemění.

### <a name="return-value"></a>Návratová hodnota

Ukazatele null. Pokud žádost zarovnán vyrovnávací paměti by začlenit do dostupného místa; jinak nová hodnota `Ptr`.

### <a name="remarks"></a>Poznámky

Upravenou `Ptr` a `Space` parametry umožňují volání `align()` opakovaně na stejné vyrovnávací paměť, případně s různé hodnoty pro `Alignment` a `Size`. Následující fragment kódu ukazuje jedno použití `align()`.

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a>  allocate_shared

Vytvoří `shared_ptr` na objekty, které jsou přidělené a vytvořená pro daný typ pomocí zadané přidělujícího modulu. Vrátí `shared_ptr`.

```cpp
template <class Type, class Allocator, class... Types>
shared_ptr<Type>
allocate_shared(Allocator Alloc, Types&&... Args);
```

### <a name="parameters"></a>Parametry

`Alloc` Allocator slouží k vytvoření objektů.

`Args` Nula nebo více argumentů, které se objekty.

### <a name="remarks"></a>Poznámky

Funkce vytvoří objekt `shared_ptr<Type>`, ukazatel na `Type(Args...)` jako přidělené a vytvořený pomocí `Alloc`.

## <a name="const_pointer_cast"></a>  const_pointer_cast

Const přetypování na shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
const_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

`Ty` Typ řízené vrácený sdílené ukazatele.

`Other` Typ řízené sdílené ukazatele argument.

`Other` Argument sdílené ukazatel.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí objekt shared_ptr prázdný, pokud `const_cast<Ty*>(sp.get())` vrátí ukazatel s hodnotou null; v opačném případě vrátí [shared_ptr – třída](../standard-library/shared-ptr-class.md)\<Ty > objekt, který je vlastníkem prostředku, který je vlastněn `sp`. Výraz `const_cast<Ty*>(sp.get())` musí být platné.

### <a name="example"></a>Příklad

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

*sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a>  declare_no_pointers

Informuje o uvolňování, který znaky v bloku paměti definované ukazatel základní adresa a velikost bloku obsahuje žádné zjistitelný ukazatele.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`ptr`|Adresa prvního znaku, který již obsahuje zjistitelný ukazatele.|
|`_Size`|Velikost bloku, která se spouští v `ptr` obsahující žádné zjistitelný ukazatele.|

### <a name="remarks"></a>Poznámky

Funkce žádné systém uvolňování paměti informuje o tom, který rozsah adres `[ ptr, ptr + _Size)` již neobsahovaly zjistitelný ukazatele. (Všechny odkazy na úložiště přidělené nesmí přímo odkázat pouze tehdy, pokud dostupná.)

## <a name="declare_reachable"></a>  declare_reachable

Informuje uvolňování paměti, že je uvedena adresa pro přidělení úložištěm a je k dispozici.

```cpp
void declare_reachable(void* ptr);
```

### <a name="parameters"></a>Parametry

`ptr` Ukazatel na oblast dostupný, přidělené, platné úložiště.

### <a name="remarks"></a>Poznámky

Pokud `ptr` nemá hodnotu null, funkce žádné systém uvolňování paměti informuje o tom, který `ptr` dále je dostupný (bodů na platné úložiště přidělené).

## <a name="default_delete"></a>  default_delete –

Odstraní objektů, kterým je přiřazen `operator new`. Vhodné pro použití s `unique_ptr`.

```cpp
struct default_delete {
   constexpr default_delete() noexcept = default;
   template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
   default_delete(const default_delete<Other>&) noexcept;
   void operator()(T* Ptr) const noexcept;
};
```

### <a name="parameters"></a>Parametry

`Ptr` Ukazatel na objekt, který chcete odstranit.

Další typ elementů v poli, aby ji odstranit.

### <a name="remarks"></a>Poznámky

Popisuje třídy šablony `deleter` , odstraní skalární objektů, kterým je přiřazen `operator new`, je vhodné pro použití s třídou šablony `unique_ptr`. Explicitní specializace je také `default_delete<Type[]>`.

## <a name="dynamic_pointer_cast"></a>  dynamic_pointer_cast

Dynamické přetypování na shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
dynamic_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

`Ty` Typ řízené vrácený sdílené ukazatele.

`Other` Typ řízené sdílené ukazatele argument.

`sp` Argument sdílené ukazatel.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí objekt shared_ptr prázdný, pokud `dynamic_cast<Ty*>(sp.get())` vrátí ukazatel s hodnotou null; v opačném případě vrátí [shared_ptr – třída](../standard-library/shared-ptr-class.md)\<Ty > objekt, který je vlastníkem prostředku, který je vlastněn `sp`. Výraz `dynamic_cast<Ty*>(sp.get())` musí být platné.

### <a name="example"></a>Příklad

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int val;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="get_deleter"></a>  get_deleter –

Metoda odstranění sám shared_ptr.

```cpp
template <class D, class Ty>
D* get_deleter(const shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parametry

`D` Typ metoda odstranění.

`Ty` Typ řízené sdílené ukazatele.

`sp` Sdílené ukazatel.

### <a name="remarks"></a>Poznámky

Funkce šablony vrací ukazatel na metoda odstranění typu `D` který patří do [shared_ptr – třída](../standard-library/shared-ptr-class.md) objekt `sp`. Pokud `sp` nemá žádná metoda odstranění nebo pokud metoda jeho odstranění není typu `D` funkce vrátí hodnotu 0.

### <a name="example"></a>Příklad

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
};

struct deleter
{
    void operator()(base *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->val = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->val = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}

```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>  get_pointer_safety

Vrátí typ zabezpečení ukazatele uvedený v rámci uvolňování paměti.

```cpp
pointer_safety get_pointer_safety();
```

### <a name="remarks"></a>Poznámky

Funkce vrátí hodnotu typu ukazatele zabezpečení předpokládá ve všech automatické systém uvolňování paměti.

## <a name="get_temporary_buffer"></a>  get_temporary_buffer

Přidělí dočasné úložiště pro řadu prvků, která není větší než zadaný počet prvků.

```cpp
template <class Type>
pair<Type *, ptrdiff_t> get_temporary_buffer(ptrdiff_t count);
```

### <a name="parameters"></a>Parametry

`count` Maximální počet elementů si vyžádal, pro kterou je třeba přidělit paměť.

### <a name="return-value"></a>Návratová hodnota

A `pair` jejichž první součást je ukazatel na paměti, který byl přidělen a jehož druhá součást dává velikost vyrovnávací paměti, určující největší počet prvků, které může uložit.

### <a name="remarks"></a>Poznámky

Funkce usnadňuje žádost o paměti a nemusí být úspěšné. Pokud je přidělena žádná vyrovnávací paměť, funkce vrátí hodnotu pár s druhou součást rovná nule a první součást rovno ukazatele null.

Tato funkce slouží pouze pro paměť, která je dočasný.

### <a name="example"></a>Příklad

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
   // Create an array of ints
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
   int count = sizeof ( intArray ) / sizeof ( int );
   cout << "The number of integers in the array is: "
      << count << "." << endl;

   pair<int *, ptrdiff_t> resultPair;
   resultPair = get_temporary_buffer<int>( count );

   cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a>  make_shared –

Vytváří a vrací `shared_ptr` odkazující na alokované objekty vytvořené z nuly nebo více argumentů pomocí výchozího alokátoru. Přiděluje a vytvoří obou objekt zadaného typu a `shared_ptr` ke správě sdílených vlastnictví objektu, a vrátí `shared_ptr`.

```cpp
template <class Type, class... Types>
shared_ptr<Type>
make_shared(Types&&... _Args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`_Args`|Argumenty konstruktoru nula nebo více. Funkce odvodí, které přetížení konstruktoru bude vyvoláno na základě poskytnutých argumentů.|

### <a name="remarks"></a>Poznámky

Použití `make_shared` jako jednoduchý a efektivnější způsob pro vytvoření objektu a `shared_ptr` ke správě sdílený přístup k objektu ve stejnou dobu. Sémanticky odpovídají těchto dvou příkazů:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Však první příkaz vytvoří dvě přidělení a pokud přidělení `shared_ptr` selže po přidělení `Example` objekt byl úspěšný, pak nepojmenované `Example` došlo k úniku objekt. Příkaz, který používá `make_shared` je jednodušší, protože je zahrnutých jenom jednu funkci volání. Je efektivnější, protože knihovny můžete provést jeden přidělení pro objekt a inteligentní ukazatele. Tím se oba rychleji a vede k menší fragmentace paměti a neexistuje možnost výjimky na jednu přidělení, ale ne na druhou. Výkon je vyšší, tím lepší polohu pro kód, který odkazuje na objekt a aktualizace, které odkaz spočítá v inteligentní ukazatele.

Zvažte použití [make_unique](../standard-library/memory-functions.md#make_unique) Pokud nepotřebujete sdílený přístup k objektu. Použití [allocate_shared](../standard-library/memory-functions.md#allocate_shared) Pokud budete muset zadat vlastní přidělení pro objekt. Nemůžete použít `make_shared` Pokud objektu vyžaduje vlastní metoda odstranění, protože neexistuje žádný způsob, jak metoda odstranění předat jako argument.

Následující příklad ukazuje, jak vytvořit sdílené odkazy na typ vyvoláním konkrétního konstruktoru přetížení.

### <a name="example"></a>Příklad

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
   std::wstring title_;
   std::wstring artist_;

   Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
   Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers() {
   // Okay, but less efficient to have separate allocations for
   // Song object and shared_ptr control block.
   auto song = new Song(L"Ode to Joy", L"Beethoven");
   std::shared_ptr<Song> sp0(song);

   // Use make_shared function when possible. Memory for control block
   // and Song object are allocated in the same call:
   auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
   auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

   // make_shared infers which constructor to use based on the arguments.
   auto sp3 = std::make_shared<Song>(L"Greensleeves");

   // The playlist vector makes copies of the shared_ptr pointers.
   std::vector<std::shared_ptr<Song>> playlist;
   playlist.push_back(sp0);
   playlist.push_back(sp1);
   playlist.push_back(sp2);
   playlist.push_back(sp3);
   playlist.push_back(sp1);
   playlist.push_back(sp2);
   for (auto&& sp : playlist) {
      std::wcout << L"Playing " << sp->title_ <<
         L" by " << sp->artist_ << L", use count: " <<
         sp.use_count() << std::endl;
   }
}

int main() {
   CreateSharedPointers();
}
```

Tento příklad vytvoří tento výstup:

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a>  make_unique

Vytvoří a vrátí [unique_ptr](../standard-library/unique-ptr-class.md) na objekt zadaného typu, který je vytvořený pomocí zadaných argumentů.

```cpp
// make_unique<T>
template <class T, class... Types>
unique_ptr<T>
make_unique(Types&&... Args)
{
    return (unique_ptr<T>(new T(forward<Types>(Args)...)));
}

// make_unique<T[]>
template <class T>
make_unique(size_t Size)
{
    return (unique_ptr<T>(new Elem[Size]()));
}

// make_unique<T[N]> disallowed
template <class T, class... Types>
typename enable_if<extent<T>::value != 0, void>::type
make_unique(Types&&...) = delete;
```

### <a name="parameters"></a>Parametry

`T` Typ objektu, který `unique_ptr` bude odkazovat na.

`Types` Typy argumenty konstruktoru určeného `Args`.

`Args` Argumenty, které mají být předána do konstruktoru objektu na objekt typu `T`.

`Elem` Pole elementy typu `T`.

`Size` Počet elementů k přidělení místa pro nové pole.

### <a name="remarks"></a>Poznámky

První přetížení se používá pro jednotlivé objekty, je vyvolána druhá přetížení pro pole a třetí přetížení brání brání určení velikost pole v argument typu (make_unique\<T [N] >); nepodporuje tento konstrukce podle aktuálního standard. Při použití `make_unique` k vytvoření `unique_ptr` do pole, je nutné inicializovat elementy pole samostatně. Pokud uvažujete o toto přetížení, pravděpodobně lepší volbou je používat [std::vector](../standard-library/vector-class.md).

Protože `make_unique` pečlivě je implementována pro bezpečnost výjimek, doporučujeme, abyste použili `make_unique` namísto přímo volání `unique_ptr` konstruktory.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `make_unique`. Další příklady najdete v tématu [postupy: vytváření a používání instancí ukazatelů unique_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Až se zobrazí chyba C2280 ve spojení s `unique_ptr`, je skoro určitě vzhledem k tomu, že se pokoušíte vyvolat kopírovací konstruktor, který je odstraněný funkce.

## <a name="owner_less"></a>  owner_less –

Umožňuje smíšené porovnání sdílených a slabých ukazatelů na základě vlastnictví. Vrátí `true` pokud levý parametr je seřadí před pravý parametr funkce člen `owner_before`.

```cpp
template <class Type>
struct owner_less; // not defined

template <class Type>
struct owner_less<shared_ptr<Type>> {
    bool operator()(
    const shared_ptr<Type>& left,
    const shared_ptr<Type>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Type>& right);
};

template <class Type>
struct owner_less<weak_ptr<Type>>
    bool operator()(
    const weak_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Ty>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);
};
```

### <a name="parameters"></a>Parametry

`_left` Sdílené nebo slabé ukazatel.

`right` Sdílené nebo slabé ukazatel.

### <a name="remarks"></a>Poznámky

Šablony třídy definují jejich operátory členy jako vrácení `left.owner_before(right)`.

## <a name="return_temporary_buffer"></a>  return_temporary_buffer

Zruší přidělení dočasné paměti, který byl přidělen s použitím `get_temporary_buffer` funkce šablony.

```cpp
template <class Type>
void return_temporary_buffer(Type* _Pbuf);
```

### <a name="parameters"></a>Parametry

*_Pbuf* ukazatel na paměť k zrušení přiřazení.

### <a name="remarks"></a>Poznámky

Tato funkce slouží pouze pro paměť, která je dočasný.

### <a name="example"></a>Příklad

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
   // Create an array of ints
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300 };
   int count = sizeof ( intArray ) / sizeof ( int );
   cout << "The number of integers in the array is: "
         << count << "." << endl;

   pair<int *, ptrdiff_t> resultPair;
   resultPair = get_temporary_buffer<int>( count );

   cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

   int* tempBuffer = resultPair.first;

   // Deallocates memory allocated with get_temporary_buffer
   return_temporary_buffer ( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
 could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>  static_pointer_cast

Statické přetypování na shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
static_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

`Ty` Typ řízené vrácený sdílené ukazatele.

`Other` Typ řízené sdílené ukazatele argument.

`Other` Argument sdílené ukazatel.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí objekt shared_ptr prázdný, pokud `sp` je prázdná `shared_ptr` objektu; v opačném případě vrátí [shared_ptr – třída](../standard-library/shared-ptr-class.md)\<Ty > objekt, který je vlastníkem prostředku, který je vlastněn `sp`. Výraz `static_cast<Ty*>(sp.get())` musí být platné.

### <a name="example"></a>Příklad

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="swap"></a>  swap (standardní knihovna C++)

Swap – dvě shared_ptr nebo weak_ptr objektů.

```cpp
template <class Ty, class Other>
void swap(shared_ptr<Ty>& left, shared_ptr<Other>& right);

template <class Ty, class Other>
void swap(weak_ptr<Ty>& left, weak_ptr<Other>& right);
```

### <a name="parameters"></a>Parametry

`Ty` Typ řízené levé sdílené nebo weak ukazatele.

`Other` Typ řízené právo sdílet nebo weak ukazatele.

`left` Levé sdílené nebo weak ukazatel.

`right` Ukazatel právo sdílet nebo příliš slabé.

### <a name="remarks"></a>Poznámky

Šablona funkce volání `left.swap(right)`.

### <a name="example"></a>Příklad

```cpp
// std__memory__swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="undeclare_no_pointers"></a>  undeclare_no_pointers

Informuje uvolňování paměti, že některé znaky v bloku paměti definované ukazatelem základní adresy a velikostí bloku mohou nyní obsahovat sledovatelné ukazatele.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="remarks"></a>Poznámky

Funkce žádné systém uvolňování paměti informuje o tom, který rozsah adres `[ptr, ptr + _Size)` teď může obsahovat zjistitelný ukazatele.

## <a name="undeclare_reachable"></a>  undeclare_reachable

Odvolá prohlášení o dostupnosti pro umístění zadaná paměťová.

```cpp
template <class Type>
Type *undeclare_reachable(Type* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`ptr`|Ukazatel na adresu paměti deklarovat není dostupný.|

### <a name="remarks"></a>Poznámky

Pokud `ptr` není `nullptr`, funkce žádné systém uvolňování paměti informuje o tom, který `ptr` není dostupný. Vrátí rovna bezpečně odvozené ukazatele, který porovnává `ptr`.

## <a name="uninitialized_copy"></a>  uninitialized_copy

Zkopíruje objekty ze zadaného zdrojového rozsahu do neinicializovaného cílového rozsahu.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(InputIterator first, InputIterator last, ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterovat prvním elementem v zdrojový rozsah adres.

`last` Vstupní iterovat posledním prvkem v zdrojový rozsah adres.

`dest` Předat dál iterator adresování prvním elementem v cílové oblasti.

### <a name="return-value"></a>Návratová hodnota

Předat dál iterator adresování první pozici nad rámec cílový rozsah, pokud zdrojový rozsah byla prázdná.

### <a name="remarks"></a>Poznámky

Tento algoritmus umožňuje zrušení spinové interakce přidělení paměti z konstrukce objektu.

Funkce šablony efektivně provede:

```cpp
while (first != last) {
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

### <a name="example"></a>Příklad

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : val(x) {}
    int get() { return val; }
private:
    int val;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    int i;
    cout << "The initialized Array contains " << N << " elements: ";
    for (i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a>  uninitialized_copy_n

Vytvoří kopii zadaného počtu prvků ze vstupního iterátoru. Kopie jsou umístěny v dopředném iterátoru.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator, který odkazuje na objekt, který chcete kopírovat.

`count` Typ celé číslo se znaménkem nebo bez znaménka určující počet opakování pro kopírování objektu.

`dest` Iterator předat dál, který odkazuje na kde přejděte nové kopie.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující první pozici za cílem. Pokud zdrojový rozsah byla prázdná, iterator adresy `first`.

### <a name="remarks"></a>Poznámky

Funkce šablony efektivně provede následující:

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

## <a name="uninitialized_fill"></a>  uninitialized_fill

Zkopíruje objekty ze zadané hodnoty do neinicializované cílové oblasti.

```cpp
template <class ForwardIterator, class Type>
void uninitialized_fill(ForwardIterator first, ForwardIterator last, const Type& val);
```

### <a name="parameters"></a>Parametry

`first` Předat dál iterator adresování prvním elementem v cílovém rozsahu, který má být zahájeno.

`last` Předat dál iterator adresování posledním prvkem v cílovém rozsahu, který má být zahájeno.

`val` Hodnota, který se má použít k chybě při inicializaci cílový rozsah.

### <a name="remarks"></a>Poznámky

Tento algoritmus umožňuje zrušení spinové interakce přidělení paměti z konstrukce objektu.

Funkce šablony efektivně provede:

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (val);
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

### <a name="example"></a>Příklad

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer {         // No default constructor
   public:
      Integer( int x ) : val( x ) {}
      int get( ) { return val; }
   private:
      int val;
};

int main( )
{
   const int N = 10;
   Integer val ( 25 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill( Array, Array + N, val );
   int i;
   cout << "The initialized Array contains: ";
      for ( i = 0 ; i < N; i++ )
      {
         cout << Array [ i ].get( ) << " ";
      }
   cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>  uninitialized_fill_n

Zkopíruje objekty zadané hodnoty do zadaného počtu prvků do neinicializovaného cílového rozsahu.

```cpp
template <class FwdIt, class Size, class Type>
void uninitialized_fill_n(ForwardIterator first, Size count, const Type& val);
```

### <a name="parameters"></a>Parametry

`first` Předat dál iterator adresování prvním elementem v cílový rozsah spustit.

`count` Počet elementů inicializovat.

`val` Hodnota, který se má použít k chybě při inicializaci cílový rozsah.

### <a name="remarks"></a>Poznámky

Tento algoritmus umožňuje zrušení spinové interakce přidělení paměti z konstrukce objektu.

Funkce šablony efektivně provede:

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(val);
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

### <a name="example"></a>Příklad

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer {   // No default constructor
public:
   Integer( int x ) : val( x ) {}
   int get( ) { return val; }
private:
   int val;
};

int main() {
   const int N = 10;
   Integer val ( 60 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill_n( Array, N, val );  // C4996
   int i;
   cout << "The uninitialized Array contains: ";
   for ( i = 0 ; i < N; i++ )
      cout << Array [ i ].get( ) <<  " ";
}
```

## <a name="see-also"></a>Viz také

[\<paměť >](../standard-library/memory.md)<br/>
