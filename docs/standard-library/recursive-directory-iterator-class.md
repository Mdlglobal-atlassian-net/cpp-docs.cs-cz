---
title: recursive_directory_iterator – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
dev_langs:
- C++
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3e1ef6dab66e0414ecace7b6e51b31eef632d06
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator – třída

Popisuje vstupní iterátor, který pořadí prostřednictvím názvy souborů v adresáři, pravděpodobně sestupném do podadresáře rekurzivně. Pro iterovat X, výraz * X vyhodnocen jako objekt directory_entry – třída, která zabalí název souboru a nic známé o jeho stav.

Další informace a příklady kódu najdete v tématu [navigační systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Poznámky

Šablony třídy úložiště:

1. objekt typu zásobníku < pair\<directory_iterator, cesta >>, volat mystack sem pro účely budeme, která představuje vnoření z adresáře, které chcete být sekvencování

1. objekt typu directory_entry názvem zde myentry, který představuje aktuální název souboru v adresáři pořadí

1. objekt typu bool, nazývá no_push zde, který zaznamenává, jestli je zakázaná rekurzivní klesání do podadresáře

1. objekt typu directory_options, nazývá myoptions zde, který zaznamenává možnosti navázat na konstrukce

Objekt sestavený výchozí typ recursive_directory_entry má iterovat koncová sekvence v .first mystack.top () a představuje iterator koncová sekvence. Například uděleno adresáři abc s položky def (adresář), def/ghi a jkl, kód:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

s argumenty navštíví volání `path("abc/def/ghi") and path("abc/jkl").`kvalifikovat sekvencování prostřednictvím podstrom directory dvěma způsoby:

1. Directory symlink budou prohledávány pouze v případě, že vytvoříte recursive_directory_iterator s argumentem directory_options, jehož hodnota je directory_options::follow_directory_symlink.

1. Když zavoláte disable_recursion_pending následné adresáře došlo během přírůstek nebudou rekurzivně zkontrolovat.

## <a name="recursivedirectoryiteratordepth"></a>recursive_directory_iterator::depth

```cpp
int depth() const;
```

Vrátí mystack.size() - 1, takže pval je při hloubce nula.

## <a name="recursivedirectoryiteratordisablerecursionpending"></a>recursive_directory_iterator::disable_recursion_pending

```cpp
void disable_recursion_pending();
```

Členská funkce ukládá do no_push hodnotu true.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator!=

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

Vrátí člen operátor! (* to == vpravo).

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator=

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

Operátory přiřazení uvedena člen chovat podle očekávání.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator==

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

Vrátí hodnotu true, pouze pokud obě člen operátor * to a pravém jsou koncová sekvence iterátory nebo obě jsou není koncoví z – pořadí – iterátory.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator*

```cpp
const directory_entry& operator*() const;
```

Operátor členů vrátí myentry.

## <a name="recursivedirectoryiteratoroperator-"></a>recursive_directory_iterator::operator->

```cpp
const directory_entry * operator->() const;
```

Vrátí & ** to.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator++

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

První člen funkce volá increment() pak vrátí * to. Druhý členská funkce vytvoří kopii objektu, volá increment() a pak vrátí kopie.

## <a name="recursivedirectoryiteratoroptions"></a>recursive_directory_iterator::options

```cpp
directory_options options() const;
```

Vrátí myoptions.

## <a name="recursivedirectoryiteratorpop"></a>recursive_directory_iterator::pop

```cpp
void pop();
```

Pokud depth() == 0 objektu se změní na iterovat koncová sekvence. Členské funkce, jinak hodnota ukončí kontrolu aktuálnímu adresáři (nejhlubší) a obnoví v další nižší hloubka.

## <a name="recursivedirectoryiteratorrecursionpending"></a>recursive_directory_iterator::recursion_pending

```cpp
bool recursion_pending() const;
```

Vrátí! no_push.

## <a name="recursivedirectoryiteratorrecursivedirectoryiterator"></a>recursive_directory_iterator::recursive_directory_iterator

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

První konstruktoru vytvoří iterovat koncová sekvence. Druhý a třetí konstruktory ukládání false v no_push a directory_options::none v myoptions a potom pokusí otevřít a přečíst si pval jako adresář. V případě úspěchu se inicializují mystack a myentry k určení první adresář-filename v sekvenci vnořené; v opačném případě vytvářejí iterovat koncová sekvence.

Konstruktory čtvrté a páté chovají stejně jako druhý a třetí, s tím rozdílem, že nejprve uložit vyjádřit výslovný souhlas myoptions. Uvedena construtors chovat podle očekávání.

## <a name="recursivedirectoryiteratorincrement"></a>recursive_directory_iterator::increment

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

Funkce se pokusí přechodu na další název souboru v vnořené pořadí. V případě úspěchu se ukládá v myentry; tento název souboru jinak vyvolá iterovat koncová sekvence.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<filesystem >

**Namespace:** std::tr2::sys

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
[Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)<br/>
