---
title: "Definování vložených funkcí jazyka C pomocí příkazů dllexport a dllimport | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inline functions [C++], with dllexport and dllimport
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
- dllexport attribute [C++]
ms.assetid: 41418f7c-1c11-470b-bb2e-1f8269a239f0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 77776e174b797bd323aff0a77a2f914b8ac0b0ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definování vložených funkcí jazyka C pomocí příkazů dllexport a dllimport
**Konkrétní Microsoft**  
  
 Jako vloženou lze definovat funkci s atributem `dllexport`. V takovém případě je pro funkci vždy vytvořena instance a funkce je exportována bez ohledu na to, zda jakýkoli modul v programu na funkci odkazuje. Funkce je považována za importovanou jiným programem.  
  
 Můžete také definovat jako vložené funkce deklarovat s **dllimport** atribut. Funkce v tomto případě můžete rozšířit (přičemž podléhá specifikace – možnost kompilátoru /Ob (vložené)) ale nikdy vytvoření instance. Zejména je-li načtena adresa vložené importované funkce, je vrácena adresa funkce umístěné v knihovně DLL. Toto chování je shodné s načtením adresy nevložené importované funkce.  
  
 Statické místních dat a řetězce v vložené funkce zachovat stejné identity mezi DLL a klientem stejně jako v jednom programu (to znamená, spustitelný soubor bez knihovnu DLL rozhraní).  
  
 Při poskytování importovaných vložených funkcí buďte opatrní. Například při aktualizaci knihovny DLL nepředpokládejte, že klient bude změněnou verzi knihovny používat. Chcete-li se ujistit, že je načítána správná verze knihovny DLL, sestavte znovu také klienta knihovny.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL Import a Export funkcí](../c-language/dll-import-and-export-functions.md)