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
ms.openlocfilehash: 6763f2a96b771fadbec311cf8740352fff53e29a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413843"
---
# <a name="directoryiterator-class"></a>directory_iterator – třída

Popisuje vstupní iterátor, který pořadí prostřednictvím názvy souborů v adresáři. Iterátor `X`, výraz `*X` vyhodnocen jako objekt třídy `directory_entry` tím končí naše název souboru a nic vědět o jeho stavu.

Uloží objekt typu třídy `path`, označované jako `mydir` zde pro účely budeme, který představuje název adresář, který má být seřazeny, a objekt typu `directory_entry` volá `myentry` tady, který představuje aktuální Název souboru v adresáři pořadí. Výchozí vyrobený objekt typu `directory_entry` prázdnou `mydir` cesta a představuje iterátor koncová sekvence.

Mějme například adresář `abc` s položkami `def` a `ghi`, kód:

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

zavolá `visit` s argumenty `path("abc/def")` a `path("abc/ghi")`.

Další informace a příklady kódu naleznete v tématu [navigace systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class directory_iterator;
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[directory_iterator](#directory_iterator)|Sestaví vstupní iterátor, který pořadí prostřednictvím názvy souborů v adresáři.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Přírůstek](#increment)|Pokusy o přechodu na další název souboru v adresáři.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Vrátí `!(*this == right)`.|
|[operátor =](#op_as)|Operátory přiřazení nastavený na výchozí hodnotu člena chovat dle očekávání.|
|[operator==](#op_eq)|Vrátí **true** pouze tehdy, pokud obě `*this` a *správné* koncová sekvence iterátory nebo obojí jsou není end z pořadí – iterátory.|
|[Operator *](#op_star)|Vrátí `myentry`.|
|[operator->](#op_cast)|Vrátí `&**this`.|
|[Operator ++](#op_increment)|Volání `increment()`, vrátí `*this`, nebo vytvoří kopii tohoto objektu, volání `increment()`, pak vrátí kopii.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<experimentální/filesystem >

**Namespace:** std::experimental::filesystem

## <a name="directory_iterator"></a> directory_iterator::directory_iterator

První konstruktor vytvoří iterátor koncová sekvence. Druhý a třetí konstruktor úložiště *pval* v `mydir`, pak se pokusíte otevřít a přečíst si `mydir` jako adresář. Pokud úspěšné, jsou v nich uložené první název souboru v adresáři v `myentry`; v opačném případě vytvářejí iterátor koncová sekvence.

Výchozí construtors chovat dle očekávání.

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Cesta k názvu uloženého souboru.

*ec*<br/>
Stavový kód chyby.

*directory_iterator*<br/>
Uložený objekt.

## <a name="increment"></a> directory_iterator::Increment –

Funkce se pokusí o přechodu na další název souboru v adresáři. Pokud úspěšně, uloží tento název souboru v `myentry`; v opačném případě vyvolá iterátor koncová sekvence.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a> directory_iterator::Operator! =

Členský operátor vrátí `!(*this == right)`.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Directory_iterator –](../standard-library/directory-iterator-class.md) porovnávané hodnotě `directory_iterator`.

## <a name="op_as"></a> directory_iterator::Operator =

Operátory přiřazení nastavený na výchozí hodnotu člena chovat dle očekávání.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Directory_iterator –](../standard-library/directory-iterator-class.md) kopírovaná do `directory_iterator`.

## <a name="op_eq"></a> directory_iterator::Operator ==

Členský operátor vrátí **true** pouze tehdy, pokud obě `*this` a *správné* koncová sekvence iterátory nebo obojí jsou není end z pořadí – iterátory.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Directory_iterator –](../standard-library/directory-iterator-class.md) porovnávané hodnotě `directory_iterator`.

## <a name="op_star"></a> directory_iterator::Operator *

Členský operátor vrátí `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> directory_iterator::Operator ->

Členská funkce vrátí `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> directory_iterator::Operator ++

První volání členských funkcí `increment()`, vrátí `*this`. Druhá členská funkce vytváří kopii objektu volání `increment()`, pak vrátí kopii.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

*int*<br/>
Počet přírůstků.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)<br/>
