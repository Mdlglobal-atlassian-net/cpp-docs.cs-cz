---
title: Definování vložených funkcí jazyka C++ pomocí příkazů dllexport a dllimport | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5299018f8c8e92cd4bfe45889f379c88064007e1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037083"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definování vložených funkcí jazyka C++ pomocí příkazů dllexport a dllimport

## <a name="microsoft-specific"></a>Specifické pro Microsoft

Jako vloženou lze definovat funkci s **dllexport** atribut. V takovém případě je pro funkci vždy vytvořena instance a funkce je exportována bez ohledu na to, zda jakýkoli modul v programu na funkci odkazuje. Funkce je považována za importovanou jiným programem.

Můžete také jako vloženou lze definovat funkce deklarovaná pomocí **dllimport** atribut. V tomto případě lze funkci rozbalit (dle specifikací /Ob), nelze pro ni však vytvořit instanci. Zejména je-li načtena adresa vložené importované funkce, je vrácena adresa funkce umístěné v knihovně DLL. Toto chování je shodné s načtením adresy nevložené importované funkce.

Tato pravidla platí pro vložené funkce, jejichž definice jsou uvedeny uvnitř definice třídy. Kromě toho statická místní data a řetězce ve vložených funkcích zachovávají stejné identity mezi knihovnou DLL a klientem tak, jak by je zachovávaly v jediném programu (tedy spustitelném souboru bez rozhraní knihovny DLL).

Při poskytování importovaných vložených funkcí buďte opatrní. Například při aktualizaci knihovny DLL nepředpokládejte, že klient bude změněnou verzi knihovny používat. Chcete-li se ujistit, že je načítána správná verze knihovny DLL, sestavte znovu také klienta knihovny.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[dllexport, dllimport](../cpp/dllexport-dllimport.md)