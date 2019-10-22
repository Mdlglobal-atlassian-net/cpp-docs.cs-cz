---
title: recursive_directory_iterator – třída
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: a5200c030986ebbcfccb1eba2963e8317c879eb6
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686795"
---
# <a name="recursive_directory_iterator-class"></a>recursive_directory_iterator – třída

Popisuje vstupní iterátor, který sekvencí přes názvy souborů v adresáři, které jsou možné rekurzivně v podadresářích. Pro iterátor `X` výraz `*X` vyhodnotí na objekt třídy `directory_entry`, který zabalí název souboru a cokoli vědět o jeho stavu.

Další informace a příklady kódu naleznete v tématu [Navigace v systému souborůC++()](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Poznámky

Šablona třídy uchovává:

1. objekt typu `stack<pair<directory_iterator, path>>`, který se označuje `mystack` zde pro účely Exposition, který představuje vnoření adresářů, které se mají sekvencovat

1. objekt typu `directory_entry` nazvaný `myentry` zde, který představuje aktuální název souboru v sekvenci adresáře.

1. objekt typu **bool**, který se označuje `no_push` tady, který zaznamenává, jestli je zakázané rekurzivní klesání na podadresáře.

1. objekt typu `directory_options`, který se nazývá `myoptions`, který zaznamenává možnosti navázáné při konstrukci

Výchozí vytvořený objekt typu `recursive_directory_entry` má iterátor konec sekvence v `mystack.top().first` a představuje iterátor konec sekvence. Například vzhledem k adresáři `abc` s položkami `def` (adresář), `def/ghi` a `jkl` kód:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

bude volat návštěvu s argumenty `path("abc/def/ghi")` a `path("abc/jkl")`. Sekvencování můžete kvalifikovat prostřednictvím podstromu adresáře dvěma způsoby:

1. Adresář symlink se prohledá pouze v případě, že vytvoříte `recursive_directory_iterator` s argumentem `directory_options`, jehož hodnota je `directory_options::follow_directory_symlink`.

1. Pokud zavoláte `disable_recursion_pending` potom se při přírůstku nerekurzivně prohledá další adresář.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Vytvoří `recursive_directory_iterator`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[úrovní](#depth)|Vrátí `mystack.size() - 1`, takže `pval` má nulovou hloubku.|
|[disable_recursion_pending](#disable_recursion_pending)|Uloží **hodnotu true** v `no_push`.|
|[zvětš](#increment)|Přejde k dalšímu názvu souboru v pořadí.|
|[nastavení](#options)|Vrátí `myoptions`.|
|[výstrah](#pop)|Vrátí další objekt.|
|[recursion_pending](#recursion_pending)|Vrátí `!no_push`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Vrátí `!(*this == right)`.|
|[operátor =](#op_as)|Výchozí operátory přiřazení členů se chovají podle očekávání.|
|[operator = = – operátor](#op_eq)|Vrátí **hodnotu true** pouze v případě, že `*this` i *Right* jsou iterátory na konci sekvence nebo obojí nejsou koncem sekvence-iterátory.|
|[podnikatel](#op_multiply)|Vrátí `myentry`.|
|[operátor->](#op_cast)|Vrátí `&**this`.|
|[operator + + – operátor](#op_increment)|Zvýší `recursive_directory_iterator`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<filesystem >

**Obor názvů:** std:: TR2:: sys

## <a name="depth"></a>recursive_directory_iterator::d epth

Vrátí `mystack.size() - 1`, takže `pval` má nulovou hloubku.

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a>recursive_directory_iterator::d isable_recursion_pending

Uloží **hodnotu true** v `no_push`.

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a>recursive_directory_iterator:: Increment

Přejde k dalšímu názvu souboru v pořadí.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Parametry

\ pro *ES*
Zadaný kód chyby

### <a name="remarks"></a>Poznámky

Funkce se pokusí přejít na další název souboru ve vnořené sekvenci. V případě úspěchu uloží tento název souboru do `myentry`; v opačném případě vytvoří iterátor na konci sekvence.

## <a name="op_neq"></a>recursive_directory_iterator:: operator! =

Vrátí `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*pravé* \
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pro porovnání.

## <a name="op_as"></a>recursive_directory_iterator:: operator =

Výchozí operátory přiřazení členů se chovají podle očekávání.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*recursive_directory_iterator* \
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) se kopíruje do `recursive_directory_iterator`.

## <a name="op_eq"></a>recursive_directory_iterator:: operator = = – operátor

Vrátí **hodnotu true** pouze v případě, že `*this` i *Right* jsou iterátory na konci sekvence nebo obojí nejsou koncem sekvence-iterátory.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*pravé* \
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pro porovnání.

## <a name="op_multiply"></a>recursive_directory_iterator:: operator * – operátor

Vrátí `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a>recursive_directory_iterator:: operator->

Vrátí `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>recursive_directory_iterator:: operator + +

Zvýší `recursive_directory_iterator`.

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

*int* \
Zadaný přírůstek.

### <a name="remarks"></a>Poznámky

První členská funkce volá `increment()` a potom vrátí `*this`. Druhá členská funkce vytvoří kopii objektu, zavolá `increment()` a vrátí kopii.

## <a name="options"></a>recursive_directory_iterator:: Options – možnosti

Vrátí `myoptions`.

```cpp
directory_options options() const;
```

## <a name="pop"></a>recursive_directory_iterator::p op

Vrátí další objekt.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Pokud `depth() == 0` objekt se stala koncovým iterátorem. V opačném případě členská funkce ukončí kontrolu aktuálního (nejhoršího) adresáře a obnoví následující nižší hloubku.

## <a name="recursion_pending"></a>recursive_directory_iterator::recursion_pending

Vrátí `!no_push`.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a>recursive_directory_iterator::recursive_directory_iterator

Vytvoří `recursive_directory_iterator`.

```cpp
recursive_directory_iterator() noexcept;
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,
    error_code& ec) noexcept;
recursive_directory_iterator(const path& pval,
    directory_options opts);

recursive_directory_iterator(const path& pval,
    directory_options opts,
    error_code& ec) noexcept;
recursive_directory_iterator(const recursive_directory_iterator&) = default;
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*pval* \
Zadaná cesta

*error_code* \
Zadaný kód chyby.

*výslovný* \
Zadané možnosti adresáře.

*recursive_directory_iterator* \
@No__t_0, ze kterého má být vytvořená `recursive_directory_iterator` kopie.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří iteraci na konci sekvence. Druhý a třetí konstruktory ukládají **hodnotu false** do `no_push` a `directory_options::none` v `myoptions` a pak se pokusí otevřít a číst *Pval* jako adresář. V případě úspěchu inicializuje `mystack` a `myentry` určí první neadresářový název souboru ve vnořené sekvenci. v opačném případě vytváří iterátor na konci sekvence.

Čtvrtý a pátý konstruktor se chová stejně jako druhá a třetí, s tím rozdílem, že nejprve uloží *výslovný* do `myoptions`. Výchozí construtors se chová podle očekávání.

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[\<filesystem >](../standard-library/filesystem.md) \
[Navigace v systému souborůC++()](../standard-library/file-system-navigation.md)
