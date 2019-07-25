---
title: recursive_directory_iterator – třída
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 98eaf2494a3bc17c0f9d11683fc67fed433ba3a5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451706"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator – třída

Popisuje vstupní iterátor, který sekvencí přes názvy souborů v adresáři, které jsou možné rekurzivně v podadresářích. Pro iterátor `X`se výraz `*X` vyhodnotí jako objekt třídy `directory_entry` , který zabalí název souboru a cokoli vědět o jeho stavu.

Další informace a příklady kódu naleznete v tématu [Navigace v systému souborůC++()](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Poznámky

Třída šablony ukládá:

1. objekt typu `stack<pair<directory_iterator, path>>`, který je zde `mystack` volán pro účely Exposition, který představuje vnoření adresářů, které mají být seřazeny

1. objekt typu `directory_entry` s názvem `myentry` , který představuje aktuální název souboru v pořadí adresářů

1. objekt typu **bool**, který se volá `no_push` tady, který zaznamenává, jestli je zakázané rekurzivní klesání na podadresáře

1. objekt typu `directory_options`, který je zde `myoptions` volán, který zaznamenává možnosti navázány při konstrukci

Výchozí konstruovaný objekt typu `recursive_directory_entry` má na konci sekvenci iterátoru na pozici `mystack.top().first` a představuje iterátor koncové sekvence. Například `abc` pro daný adresář s položkami `def` (adresář), `def/ghi`a `jkl`kód:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

bude volat návštěvu s argumenty `path("abc/def/ghi")` a. `path("abc/jkl")` Sekvencování můžete kvalifikovat prostřednictvím podstromu adresáře dvěma způsoby:

1. Symlink adresáře bude prohledán pouze `recursive_directory_iterator` `directory_options` v případě, že vytvoříte argument s argumentem, jehož hodnota `directory_options::follow_directory_symlink`je.

1. Pokud zavoláte `disable_recursion_pending` , další adresář zjištěný během přírůstku nebude rekurzivně prohledáván.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|`recursive_directory_iterator`Vytvoří.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[úrovní](#depth)|Vrátí `mystack.size() - 1`, takže `pval` má nulovou hloubku.|
|[disable_recursion_pending](#disable_recursion_pending)|Ukládá **hodnotu true** v `no_push`.|
|[zvětš](#increment)|Přejde k dalšímu názvu souboru v pořadí.|
|[nastavení](#options)|Vrátí `myoptions`.|
|[výstrah](#pop)|Vrátí další objekt.|
|[recursion_pending](#recursion_pending)|Vrátí `!no_push`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Vrátí `!(*this == right)`.|
|[operátor =](#op_as)|Výchozí operátory přiřazení členů se chovají podle očekávání.|
|[operator==](#op_eq)|Vrátí **hodnotu true** pouze v `*this` případě, že oba a *pravé* jsou iterátory na konci sekvence nebo obojí nejsou koncem sekvence – iterátory.|
|[podnikatel](#op_multiply)|Vrátí `myentry`.|
|[operátor->](#op_cast)|Vrátí `&**this`.|
|[operator + + – operátor](#op_increment)|`recursive_directory_iterator`Zvýší.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> systému souborů

**Obor názvů:** std:: TR2:: sys

## <a name="depth"></a>recursive_directory_iterator::d epth

Vrátí `mystack.size() - 1`, takže `pval` má nulovou hloubku.

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a>recursive_directory_iterator::d isable_recursion_pending

Ukládá **hodnotu true** v `no_push`.

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a>recursive_directory_iterator:: Increment

Přejde k dalšímu názvu souboru v pořadí.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Parametry

*EHS*\
Zadaný kód chyby

### <a name="remarks"></a>Poznámky

Funkce se pokusí přejít na další název souboru ve vnořené sekvenci. V případě úspěchu uloží tento název souboru v `myentry`; v opačném případě vytvoří iterátor konec sekvence.

## <a name="op_neq"></a>recursive_directory_iterator:: operator! =

Vrátí `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pro porovnání.

## <a name="op_as"></a>recursive_directory_iterator:: operator =

Výchozí operátory přiřazení členů se chovají podle očekávání.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*recursive_directory_iterator*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) , který se kopíruje `recursive_directory_iterator`do.

## <a name="op_eq"></a>recursive_directory_iterator:: operator = = – operátor

Vrátí **hodnotu true** pouze v `*this` případě, že oba a *pravé* jsou iterátory na konci sekvence nebo obojí nejsou koncem sekvence – iterátory.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
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

`recursive_directory_iterator`Zvýší.

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

*hmot*\
Zadaný přírůstek.

### <a name="remarks"></a>Poznámky

První členská funkce volá `increment()`a pak vrátí `*this`. Druhá členská funkce vytvoří kopii objektu, volá `increment()`a vrátí kopii.

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

V `depth() == 0` případě, že se objekt stal iterátorem na konci sekvence. V opačném případě členská funkce ukončí kontrolu aktuálního (nejhoršího) adresáře a obnoví následující nižší hloubku.

## <a name="recursion_pending"></a>recursive_directory_iterator::recursion_pending

Vrátí `!no_push`.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a>recursive_directory_iterator::recursive_directory_iterator

`recursive_directory_iterator`Vytvoří.

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

*pval*\
Zadaná cesta

*error_code*\
Zadaný kód chyby.

*výslovný*\
Zadané možnosti adresáře.

*recursive_directory_iterator*\
Z kterého sestavení `recursive_directory_iterator` má být kopie. `recursive_directory_iterator`

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří iteraci na konci sekvence. Druhý a třetí konstruktory ukládají **hodnotu false** v `no_push` a `directory_options::none` v `myoptions`a pak se pokusí otevřít a číst *Pval* jako adresář. V případě úspěchu se `mystack` inicializují `myentry` a určí první neadresářový název souboru ve vnořené sekvenci. v opačném případě vyprodukuje iterátor na konci sekvence.

Čtvrtý a pátý konstruktor se chová stejně jako druhá a třetí, s tím rozdílem, že nejprve uloží *výslovný* do `myoptions`. Výchozí construtors se chová podle očekávání.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<> systému souborů](../standard-library/filesystem.md)\
[Navigace v systému souborůC++()](../standard-library/file-system-navigation.md)
