---
title: "Klíčová slova jazyka (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- keywords [C++]
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e1107ad45feaae470ed2a7481f80bb17c389042d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="language-keywords-ccli"></a>Klíčová slova jazyka (C++/CLI)
Několik klíčových slov jazyka změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 V nové syntaxe jazyka Visual C++, je odebráno dvojité podtržítko jako předpona ze všech klíčových slov (s jednou výjimkou: `__identifier` se uchovávají). Například vlastnost je nyní deklarován jako `property`, nikoli `__property`.  
  
 Existují dvě primární důvody pro pomocí předpony dvojité podtržítko ve spravovaných rozšíření:  
  
-   Jde o schválenou metodu poskytování místních rozšíření ke standardní ISO C++. Primární cílem návrhu spravovaných rozšíření bylo nezavádět nekompatibility se standardní jazyk, jako je například nový klíčová slova a tokeny. Z tohoto důvodu bylo z velké části, který motivoval výběr ukazatel syntaxi pro deklaraci objektů spravovaných odkazové typy.  
  
-   Použití dvojitého podtržítka, kromě jeho aspektu je také dostatečnou záruku je neinvazivní s existující základu kódu jazyka uživatele. To se druhý primární cílem návrhu spravovaných rozšíření.  
  
 Přestože odebírání dvojité podtržítka, zůstane Microsoft zavazuje splňovala. Podpora však pro model dynamický objekt CLR představuje nové a výkonné programovací zlepší. Podporu této nové zlepší vyžaduje vlastní vysoké úrovně klíčová slova a tokeny. Snažili jsme se poskytnout prvotřídní výrazy k těmto novým paradigmatům při integraci a při podpoře standardní jazyk. Nový design syntaxe poskytuje prvotřídní programovací prostředí těchto dvou modelů různorodých objektu.  
  
 Podobně se zabývají maximalizace neinvazivní povaha tyto nové klíčová slova jazyka. Toto má být provedeno s použitím kontextu a oddělení klíčová slova. Předtím, než se podíváme na skutečné nové syntaxe jazyka, můžeme zkuste smysl těchto dvou klíčových slovo.  
  
 Kontextové klíčové slovo má zvláštní význam v rámci konkrétního kontextu programu. V rámci obecné programu, například `sealed` je považován za běžný identifikátor. Ale pokud k ní dojde v části deklaraci typu třídy spravovaný odkaz, se zpracovává jako klíčové slovo v kontextu této deklarace třídy. Tím se minimalizují potenciální dopad invazivní něco představení new – klíčové slovo v jazyce, který je velmi důležité, abyste uživatelům existujícího základu kódu. Ve stejnou dobu umožňuje uživatelům nové funkce mají prvotřídní prostředí funkci další jazyk - něco, co nebylo možné se spravovaných rozšíření. Pro příklad `sealed` se používá v tématu [deklaraci typu třídy spravované](../dotnet/declaration-of-a-managed-class-type.md).  
  
 Klíčový slova, jako například `value class`, je zvláštním případem kontextové klíčové slovo. Je to dvojice existujícího klíčového slova s kontextové modifikátor oddělené mezerou. Dvojice je zpracovaná jako na jednu jednotku a nikoli jako dva samostatné klíčová slova.  
  
## <a name="see-also"></a>Viz také  
 [C + +/ CLI migrace Úvod do](../dotnet/cpp-cli-migration-primer.md)   
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)