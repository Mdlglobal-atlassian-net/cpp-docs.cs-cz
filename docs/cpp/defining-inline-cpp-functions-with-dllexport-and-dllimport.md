---
title: Definování vložených funkcí jazyka C++ pomocí příkazů dllexport a dllimport
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
ms.openlocfilehash: 9620706e6ac477246ce323a7fc3624291bb1dd6b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180196"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definování vložených funkcí jazyka C++ pomocí příkazů dllexport a dllimport

**Specifické pro společnost Microsoft**

Můžete definovat jako vloženou funkci s atributem **dllexport** . V takovém případě je pro funkci vždy vytvořena instance a funkce je exportována bez ohledu na to, zda jakýkoli modul v programu na funkci odkazuje. Funkce je považována za importovanou jiným programem.

Můžete také definovat jako vloženou funkci deklarovanou s atributem **dllimport** . V tomto případě lze funkci rozbalit (dle specifikací /Ob), nelze pro ni však vytvořit instanci. Zejména je-li načtena adresa vložené importované funkce, je vrácena adresa funkce umístěné v knihovně DLL. Toto chování je shodné s načtením adresy nevložené importované funkce.

Tato pravidla platí pro vložené funkce, jejichž definice jsou uvedeny uvnitř definice třídy. Kromě toho statická místní data a řetězce ve vložených funkcích zachovávají stejné identity mezi knihovnou DLL a klientem tak, jak by je zachovávaly v jediném programu (tedy spustitelném souboru bez rozhraní knihovny DLL).

Při poskytování importovaných vložených funkcí buďte opatrní. Například při aktualizaci knihovny DLL nepředpokládejte, že klient bude změněnou verzi knihovny používat. Chcete-li se ujistit, že je načítána správná verze knihovny DLL, sestavte znovu také klienta knihovny.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
