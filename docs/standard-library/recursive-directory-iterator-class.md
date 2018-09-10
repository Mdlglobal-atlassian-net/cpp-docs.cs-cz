---
title: recursive_directory_iterator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
dev_langs:
- C++
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82df045c5a41767093e690ec35ffeb3d81032474
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110653"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator – třída

Popisuje vstupní iterátor, který pořadí prostřednictvím názvy souborů v adresáři, případně sestupně do podadresáře rekurzivně. Iterátor `X`, výraz `*X` vyhodnocen jako objekt třídy `directory_entry` tím končí naše název souboru a nic vědět o jeho stavu.

Další informace a příklady kódu naleznete v tématu [navigace systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Poznámky

Šablona třídy úložišť:

1. objekt typu `stack<pair<directory_iterator, path>>`, označované jako `mystack` zde pro účely budeme, která představuje vnoření adresáře se sekvencování

1. objekt typu `directory_entry` volá `myentry` tady, který představuje aktuální název souboru v adresáři pořadí

1. objekt typu `bool`, označované jako `no_push` tady, která zaznamenává, jestli je zakázaná rekurzivní sestup do podadresáře

1. objekt typu `directory_options`, označované jako `myoptions` tady, tj. zaznamenalo se stanoví při konstrukci možnosti

Výchozí vyrobený objekt typu `recursive_directory_entry` má iterátor koncová sekvence na `mystack.top().first` a představuje iterátor koncová sekvence. Mějme například adresář `abc` s položkami `def` (adresář), `def/ghi`, a `jkl`, kód:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

s argumenty navštíví volání `path("abc/def/ghi")` a `path("abc/jkl")`. Kvalifikovat sekvencování prostřednictvím podstrom dvěma způsoby:

1. Adresář symlink prohledá se jenom v případě, že vytvoříte `recursive_directory_iterator` s `directory_options` argument, jehož hodnota je `directory_options::follow_directory_symlink`.

1. Při volání `disable_recursion_pending` následné adresáře došlo k během přírůstek nesmí být rekurzivně zkontrolovat.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[recursive_directory_iterator –](#recursive_directory_iterator)|Vytvoří `recursive_directory_iterator`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Hloubka](#depth)|Vrátí `mystack.size() - 1`, takže `pval` je v hloubce nula.|
|[disable_recursion_pending](#disable_recursion_pending)|Úložiště **true** v `no_push`.|
|[Přírůstek](#increment)|Přejde k další název souboru v sekvenci.|
|[Možnosti](#options)|Vrátí `myoptions`.|
|[POP](#pop)|Vrátí další objekt.|
|[recursion_pending](#recursion_pending)|Vrátí `!no_push`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Vrátí `!(*this == right)`.|
|[operátor =](#op_as)|Operátory přiřazení nastavený na výchozí hodnotu člena chovat dle očekávání.|
|[operator==](#op_eq)|Vrátí **true** pouze tehdy, pokud obě `*this` a *správné* koncová sekvence iterátory nebo obojí jsou není end z pořadí – iterátory.|
|[Operator *](#op_multiply)|Vrátí `myentry`.|
|[Operator ->](#op_cast)|Vrátí `&**this`.|
|[Operator ++](#op_increment)|Zvýší `recursive_directory_iterator`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<filesystem >

**Namespace:** std::tr2:: sys

## <a name="depth"></a> recursive_directory_iterator::Depth –

Vrátí `mystack.size() - 1`, takže `pval` je v hloubce nula.

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a> recursive_directory_iterator::disable_recursion_pending –

Úložiště **true** v `no_push`.

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a> recursive_directory_iterator::Increment –

Přejde k další název souboru v sekvenci.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Parametry

*ES*<br/>
Zadaný kód chyby.

### <a name="remarks"></a>Poznámky

Funkce se pokusí přechodu na další filename vnořené postupně. Pokud úspěšně, uloží tento název souboru v `myentry`; v opačném případě vyvolá iterátor koncová sekvence.

## <a name="op_neq"></a> recursive_directory_iterator::Operator! =

Vrátí `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Recursive_directory_iterator –](../standard-library/recursive-directory-iterator-class.md) pro porovnání.

## <a name="op_as"></a> recursive_directory_iterator::Operator =

Operátory přiřazení nastavený na výchozí hodnotu člena chovat dle očekávání.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*recursive_directory_iterator –*<br/>
[Recursive_directory_iterator –](../standard-library/recursive-directory-iterator-class.md) kopírovaná do `recursive_directory_iterator`.

## <a name="op_eq"></a> recursive_directory_iterator::Operator ==

Vrátí **true** pouze tehdy, pokud obě `*this` a *správné* koncová sekvence iterátory nebo obojí jsou není end z pořadí – iterátory.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Recursive_directory_iterator –](../standard-library/recursive-directory-iterator-class.md) pro porovnání.

## <a name="op_multiply"></a> recursive_directory_iterator::Operator *

Vrátí `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> recursive_directory_iterator::Operator ->

Vrátí `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> recursive_directory_iterator::Operator ++

Zvýší `recursive_directory_iterator`.

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

*int*<br/>
Zadaným přírůstkem.

### <a name="remarks"></a>Poznámky

První volání členských funkcí `increment()`, vrátí `*this`. Druhá členská funkce vytváří kopii objektu volání `increment()`, pak vrátí kopii.

## <a name="options"></a> recursive_directory_iterator::Options –

Vrátí `myoptions`.

```cpp
directory_options options() const;
```

## <a name="pop"></a> recursive_directory_iterator::POP –

Vrátí další objekt.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Pokud `depth() == 0` objekt stane iterátor koncová sekvence. V opačném případě členskou funkci ukončí vyhledávání z aktuálního adresáře (nejhlouběji) a bude pokračovat na další nižší hloubku.

## <a name="recursion_pending"></a> recursive_directory_iterator::recursion_pending –

Vrátí `!no_push`.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a> recursive_directory_iterator::recursive_directory_iterator

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

*pval*<br/>
Zadaná cesta.

*error_code –*<br/>
Zadaný chybový kód.

*požádá o*<br/>
Zadaný adresář možnosti.

*recursive_directory_iterator –*<br/>
`recursive_directory_iterator` z nich vytvořeného `recursive_directory_iterator` je kopií.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří iterátor koncová sekvence. Druhý a třetí konstruktor úložiště **false** v `no_push` a `directory_options::none` v `myoptions`, pak se pokusíte otevřít a přečíst si *pval* jako adresář. Pokud úspěšné, inicializují `mystack` a `myentry` k určení první adresář-název souboru je vnořená pořadí; v opačném případě vytvářejí iterátor koncová sekvence.

Čtvrtý a pátý konstruktor se chová stejně jako druhý a třetí, s tím rozdílem, že nejprve uložit *požádá o* v `myoptions`. Výchozí construtors chovat dle očekávání.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
[Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)<br/>
