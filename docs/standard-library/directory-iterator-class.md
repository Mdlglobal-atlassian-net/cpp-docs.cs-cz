---
title: directory_iterator – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
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
ms.workload:
- cplusplus
ms.openlocfilehash: 5866f5f7dda4460f1ae9d9af073a2d3eb303dd9f
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="directoryiterator-class"></a>directory_iterator – třída

Popisuje vstupní iterator, který pořadí prostřednictvím názvy souborů v adresáři. Pro iterovat X, výraz * X vyhodnocen jako objekt directory_entry – třída, která zabalí název souboru a nic známé o jeho stav.

Třída ukládá objekt zadejte cestu, volat zde adresář pro účely budeme, který představuje název adresář, který má být sekvencování, a objekt typu directory_entry názvem zde myentry, který představuje aktuální název souboru v adresáři pořadí. Vytvoření objektu výchozí sestavený directory_entry typ má pathname prázdný adresář a představuje iterator koncová sekvence.

Například uděleno adresáři abc s def položky a ghi, kód:

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

navštíví s argumenty path("abc/def") a path("abc/ghi") volání.

Další informace a příklady kódu najdete v tématu [navigační systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class directory_iterator;
```

## <a name="directoryiteratordirectoryiterator"></a>directory_iterator::directory_iterator

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

První konstruktoru vytvoří iterovat koncová sekvence. Druhý a třetí konstruktory uložit pval adresář a potom pokusí otevřít a přečíst si adresář jako adresář. V případě úspěšného uložení první název souboru v adresáři v myentry; v opačném případě vytvářejí iterovat koncová sekvence.

Uvedena construtors chovat podle očekávání.

## <a name="directoryiteratorincrement"></a>directory_iterator::Increment –

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

Funkce se pokusí přechodu na další název souboru v adresáři. V případě úspěchu se ukládá v myentry; tento název souboru jinak vyvolá iterovat koncová sekvence.

## <a name="directoryiteratoroperator"></a>directory_iterator::Operator! =

```cpp
bool operator!=(const directory_iterator& right) const;
```

Vrátí člen operátor! (* to == vpravo).

## <a name="directoryiteratoroperator"></a>directory_iterator::operator=

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

Operátory přiřazení uvedena člen chovat podle očekávání.

## <a name="directoryiteratoroperator"></a>directory_iterator::operator==

```cpp
bool operator==(const directory_iterator& right) const;
```

Vrátí hodnotu true, pouze pokud obě člen operátor * to a pravém jsou koncová sekvence iterátory nebo obě jsou není koncoví z – pořadí – iterátory.

## <a name="directoryiteratoroperator"></a>directory_iterator::Operator *

```cpp
const directory_entry& operator*() const;
```

Operátor členů vrátí myentry.

## <a name="directoryiteratoroperator-"></a>directory_iterator::operator->

```cpp
const directory_entry * operator->() const;
```

Členské funkce vrátí hodnotu & ** to.

## <a name="directoryiteratoroperator"></a>directory_iterator::operator++

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

První člen funkce volá increment() pak vrátí * to. Druhý členská funkce vytvoří kopii objektu, volá increment() a pak vrátí kopie.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<experimentální/filesystem >

**Namespace:** std::experimental::filesystem

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
[Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)<br/>
