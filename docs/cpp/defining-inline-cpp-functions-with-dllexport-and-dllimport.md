---
title: "Definování vložených funkcí jazyka C++ pomocí příkazů dllexport a dllimport | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 125bd894c5448c20948da04b6d7acbe959cc2c9f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definování vložených funkcí jazyka C++ pomocí příkazů dllexport a dllimport
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Jako vloženou lze definovat funkci s atributem `dllexport`. V takovém případě je pro funkci vždy vytvořena instance a funkce je exportována bez ohledu na to, zda jakýkoli modul v programu na funkci odkazuje. Funkce je považována za importovanou jiným programem.  
  
 Můžete také definovat jako vložené funkce deklarovat s **dllimport** atribut. V tomto případě lze funkci rozbalit (dle specifikací /Ob), nelze pro ni však vytvořit instanci. Zejména je-li načtena adresa vložené importované funkce, je vrácena adresa funkce umístěné v knihovně DLL. Toto chování je shodné s načtením adresy nevložené importované funkce.  
  
 Tato pravidla platí pro vložené funkce, jejichž definice jsou uvedeny uvnitř definice třídy. Kromě toho statická místní data a řetězce ve vložených funkcích zachovávají stejné identity mezi knihovnou DLL a klientem tak, jak by je zachovávaly v jediném programu (tedy spustitelném souboru bez rozhraní knihovny DLL).  
  
 Při poskytování importovaných vložených funkcí buďte opatrní. Například při aktualizaci knihovny DLL nepředpokládejte, že klient bude změněnou verzi knihovny používat. Chcete-li se ujistit, že je načítána správná verze knihovny DLL, sestavte znovu také klienta knihovny.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)