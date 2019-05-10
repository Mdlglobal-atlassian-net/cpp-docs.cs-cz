---
title: Třídy a struktury (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- C++, classes and structs
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: a37a23296159de2632f6a218eb81315ee2d6a646
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222509"
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

Další informace o sjednocení, naleznete v tématu [sjednocení](../cpp/unions.md). Informace o třídách a strukturách v C++vyhodnocovací a C++/CX, naleznete v tématu [třídy a struktury](../extensions/classes-and-structs-cpp-component-extensions.md).

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Řízení přístupu a omezení struktury, třídy a sjednocení

|Struktury|Třídy|Sjednocení|
|----------------|-------------|------------|
|klíč třídy je **– struktura**|klíč třídy je **třídy**|klíč třídy je **sjednocení**|
|Přístup k výchozím je veřejný|Přístup k výchozím je soukromý|Přístup k výchozím je veřejný|
|Bez omezení využití|Bez omezení využití|Chvíli používat jenom jeden člen.|

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)