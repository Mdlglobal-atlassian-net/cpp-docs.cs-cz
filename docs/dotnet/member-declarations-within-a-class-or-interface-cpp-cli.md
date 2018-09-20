---
title: Deklarace členů v rámci třídy nebo rozhraní (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- members, declaration syntax
- class members, declaration syntax
ms.assetid: 95d312a4-198b-46f0-b8f5-15253807c55e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 80b872b4c614677c05b0d28b821d3a48255905c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430630"
---
# <a name="member-declarations-within-a-class-or-interface-ccli"></a>Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)

Deklarace vlastnosti a operátory byla výrazně přepracována ze spravovaného rozšíření jazyka C++ pro Visual C++, skrytí podkladové podrobnosti implementace, které byly vystaveny v návrhu Správce rozšíření. Deklarace událostí byly změněny také.

V rámci kategorie změn byl zaveden, že žádná podpora spravovaného rozšíření statické konstruktory mohou být definovaná mimo řádek (byly nemusí být definovány ve vloženém spravovaných rozšíření) a pojem Delegující konstruktor.

## <a name="in-this-section"></a>V tomto oddílu

[Deklarace vlastnosti](../dotnet/property-declaration.md)<br/>
Tento článek popisuje změny deklarace vlastností.

[Deklarace indexu vlastnosti](../dotnet/property-index-declaration.md)<br/>
Tento článek popisuje změny deklarace indexované vlastnosti.

[Delegáti a události](../dotnet/delegates-and-events.md)<br/>
Tento článek popisuje změny syntaxe pro deklarování delegátů a událostí.

[Zapečetění virtuální funkce](../dotnet/sealing-a-virtual-function.md)<br/>
Tento článek popisuje změny syntaxe zapečetění funkce.

[Přetížené operátory](../dotnet/overloaded-operators.md)<br/>
Tento článek popisuje změny přetížení operátoru.

[Změny operátorů převodu](../dotnet/changes-to-conversion-operators.md)<br/>
Tento článek popisuje změny u operátorů převodů.

[Explicitní přepsání člena rozhraní](../dotnet/explicit-override-of-an-interface-member.md)<br/>
Tento článek popisuje změny metody pro explicitní přepsání člena rozhraní.

[Soukromé virtuální funkce](../dotnet/private-virtual-functions.md)<br/>
Tento článek popisuje změny ve způsobu zpracování soukromé virtuální funkce v odvozených třídách.

[Statické propojení Const Int už není literál](../dotnet/static-const-int-linkage-is-no-longer-literal.md)<br/>
Tento článek popisuje změny ve způsobu, jakým `static const` integrální členy jsou propojeny a jak explicitně deklarovat konstanty pomocí nového `literal` – klíčové slovo.

## <a name="see-also"></a>Viz také

[Základy migrace v jazyce C++/CLI](../dotnet/cpp-cli-migration-primer.md)