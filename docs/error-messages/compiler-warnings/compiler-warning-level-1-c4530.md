---
title: Upozornění kompilátoru (úroveň 1) C4530
description: Referenční příručka pro microsoft c++ kompilátor upozornění C4530.
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 9de88a4b0b6c7176ff82b68c92d09d9fe75a70b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369787"
---
# <a name="compiler-warning-level-1-c4530"></a>Upozornění kompilátoru (úroveň 1) C4530

> Používá se obslužná rutina výjimky jazyka C++, ale unwind sémantiku nejsou povoleny. Zadat /EHsc

Kód používá zpracování výjimek Jazyka C++, ale [/EHsc](../../build/reference/eh-exception-handling-model.md) nebyl zahrnut do možností kompilátoru.

## <a name="remarks"></a>Poznámky

Kompilátor vyžaduje **`/EHsc`** možnost vytvořit kód Jazyka C++, který následuje za standardem Jazyka C++ pro zpracování výjimek. Standardní *sémantiku unwind* jazyka C++ určuje, že objekty a rámce zásobníku vytvořené mezi místem, kde je vyvolána výjimka, a kde je zachycena, musí být zničena a jejich prostředky obnoveny. Tento proces se označuje jako *odvíjení zásobníku*.

Možnost **`/EHsc`** říká kompilátoru generovat kód, který volá destruktory na objekty automatickéúložiště při průchodu výjimky obsahující rámec zásobníku. *Objekty automatického úložiště* jsou objekty přidělené v zásobníku, například místní proměnné. Říká se tomu automatické úložiště, protože se přiřazuje automaticky při volání funkcí a automaticky se uvolňuje, když se vrátí. *Rámec zásobníku* je data umístěná v zásobníku při volání funkce, spolu s jeho automatické úložiště.

Při vyvolání výjimky může cestovat přes několik rámců zásobníku před jeho chycení. Tyto rámce zásobníku musí být odvíjeny, protože výjimka prochází jimi v obráceném pořadí volání. Objekty automatického úložiště v každém rámci zásobníku musí být zničeny, aby bylo možné jejich prostředky obnovit čistě. Je to stejný proces zničení a obnovení, který se stane automaticky, když se funkce vrátí normálně.

Pokud **`/EHsc`** tato možnost není povolena, automatické objekty úložiště v rámcích zásobníku mezi funkcí vyvolání a funkcí, kde je výjimka zachycena, se nezničí. Zničeny byly pouze objekty automatického úložiště vytvořené v bloku **try** nebo **catch,** což může vést k významným nevracením prostředků a dalším neočekávaným chováním.

Pokud žádné výjimky může být vyvolána ve spustitelném souboru, můžete bezpečně ignorovat toto upozornění. Některé kódmůže vyžadovat jiné možnosti zpracování výjimek. Další informace naleznete v tématu [/EH](../../build/reference/eh-exception-handling-model.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4530:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Zkompilujte **`/EHsc`** ukázku s vyřešit upozornění.
