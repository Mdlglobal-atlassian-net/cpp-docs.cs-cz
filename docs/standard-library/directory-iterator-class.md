---
title: directory_iterator – třída
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::increment
- filesystem/std::experimental::filesystem::directory_iterator::operator=
- filesystem/std::experimental::filesystem::directory_iterator::operator==
- filesystem/std::experimental::filesystem::directory_iterator::operator!=
- filesystem/std::experimental::filesystem::directory_iterator::operator*
- filesystem/std::experimental::filesystem::directory_iterator::operator-&gt;
- filesystem/std::experimental::filesystem::directory_iterator::operator++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
helpviewer_keywords:
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator-&gt;
- std::experimental::filesystem::directory_iterator::operator++
ms.openlocfilehash: 8c6dcce3de32c7e25d2489cb508454dff500a1a6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454418"
---
# <a name="directoryiterator-class"></a>directory_iterator – třída

Popisuje vstupní iterátor, který bude sekvencovat prostřednictvím názvů souborů v adresáři. Pro iterátor `X`se výraz `*X` vyhodnotí jako objekt třídy `directory_entry` , který zabalí název souboru a cokoli vědět o jeho stavu.

Třída `path`ukládá objekt typu, který je zde volán `mydir` pro účely Exposition, který představuje název adresáře, který má být sekvencované, a objekt typu `directory_entry` `myentry` , který představuje aktuální název souboru v posloupnosti adresářů Výchozí vytvořený objekt typu `directory_entry` má prázdnou `mydir` cestu a představuje iterátor konec sekvence.

Například pro daný adresář `abc` s položkami `def` a `ghi`kód:

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

provede volání `visit` s argumenty `path("abc/def")` a `path("abc/ghi")`.

Další informace a příklady kódu naleznete v tématu [Navigace v systému souborůC++()](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class directory_iterator;
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[directory_iterator](#directory_iterator)|Vytvoří vstupní iterátor, který bude sekvencovat prostřednictvím názvů souborů v adresáři.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[zvětš](#increment)|Pokusí se přejít k dalšímu názvu souboru v adresáři.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Vrátí `!(*this == right)`.|
|[operátor =](#op_as)|Výchozí operátory přiřazení členů se chovají podle očekávání.|
|[operator==](#op_eq)|Vrátí **hodnotu true** pouze v `*this` případě, že oba a *pravé* jsou iterátory na konci sekvence nebo obojí nejsou koncem sekvence – iterátory.|
|[podnikatel](#op_star)|Vrátí `myentry`.|
|[operátor->](#op_cast)|Vrátí `&**this`.|
|[operator + + – operátor](#op_increment)|Volá `increment()`, vrátí `*this`nebo vytvoří kopii objektu, volá `increment()`a vrátí kopii.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<experimentální/FileSystem >

**Obor názvů:** std:: experimentální:: FileSystem

## <a name="directory_iterator"></a>Directory_iterator::d irectory_iterator

První konstruktor vytvoří iteraci na konci sekvence. Druhý a třetí konstruktory ukládají *Pval* do `mydir`a pak se pokusí otevřít a číst `mydir` jako adresář. V případě úspěchu uloží první název souboru do adresáře v `myentry`. v opačném případě vyprodukuje iterátor na konci sekvence.

Výchozí construtors se chová podle očekávání.

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*pval*\
Cesta k názvu uloženého souboru.

*EHS*\
Kód chyby stavu.

*directory_iterator*\
Uložený objekt.

## <a name="increment"></a>Directory_iterator:: Increment

Funkce se pokusí přejít k dalšímu názvu souboru v adresáři. V případě úspěchu uloží tento název souboru v `myentry`; v opačném případě vytvoří iterátor konec sekvence.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a>Directory_iterator:: operator! =

Vrátí `!(*this == right)`operátor member.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Directory_iterator](../standard-library/directory-iterator-class.md) je porovnán `directory_iterator`s.

## <a name="op_as"></a>Directory_iterator:: operator =

Výchozí operátory přiřazení členů se chovají podle očekávání.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Directory_iterator](../standard-library/directory-iterator-class.md) , který se kopíruje `directory_iterator`do.

## <a name="op_eq"></a>Directory_iterator:: operator = = – operátor

Členský operátor vrátí **hodnotu true** pouze v případě `*this` , že *jsou a jsou* iterátory na konci sekvence nebo obojí nejsou koncem sekvence – iterátory.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Directory_iterator](../standard-library/directory-iterator-class.md) je porovnán `directory_iterator`s.

## <a name="op_star"></a>Directory_iterator:: operator * – operátor

Vrátí `myentry`operátor member.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a>Directory_iterator:: operator->

Vrátí `&**this`členské funkce.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>Directory_iterator:: operator + +

První členská funkce volá `increment()`a pak vrátí `*this`. Druhá členská funkce vytvoří kopii objektu, volá `increment()`a vrátí kopii.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

*hmot*\
Počet přírůstků.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<> systému souborů](../standard-library/filesystem.md)\
[Navigace v systému souborůC++()](../standard-library/file-system-navigation.md)
