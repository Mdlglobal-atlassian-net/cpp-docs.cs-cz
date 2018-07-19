---
title: '&lt;paměť&gt; funkce | Dokumentace Microsoftu'
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
ms.openlocfilehash: d104d8a64dd60e5aaa7244e5bf5f535343f6e132
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957422"
---
# <a name="ltmemorygt-functions"></a>&lt;paměť&gt; funkce

||||
|-|-|-|
|[addressof](#addressof)|[align](#align)|[allocate_shared](#allocate_shared)|
|[const_pointer_cast](#const_pointer_cast)|[declare_no_pointers](#declare_no_pointers)|[declare_reachable](#declare_reachable)|
|[default_delete](#default_delete)|[dynamic_pointer_cast](#dynamic_pointer_cast)|[get_deleter](#get_deleter)|
|[get_pointer_safety](#get_pointer_safety)|[get_temporary_buffer](#get_temporary_buffer)|[make_shared](#make_shared)|
|[make_unique](#make_unique)|[owner_less](#owner_less)|[return_temporary_buffer](#return_temporary_buffer)|
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

*Val* objektu nebo funkce, pro které chcete získat adresu true.

### <a name="return-value"></a>Návratová hodnota

Skutečná adresa objektu nebo funkce odkazované *Val*, i když přetížený `operator&()` existuje.

### <a name="remarks"></a>Poznámky

## <a name="align"></a>  zarovnání

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

*Zarovnání* zarovnání čekající na pokus.

*Velikost* velikost v bajtech pro zarovnané úložiště.

*PTR* počáteční adresu dostupného nepřetržitého fondu úložiště používat. Tento parametr je také výstupní parametr a je nastavena na obsahovat novou počáteční adresu, pokud je zarovnání úspěšné. Pokud `align()` je neúspěšné, nebude tento parametr změněn.

*Místo* celkové místo k dispozici `align()` k použití při vytváření zarovnaného úložiště. Tento parametr je také výstupní parametr a obsahuje zbývající upravené místo ve vyrovnávací paměti úložiště po odečtení zarovnaného úložiště a veškeré přidružené režie.

Pokud `align()` je neúspěšné, nebude tento parametr změněn.

### <a name="return-value"></a>Návratová hodnota

Nulový ukazatel, pokud se požadovaná zarovnaná vyrovnávací paměť nevejde do dostupného prostoru; v opačném případě nová hodnota *Ptr*.

### <a name="remarks"></a>Poznámky

Upravené *Ptr* a *místo* parametry umožňují volat `align()` opakovaně na stejné vyrovnávací paměti, s možností jiných hodnot pro *zarovnání* a  *Velikost*. Následující fragment kódu ukazuje jedno použití `align()`.

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

Vytvoří `shared_ptr` na objekty, které jsou přiděleny a konstruovány pro daný typ pomocí zadaného alokátoru. Vrátí `shared_ptr`.

```cpp
template <class Type, class Allocator, class... Types>
shared_ptr<Type>
allocate_shared(Allocator Alloc, Types&&... Args);
```

### <a name="parameters"></a>Parametry

*ALLOC* Alokátor použitý k vytvoření objektů.

*Args* nuly nebo více argumentů, které se stanou objekty.

### <a name="remarks"></a>Poznámky

Funkce vytvoří objekt `shared_ptr<Type>`, ukazatel na `Type(Args...)` jak byl alokován a vytvořen *alokační*.

## <a name="const_pointer_cast"></a>  const_pointer_cast –

Const cast na shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
const_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Ty* typ řízený vráceného sdílený ukazatel.

*Další* typ řízený sdíleným ukazatelem argumentu.

*Další* sdíleným ukazatelem argumentu.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí prázdný shared_ptr objektu, pokud `const_cast<Ty*>(sp.get())` vrátí ukazatel s hodnotou null; v opačném případě vrátí [shared_ptr – třída](../standard-library/shared-ptr-class.md)\<Ty > objekt, který vlastní prostředek, který je vlastněn `sp`. Výraz `const_cast<Ty*>(sp.get())` musí být platný.

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

Informuje uvolňování paměti, že znaky v bloku paměti definované ukazatelem základní adresy a velikost bloku neobsahuje žádné sledovatelné ukazatele.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Adresa prvního znaku, který již obsahuje sledovatelné ukazatele.|
|*_Velikost*|Velikost bloku, která začíná na *ptr* , který neobsahuje žádné sledovatelné ukazatele.|

### <a name="remarks"></a>Poznámky

Informuje uvolňování funkce, která z rozsahu adres `[ ptr, ptr + _Size)` již nemusí obsahovat sledovatelné ukazatele. (Všechny ukazatele na přidělené úložiště nesmí být dereferencována pouze tehdy, pokud dostupné.)

## <a name="declare_reachable"></a>  declare_reachable

Informuje uvolňování paměti, že je uvedena adresa pro přidělení úložištěm a je k dispozici.

```cpp
void declare_reachable(void* ptr);
```

### <a name="parameters"></a>Parametry

*PTR* ukazatel na oblast dostupný, přidělené, platné úložiště.

### <a name="remarks"></a>Poznámky

Pokud *ptr* nemá hodnotu null, funkce informuje uvolňování, který *ptr* dále je dostupný (bodů na platný přidělené úložiště).

## <a name="default_delete"></a>  default_delete

Odstraní objektů přidělených s **operátor new**. Vhodný pro použití s `unique_ptr`.

```cpp
struct default_delete {
   constexpr default_delete() noexcept = default;
   template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
   default_delete(const default_delete<Other>&) noexcept;
   void operator()(T* Ptr) const noexcept;
};
```

### <a name="parameters"></a>Parametry

*PTR* ukazatel na objekt odstranit.

Další typ prvků v poli, která se má odstranit.

### <a name="remarks"></a>Poznámky

Třída šablony popisuje `deleter` , který odstraní skalární objektů přidělených s **operátor new**. to se hodí pro použití s šablony třídy `unique_ptr`. Má také explicitní specializace `default_delete<Type[]>`.

## <a name="dynamic_pointer_cast"></a>  dynamic_pointer_cast

Dynamické přetypování na shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
dynamic_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Ty* typ řízený vráceného sdílený ukazatel.

*Další* typ řízený sdíleným ukazatelem argumentu.

*SP* sdíleným ukazatelem argumentu.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí prázdný shared_ptr objektu, pokud `dynamic_cast<Ty*>(sp.get())` vrátí ukazatel s hodnotou null; v opačném případě vrátí [shared_ptr – třída](../standard-library/shared-ptr-class.md)\<Ty > objekt, který vlastní prostředek, který je vlastněn *sp* . Výraz `dynamic_cast<Ty*>(sp.get())` musí být platný.

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

Získáte odstraňovač z shared_ptr.

```cpp
template <class D, class Ty>
D* get_deleter(const shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parametry

*D* typ odstraňovače.

*Ty* typ řízený sdíleným ukazatelem.

*SP* sdílený ukazatel.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí ukazatel odstraňovač typu *D* , který patří do [shared_ptr – třída](../standard-library/shared-ptr-class.md) objekt *sp*. Pokud *sp* nemá žádné deleter nebo pokud není typu jeho deleter *D* funkce vrátí 0.

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

Funkce vrátí typ zabezpečení ukazatele předpokládá, že automatické uvolňování.

## <a name="get_temporary_buffer"></a>  get_temporary_buffer

Přidělí dočasné úložiště pro řadu prvků, která není větší než zadaný počet prvků.

```cpp
template <class Type>
pair<Type *, ptrdiff_t> get_temporary_buffer(ptrdiff_t count);
```

### <a name="parameters"></a>Parametry

*počet* je maximální počet prvků požadované paměti, které mají být přiděleny.

### <a name="return-value"></a>Návratová hodnota

A `pair` jehož první komponenta je ukazatel na paměti, který byl přiřazen, a jehož sekundy poskytuje velikost vyrovnávací paměti, určující největší počet prvků, které může uchovávat.

### <a name="remarks"></a>Poznámky

Funkce vytvoří požadavek na paměť a nemusí proběhnout úspěšně. Pokud žádná vyrovnávací paměť je přidělena, funkce vrátí pár druhého rovná součástí na hodnotu nula a první komponenta rovna ukazatele s hodnotou null.

Tato funkce by měla sloužit pouze pro paměti, která je pouze dočasné.

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

## <a name="make_shared"></a>  make_shared

Vytváří a vrací `shared_ptr` odkazující na alokované objekty vytvořené z nuly nebo více argumentů pomocí výchozího alokátoru. Přiděluje a vytvoří oba objekt zadaného typu a `shared_ptr` ke správě sdílené vlastnictví objektu a vrátí `shared_ptr`.

```cpp
template <class Type, class... Types>
shared_ptr<Type>
make_shared(Types&&... _Args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Args*|Nula nebo více argumentů konstruktoru. Funkce odvodí, které přetížení konstruktoru bude vyvoláno na základě poskytnutých argumentů.|

### <a name="remarks"></a>Poznámky

Použití `make_shared` jako jednoduchý a efektivnější způsob, jak vytvořit objekt a `shared_ptr` ke správě sdílený přístup k objektu ve stejnou dobu. Sémanticky tyto dva příkazy jsou ekvivalentní:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Však první příkaz vytvoří dvě přidělení a pokud přidělení `shared_ptr` selže po přidělení `Example` objekt proběhla úspěšně, potom nepojmenované `Example` úniku objektu. Příkaz, který používá `make_shared` je jednodušší, protože je potřebný jenom jednu funkci volání. To je mnohem efektivnější, protože knihovny může být jedna alokace pro objekt a inteligentní ukazatel. To je rychlejší a vede k méně fragmentace paměti a neexistuje možnost výjimky na jeden přidělení, ale nikoli u druhého. Lepší místo pro kód, který odkazuje na objekt a aktualizací, které se počítá odkaz v inteligentní ukazatel vyšší výkon.

Zvažte použití [make_unique](../standard-library/memory-functions.md#make_unique) Pokud nepotřebujete sdílený přístup k objektu. Použití [allocate_shared](../standard-library/memory-functions.md#allocate_shared) Pokud je třeba zadat vlastního alokátoru pro objekt. Nemůžete použít `make_shared` Pokud objektu vyžaduje vlastním odstraňovačem, protože neexistuje žádný způsob, jak předat jako argument odstraňovač.

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

Vytvoří a vrátí [unique_ptr](../standard-library/unique-ptr-class.md) na objekt zadaného typu, který je vyroben pomocí zadaných argumentů.

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

*T* typu objektu, který `unique_ptr` bude odkazovat.

*Typy* typy argumentů konstruktoru dané podle *Args*.

*Args* argumenty, které mají být předána do konstruktoru objektu typu *T*.

*Elem* pole elementů typu *T*.

*Velikost* počet prvků k přidělení místa pro nové pole.

### <a name="remarks"></a>Poznámky

První přetížení se používá pro jednotlivé objekty, druhé přetížení je vyvoláno pro pole a třetí přetížení zabraňuje zabrání v zadání velikost pole v argumentu typu (make_unique\<T [N] >); Tato konstrukce není podporován. aktuální Standard. Při použití `make_unique` k vytvoření `unique_ptr` pro pole, je třeba inicializovat prvky pole zvlášť. Pokud uvažujete o tomto přetížení, možná je vhodnější, je použít [std::vector](../standard-library/vector-class.md).

Protože `make_unique` pečlivě je implementována pro bezpečnost výjimek, doporučujeme, abyste použili `make_unique` místo přímého volání `unique_ptr` konstruktory.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `make_unique`. Další příklady najdete v tématu [postupy: vytváření a používání instancí ukazatelů unique_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Když se zobrazí chyba C2280 v souvislosti s `unique_ptr`, je téměř jistě vzhledem k tomu, že se pokoušíte volání kopie konstruktoru, který je to Odstraněná funkce.

## <a name="owner_less"></a>  owner_less

Umožňuje smíšené porovnání sdílených a slabých ukazatelů na základě vlastnictví. Vrátí **true** pokud levý parametr je řazen před pravý parametr pomocí členské funkce `owner_before`.

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

*_vlevo* sdílené nebo slabý ukazatel.

*správné* sdílené nebo slabý ukazatel.

### <a name="remarks"></a>Poznámky

Šablony třídy definují jejich členské operátory jako vracející `left.owner_before(right)`.

## <a name="return_temporary_buffer"></a>  return_temporary_buffer

Zruší přidělení dočasné paměti, která byla přidělena pomocí `get_temporary_buffer` šablony funkce.

```cpp
template <class Type>
void return_temporary_buffer(Type* _Pbuf);
```

### <a name="parameters"></a>Parametry

*_Pbuf* ukazatel na uvolnění paměti.

### <a name="remarks"></a>Poznámky

Tato funkce by měla sloužit pouze pro paměti, která je pouze dočasné.

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

## <a name="static_pointer_cast"></a>  static_pointer_cast –

Statické přetypování na shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
static_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Ty* typ řízený vráceného sdílený ukazatel.

*Další* typ řízený sdíleným ukazatelem argumentu.

*Další* sdíleným ukazatelem argumentu.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí prázdný shared_ptr objektu, pokud `sp` prázdný `shared_ptr` objektu; v opačném případě vrátí [shared_ptr – třída](../standard-library/shared-ptr-class.md)\<Ty > objekt, který vlastní prostředek, který je vlastněn `sp`. Výraz `static_cast<Ty*>(sp.get())` musí být platný.

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

Dva objekty shared_ptr nebo weak_ptr prohodit.

```cpp
template <class Ty, class Other>
void swap(shared_ptr<Ty>& left, shared_ptr<Other>& right);

template <class Ty, class Other>
void swap(weak_ptr<Ty>& left, weak_ptr<Other>& right);
```

### <a name="parameters"></a>Parametry

*Ty* typ řízený levé sdílené/weak ukazatele.

*Další* typ řízený ukazatelem právo sdílet/weak.

*levé* levé sdílené/weak ukazatele.

*správné* právo sdílet/weak ukazatele.

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

Informuje uvolňování funkci, která z rozsahu adres `[ptr, ptr + _Size)` mohou nyní obsahovat sledovatelné ukazatele.

## <a name="undeclare_reachable"></a>  undeclare_reachable

Odebere deklaraci dostupnosti pro zadané umístění v paměti.

```cpp
template <class Type>
Type *undeclare_reachable(Type* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na adresu paměti deklarovat není dostupný.|

### <a name="remarks"></a>Poznámky

Pokud *ptr* není **nullptr**, funkce informuje uvolňování, který *ptr* už není dostupný. Vrátí rovna bezpečně odvozené ukazatel, který porovnává *ptr*.

## <a name="uninitialized_copy"></a>  uninitialized_copy

Zkopíruje objekty ze zadaného zdrojového rozsahu do neinicializovaného cílového rozsahu.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(InputIterator first, InputIterator last, ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

*první* vstupní iterátor adresující první prvek ve zdrojovém rozsahu.

*poslední* vstupní iterátor adresující poslední prvek ve zdrojovém rozsahu.

*DEST* dopředný iterátor adresující první prvek v cílovém rozsahu.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující první pozici za cílovým rozsahem, pokud zdrojová oblast byla prázdná.

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

*první* vstupní iterátor, který odkazuje na objekt, který chcete zkopírovat.

*počet* A podepsaný nebo nepodepsaný řetězec typu celé číslo určující počet, kolikrát má objekt kopírovat.

*DEST* dopředný iterátor, který odkazuje na kam se obrátit nových kopií.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující první pozici za cílem. Pokud zdrojová oblast byla prázdná, iterátor adresuje *první*.

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

*první* dopředný iterátor adresující první prvek v cílovém rozsahu, který má být zahájeno.

*poslední* dopředný iterátor adresující poslední prvek v cílovém rozsahu, který má být zahájeno.

*Val* hodnota, která má sloužit k inicializaci cílového rozsahu.

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

*první* dopředný iterátor adresující první prvek v cílovém rozsahu, má být iniciován.

*počet* počet prvků, které mají být inicializovány.

*Val* hodnota, která má sloužit k inicializaci cílového rozsahu.

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

## <a name="see-also"></a>Viz také:

[\<paměť >](../standard-library/memory.md)<br/>
