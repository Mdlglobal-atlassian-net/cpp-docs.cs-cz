---
title: Třídy a struktury (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C++, classes
- structures, C++ classes
- user-defined types
- classes [C++]
- user-defined types, C++ classes
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: 44736b9515363d1406b124858f72f12f8f7f552a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562744"
---
# <a name="classes-and-structs-c"></a>Třídy a struktury (C++)

Tato část představuje C++ třídy a struktury. Dva konstruktory jsou identické v jazyce C++, s tím rozdílem, že ve strukturách výchozí dostupnost je veřejné, zatímco ve třídách výchozí hodnota je privátní.

Třídy a struktury jsou konstrukce, které definování vlastních typů. Třídy a struktury můžete oba obsahovat datové členy a členské funkce, které vám umožní popisují stav a chování tohoto typu.

Jsou zahrnuty v následujících tématech:

- [class](../cpp/class-cpp.md)

- [struct](../cpp/struct-cpp.md)

- [Přehled členů třídy](../cpp/class-member-overview.md)

- [Řízení přístupu ke členu](../cpp/member-access-control-cpp.md)

- [Dědičnost](../cpp/inheritance-cpp.md)

- [Statické členy](../cpp/static-members-cpp.md)

- [Převody typů definovaných uživatelem](../cpp/user-defined-type-conversions-cpp.md)

- [Proměnlivé datové členy (proměnný specifikátor)](../cpp/mutable-data-members-cpp.md)

- [Deklarace vnořených tříd](../cpp/nested-class-declarations.md)

- [Anonymní typy tříd](../cpp/anonymous-class-types.md)

- [Ukazatelé na členy](../cpp/pointers-to-members.md)

- [this – ukazatel](../cpp/this-pointer.md)

- [Bitová pole jazyka C++](../cpp/cpp-bit-fields.md)

Třída tři typy jsou struktury, třídy a sjednocení. Jsou deklarovány pomocí [struktura](../cpp/struct-cpp.md), [třídy](../cpp/class-cpp.md), a [sjednocení](../cpp/unions.md) klíčová slova. V následující tabulce jsou uvedeny rozdíly mezi typy tři třídy.

Další informace o sjednocení, naleznete v tématu [sjednocení](../cpp/unions.md). Informace o spravovaných třídách a strukturách naleznete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md).

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Řízení přístupu a omezení struktury, třídy a sjednocení

|Struktury|Třídy|Sjednocení|
|----------------|-------------|------------|
|klíč třídy je **– struktura**|klíč třídy je **třídy**|klíč třídy je **sjednocení**|
|Přístup k výchozím je veřejný|Přístup k výchozím je soukromý|Přístup k výchozím je veřejný|
|Bez omezení využití|Bez omezení využití|Chvíli používat jenom jeden člen.|

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)