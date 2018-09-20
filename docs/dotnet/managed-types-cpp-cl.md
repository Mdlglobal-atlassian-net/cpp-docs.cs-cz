---
title: Spravované typy (c + +/ CL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- types [C++], CLR
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 382228b9e8364d90d7929b4633744071c5eb0c77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408028"
---
# <a name="managed-types-ccl"></a>Spravované typy (C++/CL)

Syntaxe pro deklaraci spravovaných typů, vytváření a využívání tyto typy objektů výrazně upravíte ze spravovaného rozšíření jazyka C++ pro Visual C++. To bylo provedeno podporovat jejich integrace v rámci systému typů ISO C++. Tyto změny jsou uvedeny v podrobnosti v následujících oddílech.

## <a name="in-this-section"></a>V tomto oddílu

[Deklarace spravovaného typu třídy](../dotnet/declaration-of-a-managed-class-type.md)<br/>
Popisuje, jak deklarovat spravovaný `class`, `struct`, nebo `interface`.

[Deklarace objektu referenční třídy CLR](../dotnet/declaration-of-a-clr-reference-class-object.md)<br/>
Popisuje, jak deklarovat objekt typu referenční třídy pomocí sledovací popisovač.

[Deklarace pole CLR](../dotnet/declaration-of-a-clr-array.md)<br/>
Vysvětluje, jak deklarovat a inicializovat pole.

[Změny v pořadí inicializace konstruktoru](../dotnet/changes-in-constructor-initialization-order.md)<br/>
Tento článek popisuje klíčové změny v pořadí inicializace konstruktoru třídy.

[Změny v sémantice destruktorů](../dotnet/changes-in-destructor-semantics.md)<br/>
Tento článek popisuje nedeterministické dokončení `Finalize` oproti `Dispose`, důsledky pro odkaz na objekty a použití explicitní `Finalize`.

**Poznámka:** diskuse o delegátech je odložena až do [Delegáti a události](../dotnet/delegates-and-events.md) prezentovat je události v rámci třídy, obecnými tématy [deklarace členů v rámci třídy nebo rozhraní (C + +/ CLI) ](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).

## <a name="see-also"></a>Viz také

[Základy migrace v jazyce C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[Pole](../windows/arrays-cpp-component-extensions.md)