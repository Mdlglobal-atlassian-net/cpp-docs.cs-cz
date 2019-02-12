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
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151153"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definování vložených funkcí jazyka C pomocí příkazů dllexport a dllimport

**Microsoft Specific**

Jako vloženou lze definovat funkci s atributem `dllexport`. V takovém případě je pro funkci vždy vytvořena instance a funkce je exportována bez ohledu na to, zda jakýkoli modul v programu na funkci odkazuje. Funkce je považována za importovanou jiným programem.

Můžete také jako vloženou lze definovat funkce deklarovaná pomocí **dllimport** atribut. V takovém případě funkce můžete rozbalit (specifikace – možnost kompilátoru /Ob (inline)) ale nikdy nevytváří instanci. Zejména je-li načtena adresa vložené importované funkce, je vrácena adresa funkce umístěné v knihovně DLL. Toto chování je shodné s načtením adresy nevložené importované funkce.

Statická místní data a řetězce ve vložených funkcích zachovávají stejné identity mezi knihovnou DLL a klientem, jak by je zachovávaly v jediném programu (tedy spustitelném souboru bez rozhraní knihovny DLL).

Při poskytování importovaných vložených funkcí buďte opatrní. Například při aktualizaci knihovny DLL nepředpokládejte, že klient bude změněnou verzi knihovny používat. Chcete-li se ujistit, že je načítána správná verze knihovny DLL, sestavte znovu také klienta knihovny.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Import a export funkcí knihovny DLL](../c-language/dll-import-and-export-functions.md)
