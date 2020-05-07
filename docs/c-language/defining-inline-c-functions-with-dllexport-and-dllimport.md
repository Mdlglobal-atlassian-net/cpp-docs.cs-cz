---
title: Definování vložených funkcí jazyka C pomocí příkazů dllexport a dllimport
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], with dllexport and dllimport
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
- dllexport attribute [C++]
ms.assetid: 41418f7c-1c11-470b-bb2e-1f8269a239f0
ms.openlocfilehash: 2e43f01b495a03e4f50295de42afa9b6c6b38173
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234415"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definování vložených funkcí jazyka C pomocí příkazů dllexport a dllimport

**Specifické pro Microsoft**

Jako vloženou lze definovat funkci s atributem `dllexport`. V takovém případě je pro funkci vždy vytvořena instance a funkce je exportována bez ohledu na to, zda jakýkoli modul v programu na funkci odkazuje. Funkce je považována za importovanou jiným programem.

Můžete také definovat jako vloženou funkci deklarovanou s atributem **dllimport** . V tomto případě lze funkci rozšířit (v souladu se specifikací/ob (inline) kompilátoru), ale nikdy se nevytvoří instance. Zejména je-li načtena adresa vložené importované funkce, je vrácena adresa funkce umístěné v knihovně DLL. Toto chování je shodné s načtením adresy nevložené importované funkce.

Statická lokální data a řetězce ve vložených funkcích udržují stejné identity mezi knihovnou DLL a klientem, protože by to byly v jednom programu (tj. spustitelný soubor bez rozhraní DLL).

Při poskytování importovaných vložených funkcí buďte opatrní. Například při aktualizaci knihovny DLL nepředpokládejte, že klient bude změněnou verzi knihovny používat. Chcete-li se ujistit, že je načítána správná verze knihovny DLL, sestavte znovu také klienta knihovny.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Import a export funkcí knihovny DLL](../c-language/dll-import-and-export-functions.md)
