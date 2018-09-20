---
title: Klíčová slova jazyka (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keywords [C++]
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0b9deb25e203ea805b1430b2ec8e56f17a50123b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445435"
---
# <a name="language-keywords-ccli"></a>Klíčová slova jazyka (C++/CLI)

Několik klíčových slov jazyka změněn ze spravovaného rozšíření jazyka C++ pro Visual C++.

V nové syntaxi jazyka Visual C++ se odebere dvojitým podtržítkem jako předpona ze všechna klíčová slova (s jednou výjimkou: `__identifier` se uchovávají). Například vlastnost nyní deklarován jako `property`, nikoli `__property`.

Došlo k dispozici dva hlavní důvody pomocí předpony double podtržítka ve spravovaných rozšíření:

- Je metoda splňující podmínky poskytování místních rozšíření standardu ISO C++. Hlavním cílem návrhu spravovaného rozšíření bylo kritickému nekompatibilitu s standardní jazyk, jako je nová klíčová slova a tokeny. Z tohoto důvodu byla z velké části, který motivoval výběr ukazatel syntaxi pro deklaraci referenční informace pro spravované typy objektů.

- Použití dvojitého podtržítka, kromě jeho aspektu je také přiměřené záruku toho, že neinvazivní s existující základ kódu jazyka uživatele. To bylo druhé hlavním cílem návrhu spravovaného rozšíření.

Přestože odstranění dvojitého podtržítka, zůstane Microsoft zavazuje splňovala. Ale podporuje dynamické objektový model CLR představuje novou a výkonnou programovacího paradigmatu. Podpora nových paradigmat vyžaduje svou vlastní základní klíčová slova a tokeny. Snažili jsme se poskytovat prvotřídní výrazu nových paradigmat při integraci a podporuje standardní jazyk. Nový design syntaxe poskytuje prvotřídní programovací prostředí z těchto dvou různých objektových modelů.

Podobně se zabývají maximalizuje neinvazivní povahu těchto nových klíčová slova jazyka. To má být provedeno s použitím kontextu a oddělení klíčových slov. Předtím, než se podíváme na skutečné novou syntaxi jazyka, Zkusme vyznat se tyto dva typy speciální – klíčové slovo.

Kontextové klíčové slovo má zvláštní význam v rámci konkrétní program kontexty. V rámci obecné programu, například `sealed` je považován za běžné identifikátor. Nicméně když k ní dojde v rámci části deklarace typu referenční informace pro spravované třídy, je považován za klíčové slovo v rámci deklarace třídy. Tím se minimalizují potenciální dopad invazivní něco Představujeme nové klíčové slovo v jazyce, který je velmi důležité, abyste uživatelům s existující kódové základně. Ve stejnou dobu umožňuje uživatelům nové funkce prvotřídní prostředí další jazykové funkce - něco, co nebylo možné se spravovaným rozšířením. Příklad toho, jak `sealed` slouží naleznete v tématu [deklarace spravovaného typu třídy](../dotnet/declaration-of-a-managed-class-type.md).

Oddělení – klíčové slovo jako například `value class`, je zvláštním případem kontextové klíčové slovo. Je to s oddělené mezerou kontextová modifikátor dvojice existujícího klíčového slova. Dvojice je zpracováván jako celek, nikoli jako dva samostatné klíčová slova.

## <a name="see-also"></a>Viz také

[Základy migrace v jazyce C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)