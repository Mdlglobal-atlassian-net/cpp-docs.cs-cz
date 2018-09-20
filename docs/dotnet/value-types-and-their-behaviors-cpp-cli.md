---
title: Hodnotové typy a jejich chování (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- value types
ms.assetid: 5cb872a6-1e0a-429d-853d-df4ab47e8f2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d2d980e48a6f948c35faf0c4e42969795ef8dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404654"
---
# <a name="value-types-and-their-behaviors-ccli"></a>Hodnotové typy a jejich chování (C++/CLI)

Typy hodnot změnily různými způsoby ze spravovaného rozšíření jazyka C++ pro Visual C++. V této části se podíváme na typ výčtu CLR a hodnota typu třídy, společně se podívat, zabalení a přístup k instanci boxed na haldě modulu CLR, jakož i pohled na vnitřních a přídavných ukazatelů. V této oblasti byla rozsáhlé jazykové změny.

## <a name="in-this-section"></a>V tomto oddílu

[Typ enum v prostředí CLR](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
Tento článek popisuje změny v deklaraci a chování výčtů.

[Implicitní zabalení typů hodnot](../dotnet/implicit-boxing-of-value-types.md)<br/>
Tento článek popisuje motivace pro implicitní zabalení typů hodnot a následné změny v chování.

[Sledovací popisovač zabalené hodnoty](../dotnet/a-tracking-handle-to-a-boxed-value.md)<br/>
Popisuje, jak implicitní zabalení typů hodnot překládá na sledovací popisovač zabalené hodnoty objektu.

[Sémantika typu hodnoty](../dotnet/value-type-semantics.md)<br/>
Tento článek popisuje změny Sémantika typu hodnoty, včetně zděděné virtuální metody, třídy výchozí konstruktory, vnitřních ukazatelů a přídavné ukazatele.

## <a name="see-also"></a>Viz také

[Základy migrace v jazyce C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)