---
title: Přehled funkcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b03357ed094684bb561eff9b790c090a1ebb0712
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033625"
---
# <a name="overview-of-functions"></a>Přehled funkcí

Funkce musejí obsahovat definici a měly by obsahovat deklaraci, přestože může definice sloužit jako deklarace, vyskytne-li se tato deklarace před voláním funkce. Definice funkce obsahuje tělo funkce – kód, který se spustí, když je funkce zavolána.

Deklarace funkce vytvoří název, návratový typ a atributy funkce, která je definována kdekoli v programu. Deklarace funkce musí předcházet volání funkce. Z tohoto důvodu jsou hlavičkové soubory obsahující deklarace funkcí modulu runtime zahrnuty v kódu před voláním funkce modulu runtime. Obsahuje-li deklarace informace o typech a počtu parametrů, je deklarace prototypem. Zobrazit [prototypy](../c-language/function-prototypes.md) Další informace.

Kompilátor používá prototyp pro porovnání typů argumentů v následných voláních funkce s parametry funkce a pro převedení typů argumentů na typy parametrů, kdykoli je to zapotřebí.

Volání funkce předává řízení provádění kódu z volající funkce na volanou funkci. Argumenty, pokud existují, jsou předány na základě hodnoty do volané funkce. Spuštění příkazu `return` ve volané funkci vrátí řízení a případně hodnotu volající funkci.

## <a name="see-also"></a>Viz také

[Funkce](../c-language/functions-c.md)