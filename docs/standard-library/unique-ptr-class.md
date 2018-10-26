---
title: unique_ptr – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::unique_ptr
- memory/std::unique_ptr::deleter_type
- memory/std::unique_ptr::element_type
- memory/std::unique_ptr::pointer
- memory/std::unique_ptr::get
- memory/std::unique_ptr::get_deleter
- memory/std::unique_ptr::release
- memory/std::unique_ptr::reset
- memory/std::unique_ptr::swap
dev_langs:
- C++
helpviewer_keywords:
- std::unique_ptr [C++]
- std::unique_ptr [C++], deleter_type
- std::unique_ptr [C++], element_type
- std::unique_ptr [C++], pointer
- std::unique_ptr [C++], get
- std::unique_ptr [C++], get_deleter
- std::unique_ptr [C++], release
- std::unique_ptr [C++], reset
- std::unique_ptr [C++], swap
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f148d548cb9d3c93e94f51c1cd8c90fae69527f8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075733"
---
# <a name="uniqueptr-class"></a>unique_ptr – třída

Uchovává ukazatel na vlastní objekt nebo pole. Objekt nebo pole je ve vlastnictví žádné jiné `unique_ptr`. Objekt nebo pole je zničen při `unique_ptr` zničen.

## <a name="syntax"></a>Syntaxe

```cpp
class unique_ptr {
public:
    unique_ptr();
    unique_ptr(nullptr_t Nptr);
    explicit unique_ptr(pointer Ptr);
    unique_ptr(pointer Ptr,
        typename conditional<is_reference<Del>::value, Del,
        typename add_reference<const Del>::type>::type Deleter);
    unique_ptr(pointer Ptr,
        typename remove_reference<Del>::type&& Deleter);
    unique_ptr(unique_ptr&& Right);
    template <class T2, Class Del2>
    unique_ptr(unique_ptr<T2, Del2>&& Right);
    unique_ptr(const unique_ptr& Right) = delete;
    unique_ptr& operator=(const unique_ptr& Right) = delete;
};

//Specialization for arrays:
template <class T, class D>
class unique_ptr<T[], D> {
public:
    typedef pointer;
    typedef T element_type;
    typedef D deleter_type;
    constexpr unique_ptr() noexcept;
    template <class U>
    explicit unique_ptr(U p) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    unique_ptr(unique_ptr&& u) noexcept;
    constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }     template <class U, class E>
        unique_ptr(unique_ptr<U, E>&& u) noexcept;
    ~unique_ptr();
    unique_ptr& operator=(unique_ptr&& u) noexcept;
    template <class U, class E>
    unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;
    unique_ptr& operator=(nullptr_t) noexcept;
    T& operator[](size_t i) const;

    pointer get() const noexcept;
    deleter_type& get_deleter() noexcept;
    const deleter_type& get_deleter() const noexcept;
    explicit operator bool() const noexcept;
    pointer release() noexcept;
    void reset(pointer p = pointer()) noexcept;
    void reset(nullptr_t = nullptr) noexcept;
    template <class U>
    void reset(U p) noexcept = delete;
    void swap(unique_ptr& u) noexcept;  // disable copy from lvalue unique_ptr(const unique_ptr&) = delete;
    unique_ptr& operator=(const unique_ptr&) = delete;
};
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
A `unique_ptr`.

*Nptr*<br/>
`rvalue` Typu `std::nullptr_t`.

*PTR*<br/>
A `pointer`.

*Odstraňovač*<br/>
A `deleter` funkce, která je vázána na `unique_ptr`.

## <a name="exceptions"></a>Výjimky

Podle nejsou generovány žádné výjimky `unique_ptr`.

## <a name="remarks"></a>Poznámky

`unique_ptr` Třídy nahrazuje `auto_ptr`a může sloužit jako element kontejnery standardní knihovny C++.

Použití [make_unique](../standard-library/memory-functions.md#make_unique) pomocnou funkci k efektivnímu vytvoření nových instancí `unique_ptr`.

`unique_ptr` jednoznačně spravuje prostředky. Každý `unique_ptr` ukládá ukazatel na objekt, který je vlastníkem, nebo uchovává ukazatel s hodnotou null. Prostředek může být vlastněn maximálně jedním `unique_ptr` objektu  Když `unique_ptr` objekt, který vlastní určitý prostředek, zničen, prostředek je uvolněn. A `unique_ptr` objekt může být přesunuta, ale nikoli kopírovat;  Další informace najdete v tématu [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

Prostředek je uvolněn voláním uloženého `deleter` objekt typu `Del` , které ví, jak jsou prostředky přidělené pro konkrétní `unique_ptr`. Výchozí hodnota `deleter` `default_delete<T>` předpokládá, že prostředek odkazované `ptr` přidělená k `new`, a lze jej uvolnit voláním `delete _Ptr`. (Částečná specializace `unique_ptr<T[]>`spravuje objekty pole přiřazené s `new[]`, a má výchozí `deleter` `default_delete<T[]>`specializované na delete [] `ptr`.)

Uložený ukazatel na vlastní prostředek, `stored_ptr` má typ `pointer`. Je `Del::pointer` -li definována, a `T *` Pokud tomu tak není. Uložený `deleter` objekt `stored_deleter` nezabírá žádný prostor v objektu, pokud `deleter` jsou bezstavové. Všimněte si, že `Del` může být typ odkazu.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[unique_ptr](#unique_ptr)|Existuje sedm konstruktorů pro `unique_ptr`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[deleter_type](#deleter_type)|Synonymum pro parametr šablony `Del`.|
|[element_type](#element_type)|Synonymum pro parametr šablony `T`.|
|[Ukazatel](#pointer)|Synonymum pro `Del::pointer` li definováno, jinak `T *`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[get](#get)|Vrátí `stored_ptr`.|
|[get_deleter](#get_deleter)|Vrátí odkaz na `stored_deleter`.|
|[Vydání verze](#release)|ukládá `pointer()` v `stored_ptr` a vrátí jeho předchozí obsah.|
|[Resetovat](#reset)|Uvolní aktuálně vlastněný prostředek a přijme nový prostředek.|
|[Prohození](#swap)|Vymění prostředek a `deleter` za poskytnutý `unique_ptr`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|**bool – operátor**|Operátor vrátí hodnotu typu, který lze převést na **bool**. Výsledek převodu na **bool** je **true** při `get() != pointer()`, jinak **false**.|
|`operator->`|Členská funkce vrátí `stored_ptr`.|
|`operator*`|Členská funkce vrátí `*stored_ptr`.|
|[unique_ptr operator=](#unique_ptr_operator_eq)|Přiřadí hodnotu `unique_ptr` (nebo `pointer-type`) na aktuální `unique_ptr`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** std

## <a name="deleter_type"></a>  deleter_type

Typ je synonymum pro parametr šablony `Del`.

```cpp
typedef Del deleter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Del`.

## <a name="element_type"></a>  ELEMENT_TYPE

Typ je synonymum pro parametr šablony `Type`.

```cpp
typedef Type element_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Ty`.

## <a name="get"></a>  unique_ptr::Get

Vrátí `stored_ptr`.

```cpp
pointer get() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `stored_ptr`.

## <a name="get_deleter"></a>  unique_ptr::get_deleter

Vrátí odkaz na `stored_deleter`.

```cpp
Del& get_deleter();

const Del& get_deleter() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na `stored_deleter`.

## <a name="unique_ptr_operator_eq"></a>  unique_ptr operator =

Přiřadí adresu poskytnutého `unique_ptr` do aktuálního.

```cpp
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```

### <a name="parameters"></a>Parametry

A `unique_ptr` odkaz lze přiřadit hodnotu na aktuální `unique_ptr`.

### <a name="remarks"></a>Poznámky

Členské funkce volání `reset(right.release())` a přesunout `right.stored_deleter` k `stored_deleter`a pak se vrátit `*this`.

## <a name="pointer"></a>  Ukazatel

Synonymum pro `Del::pointer` li definováno, jinak `Type *`.

```cpp
typedef T1 pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `Del::pointer` li definováno, jinak `Type *`.

## <a name="release"></a>  unique_ptr::Release

Uvolní vlastnictví objektu vráceného uložený ukazatel volajícímu a nastaví hodnotu uložený ukazatel **nullptr**.

```cpp
pointer release();
```

### <a name="remarks"></a>Poznámky

Použití `release` převzít vlastnictví nezpracovaný ukazatel uložené `unique_ptr`. Volající zodpovídá za odstranění vrácenému ukazateli. `unique-ptr` Je nastavena na prázdný stav vytvořené s výchozím nastavením. Můžete přiřadit jinému ukazateli kompatibilní typ `unique_ptr` po volání `release`.

### <a name="example"></a>Příklad

Tento příklad ukazuje, jak je zodpovědný za objekt vrácený volající verze:

```cpp
// stl_release_unique.cpp
// Compile by using: cl /W4 /EHsc stl_release_unique.cpp
#include <iostream>
#include <memory>

struct Sample {
   int content_;
   Sample(int content) : content_(content) {
      std::cout << "Constructing Sample(" << content_ << ")" << std::endl;
   }
   ~Sample() {
      std::cout << "Deleting Sample(" << content_ << ")" << std::endl;
   }
};

void ReleaseUniquePointer() {
   // Use make_unique function when possible.
   auto up1 = std::make_unique<Sample>(3);
   auto up2 = std::make_unique<Sample>(42);

   // Take over ownership from the unique_ptr up2 by using release
   auto ptr = up2.release();
   if (up2) {
      // This statement does not execute, because up2 is empty.
      std::cout << "up2 is not empty." << std::endl;
   }
   // We are now responsible for deletion of ptr.
   delete ptr;
   // up1 deletes its stored pointer when it goes out of scope.
}

int main() {
   ReleaseUniquePointer();
}
```

Výstup počítače:

```Output
Constructing Sample(3)
Constructing Sample(42)
Deleting Sample(42)
Deleting Sample(3)

```

## <a name="reset"></a>  unique_ptr::Reset

Převezme vlastnictví parametr ukazatele a poté odstraní původní uložený ukazatel. Pokud je nový ukazatel stejný jako původní uložený ukazatel `reset` odstraní ukazatel a nastaví uložený ukazatel na **nullptr**.

```cpp
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na prostředek, který chcete převzít vlastnictví.|

### <a name="remarks"></a>Poznámky

Použití `reset` změnit uloženou [ukazatel](#pointer) vlastněné `unique_ptr` k *ptr* a pak odstraňte původní uložený ukazatel. Pokud `unique_ptr` nebyla prázdná, `reset` vyvolá funkci deleter vrácený [get_deleter –](#get_deleter) na původní uložený ukazatel.

Protože `reset` nejdřív uloží nový ukazatel *ptr*a poté odstraní původní uložený ukazatel, je možné, `reset` okamžitě odstranit *ptr* Pokud je stejný jako původní uložený ukazatel.

## <a name="swap"></a>  unique_ptr::swap

Vymění ukazatelů mezi dvěma `unique_ptr` objekty.

```cpp
void swap(unique_ptr& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
A `unique_ptr` používají k přehazování ukazatele.

### <a name="remarks"></a>Poznámky

Členská funkce Zamění `stored_ptr` s `right.stored_ptr` a `stored_deleter` s `right.stored_deleter`.

## <a name="unique_ptr"></a>  unique_ptr::unique_ptr

Existuje sedm konstruktorů pro `unique_ptr`.

```cpp
unique_ptr();

unique_ptr(nullptr_t);
explicit unique_ptr(pointer ptr);

unique_ptr(
    Type* ptr,
    typename conditional<
    is_reference<Del>::value,
    Del,
    typename add_reference<const Del>::type>::type _Deleter);

unique_ptr(pointer ptr, typename remove_reference<Del>::type&& _Deleter);
unique_ptr(unique_ptr&& right);
template <class Ty2, Class Del2>
unique_ptr(unique_ptr<Ty2, Del2>&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na prostředek, který má být přiřazená `unique_ptr.`|
|*_Deleter*|A `deleter` přiřazení `unique_ptr`.|
|*doprava*|`rvalue reference` k `unique_ptr` odkud `unique_ptr` pole jsou přiřazené do nově vytvořeného přesunout `unique_ptr`.|

### <a name="remarks"></a>Poznámky

První dva konstruktory vytvořit objekt, který spravuje žádný prostředek. Třetí konstruktor ukládá *ptr* v `stored_ptr`. Čtvrtý konstruktor ukládá *ptr* v `stored_ptr` a `deleter` v `stored_deleter`.

Pátý konstruktor ukládá *ptr* v `stored_ptr` a přesune `deleter` do `stored_deleter`. Šestý a sedmý konstruktor úložiště `right.release()` v `stored_ptr` a přesune `right.get_deleter()` do `stored_deleter`.

## <a name="dtorunique_ptr"></a>  unique_ptr ~ unique_ptr

Destruktor `unique_ptr`, odstraní `unique_ptr` objektu.

```cpp
~unique_ptr();
```

### <a name="remarks"></a>Poznámky

Volání destruktoru `get_deleter()(stored_ptr)`.

## <a name="see-also"></a>Viz také:

[\<paměť >](../standard-library/memory.md)<br/>
