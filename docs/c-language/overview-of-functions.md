---
title: "Přehled funkcí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 093400e5d98b0b5e0336c2f640ed0937bdb157b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-functions"></a>Přehled funkcí
Funkce musejí obsahovat definici a měly by obsahovat deklaraci, přestože může definice sloužit jako deklarace, vyskytne-li se tato deklarace před voláním funkce. Definice funkce obsahuje tělo funkce – kód, který se spustí, když je funkce zavolána.  
  
 Deklarace funkce vytvoří název, návratový typ a atributy funkce, která je definována kdekoli v programu. Deklarace funkce musí předcházet volání funkce. Z tohoto důvodu jsou hlavičkové soubory obsahující deklarace funkcí modulu runtime zahrnuty v kódu před voláním funkce modulu runtime. Obsahuje-li deklarace informace o typech a počtu parametrů, je deklarace prototypem. V tématu [prototypy funkcí](../c-language/function-prototypes.md) Další informace.  
  
 Kompilátor používá prototyp pro porovnání typů argumentů v následných voláních funkce s parametry funkce a pro převedení typů argumentů na typy parametrů, kdykoli je to zapotřebí.  
  
 Volání funkce předává řízení provádění kódu z volající funkce na volanou funkci. Argumenty, pokud existují, jsou předány na základě hodnoty do volané funkce. Spuštění příkazu `return` ve volané funkci vrátí řízení a případně hodnotu volající funkci.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../c-language/functions-c.md)