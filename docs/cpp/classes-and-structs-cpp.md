---
title: Třídy a struktury (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, classes
- structures, C++ classes
- user-defined types
- classes [C++]
- user-defined types, C++ classes
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88836d93d6ce3ba4dff817c7b470e87f48f61b14
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954174"
---
# <a name="classes-and-structs-c"></a>Třídy a struktury (C++)
Tato část představuje C++ třídy a struktury. Dva konstruktory jsou identické v jazyce C++, s tím rozdílem, že ve strukturách výchozí dostupnost je veřejné, zatímco ve třídách výchozí hodnota je privátní.  
  
 Třídy a struktury jsou konstrukce, které definování vlastních typů. Třídy a struktury můžete oba obsahovat datové členy a členské funkce, které vám umožní popisují stav a chování tohoto typu.  
  
 Jsou zahrnuty v následujících tématech:  
  
-   [class](../cpp/class-cpp.md)  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [Přehled členů třídy](../cpp/class-member-overview.md)  
  
-   [Řízení přístupu ke členu](../cpp/member-access-control-cpp.md)  
  
-   [Dědičnost](../cpp/inheritance-cpp.md)  
  
-   [Statické členy](../cpp/static-members-cpp.md)  
  
-   [Převody typů definovaných uživatelem](../cpp/user-defined-type-conversions-cpp.md)  
  
-   [Proměnlivé datové členy (proměnný specifikátor)](../cpp/mutable-data-members-cpp.md)  
  
-   [Deklarace vnořených tříd](../cpp/nested-class-declarations.md)  
  
-   [Anonymní typy tříd](../cpp/anonymous-class-types.md)  
  
-   [Ukazatelé na členy](../cpp/pointers-to-members.md)  
  
-   [this – ukazatel](../cpp/this-pointer.md)  
  
-   [Bitová pole jazyka C++](../cpp/cpp-bit-fields.md)  
  
 Třída tři typy jsou struktury, třídy a sjednocení. Jsou deklarovány pomocí [struktura](../cpp/struct-cpp.md), [třídy](../cpp/class-cpp.md), a [sjednocení](../cpp/unions.md) klíčová slova. V následující tabulce jsou uvedeny rozdíly mezi typy tři třídy.  
  
 Další informace o sjednocení, naleznete v tématu [sjednocení](../cpp/unions.md). Informace o spravovaných třídách a strukturách naleznete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md).  
  
### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Řízení přístupu a omezení struktury, třídy a sjednocení  
  
|Struktury|Třídy|Sjednocení|  
|----------------|-------------|------------|  
|klíč třídy je **– struktura**|klíč třídy je **třídy**|klíč třídy je **sjednocení**|  
|Přístup k výchozím je veřejný|Přístup k výchozím je soukromý|Přístup k výchozím je veřejný|  
|Bez omezení využití|Bez omezení využití|Chvíli používat jenom jeden člen.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)