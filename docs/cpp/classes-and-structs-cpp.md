---
title: Třídy a struktury (C++) | Microsoft Docs
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
ms.openlocfilehash: 61348578018a5bbddcaff293fa3ed76575eb16de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413242"
---
# <a name="classes-and-structs-c"></a>Třídy a struktury (C++)
Tato část představuje C++ třídy a struktury. Kromě toho, že v struktury je výchozí usnadnění veřejným, zatímco ve třídách výchozí hodnota je privátní, jsou identické v jazyce C++ dvěma konceptů.  
  
 Třídy a struktury jsou konstrukce, které definujete vlastní typy. Třídy a struktury může obě obsahovat datových členů a členské funkce, které vám umožní popisují stavu a chování tohoto typu.  
  
 V následujících tématech jsou zahrnuty:  
  
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
  
 Typy tři třídy jsou struktura, třídu a sjednocení. Jsou deklarovány pomocí [struktura](../cpp/struct-cpp.md), [třída](../cpp/class-cpp.md), a [– typ union](../cpp/unions.md) klíčová slova (najdete v části [definování typy tříd](http://msdn.microsoft.com/en-us/e8c65425-0f3a-4dca-afc2-418c3b1e57da)). V následující tabulce jsou uvedeny rozdíly mezi typy tří tříd.  
  
 Další informace o sjednocení najdete v tématu [sjednocení](../cpp/unions.md). Informace na spravované třídy a struktury najdete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md).  
  
### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Řízení přístupu a omezení struktury, třídy a sjednocení  
  
|Struktury|Třídy|Sjednocení|  
|----------------|-------------|------------|  
|je klíč třídy `struct`|klíč třídy je **– třída**|klíč třídy je **sjednocení**|  
|Výchozí úroveň přístupu je veřejný|Výchozí úroveň přístupu je soukromý|Výchozí úroveň přístupu je veřejný|  
|Žádná omezení využití|Žádná omezení využití|Současně použít jen jeden členský|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)