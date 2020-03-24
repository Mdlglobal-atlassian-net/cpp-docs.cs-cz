---
title: Třídy a struktury (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- C++, classes and structs
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: 19d95c9519670db39f3ca467aff794233823d7ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180885"
---
# <a name="classes-and-structs-c"></a>Třídy a struktury (C++)

Tato část zavádí C++ třídy a struktury. Tyto dvě konstrukce jsou identické v C++ s tím rozdílem, že ve strukturách je výchozí přístupnost veřejná, zatímco v třídách výchozí je privátní.

Třídy a struktury jsou konstrukce, při kterých definujete vlastní typy. Třídy a struktury mohou obsahovat datové členy a členské funkce, které umožňují popsat stav a chování typu.

Jsou k dispozici následující témata:

- [class](../cpp/class-cpp.md)

- [struct](../cpp/struct-cpp.md)

- [Přehled členů třídy](../cpp/class-member-overview.md)

- [Řízení přístupu ke členu](../cpp/member-access-control-cpp.md)

- [Dědičnost](../cpp/inheritance-cpp.md)

- [Statické členy](../cpp/static-members-cpp.md)

- [Převody typů definovaných uživatelem](../cpp/user-defined-type-conversions-cpp.md)

- [Proměnlivé datové členy (proměnlivý specifikátor)](../cpp/mutable-data-members-cpp.md)

- [Deklarace vnořených tříd](../cpp/nested-class-declarations.md)

- [Anonymní typy tříd](../cpp/anonymous-class-types.md)

- [Ukazatelé na členy](../cpp/pointers-to-members.md)

- [this – ukazatel](../cpp/this-pointer.md)

- [Bitová pole jazyka C++](../cpp/cpp-bit-fields.md)

Tři typy tříd jsou struktura, třída a sjednocení. Jsou deklarovány pomocí klíčových slov [struct](../cpp/struct-cpp.md), [Class](../cpp/class-cpp.md)a [Union](../cpp/unions.md) . V následující tabulce jsou uvedeny rozdíly mezi třemi typy tříd.

Další informace o sjednoceních najdete v tématu [sjednocení](../cpp/unions.md). Informace o třídách a strukturách v C++/CLI a C++/CX naleznete v tématu [třídy a struktury](../extensions/classes-and-structs-cpp-component-extensions.md).

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Access Control a omezení struktur, tříd a sjednocení

|Struktury|Třídy|Sjednocení|
|----------------|-------------|------------|
|klíč třídy je **Struktura** .|klíč třídy je **Třída** .|klíč třídy je **sjednocení** .|
|Výchozí přístup je veřejný.|Výchozí přístup je privátní.|Výchozí přístup je veřejný.|
|Žádná omezení použití|Žádná omezení použití|Použít vždy pouze jednoho člena|

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)
