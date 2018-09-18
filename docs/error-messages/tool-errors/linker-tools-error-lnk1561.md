---
title: Chyba Linkerů LNK1561 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1561
dev_langs:
- C++
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac24ed0c4aff4cbd7f0ea95ff71d0b8c4b3be09c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050759"
---
# <a name="linker-tools-error-lnk1561"></a>Chyba linkerů LNK1561

musí být definován vstupní bod

Propojovací program nebyl nalezen *vstupní bod*, počáteční funkce má být volána v spustitelný soubor. Ve výchozím nastavení, propojovací program vyhledá `main` nebo `wmain` funkce pro aplikaci konzoly, `WinMain` nebo `wWinMain` funkce aplikace pro Windows, nebo `DllMain` pro knihovnu DLL, která vyžaduje inicializace. Můžete zadat jiné funkce s použitím [/Entry](../../build/reference/entry-entry-point-symbol.md) – možnost linkeru.

Tato chyba může mít několik příčin:
- Nesmí obsahovat soubor, který definuje vstupní bod v seznamu souborů určených k propojení. Ověřte, že je propojený soubor, který obsahuje funkci vstupního bodu do vaší aplikace.
- Jste definovali pomocí nesprávného funkce podpis; vstupní bod například jste zadáno chybně nebo použít nesprávné případu pro název funkce a nesprávně zadaný návratový typ nebo typy parametrů.
- Zadali jste [/dll](../../build/reference/dll-build-a-dll.md) možnost při sestavování knihovny DLL.
- Možná jste zadali název funkci vstupního bodu správně při použití [/Entry](../../build/reference/entry-entry-point-symbol.md) – možnost linkeru.
- Pokud používáte [LIB](../../build/reference/lib-reference.md) nástroj k vytváření knihovny DLL, jste zadali .def souboru. Pokud ano, odeberte soubor .def ze sestavení.

Při sestavování aplikace, hledá linker funkci vstupního bodu volaná ke spuštění kódu. Toto je funkce, která je volána po načtení aplikace a modul runtime je inicializován. Je nutné zadat funkci vstupního bodu pro aplikaci nebo aplikaci nelze spustit. Vstupní bod je volitelný pro knihovnu DLL. Ve výchozím nastavení, hledá linker funkci vstupního bodu, který má jednu z několika specifickými názvy a podpisy, jako například `int main(int, char**)`. Můžete zadat jiný název funkce jako položku bodu pomocí možnosti linkeru/Entry.

## <a name="example"></a>Příklad

Následující ukázka generuje LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```