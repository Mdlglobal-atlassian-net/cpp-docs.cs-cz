---
title: pointers_to_members
ms.date: 11/04/2016
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: 5ee45a77a7094fb1ef9ba536bae391aaad00e812
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032060"
---
# <a name="pointerstomembers"></a>pointers_to_members

**Specifické pro C++**

Určuje, zda ukazatel na člen třídy lze deklarovat před definicí jeho přidružené třídy, a slouží k řízení velikosti ukazatele a kódu potřebného k interpretaci tohoto ukazatele.

## <a name="syntax"></a>Syntaxe

```
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )
```

## <a name="remarks"></a>Poznámky

Můžete umístit **pointers_to_members** – Direktiva pragma ve zdrojovém souboru jako alternativu k použití [/vmx](../build/reference/vmb-vmg-representation-method.md) – možnosti kompilátoru nebo [klíčová slova dědičnosti](../cpp/inheritance-keywords.md).

*Deklaraci ukazatele* argument určuje, zda je deklarován ukazatel na člen před nebo po definici související funkce. *Deklaraci ukazatele* argument je jedním z následujících dvou symbolů:

|Argument|Komentáře|
|--------------|--------------|
|*full_generality*|Generuje bezpečný, někdy neoptimální kód. Použijete *full_generality* Pokud je jakýkoli ukazatel na člen deklarován před definicí přidružené třídy. Tento argument vždy používá reprezentaci ukazatele určenou argumentem *most-general-representation* argument. Ekvivalentní možnosti /vmg.|
|*best_case*|Generuje bezpečný, optimální kód, který používá nejlepší reprezentaci pro všechny odkazy na členy. Vyžaduje definování třídy před deklarací ukazatele na člena této třídy. Výchozí hodnota je *best_case*.|

*Most-general-representation* argument určuje nejmenší reprezentaci ukazatele, který kompilátor může bezpečně použít k odkazování na jakýkoli ukazatel na člen třídy v jednotce překladu. Tento argument může nabývat kterékoliv z těchto hodnot:

|Argument|Komentáře|
|--------------|--------------|
|*single_inheritance*|Nejobecnější reprezentace je jediná dědičnost, ukazatel na členskou funkci. Způsobí chybu, je-li model dědičnosti definice třídy, pro kterou je ukazatel na člen deklarován jako vícenásobný nebo virtuální.|
|*multiple_inheritance*|Nejobecnější reprezentace je vícenásobná dědičnost, ukazatel na členskou funkci. Způsobí chybu, je-li model dědičnosti definice třídy, pro kterou je ukazatel na člen deklarován jako virtuální.|
|*virtual_inheritance*|Nejobecnější reprezentace je virtuální dědičnost, ukazatel na členskou funkci. Nikdy nezpůsobí chybu. Toto je výchozí argument při `#pragma pointers_to_members(full_generality)` se používá.|

> [!CAUTION]
> Doporučujeme umístit **pointers_to_members** – Direktiva pragma pouze v souboru se zdrojovým kódem, který chcete ovlivnit a až po všech `#include` direktivy. Tímto postupem snížíte riziko, že tato direktiva pragma ovlivní další soubory a že bude náhodně zadáno více definic pro stejnou proměnnou, funkci nebo název třídy.

## <a name="example"></a>Příklad

```
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

## <a name="end-c-specific"></a>Specifické pro END C++

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)