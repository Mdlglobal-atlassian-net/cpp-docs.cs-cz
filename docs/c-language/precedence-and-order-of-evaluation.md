---
title: Přednost a pořadí vyhodnocení
ms.date: 11/04/2016
helpviewer_keywords:
- associativity of operators [C++]
- precedence [C++], operators
- data binding [C++], operator precedence
- operators [C++], precedence
ms.assetid: 201f7864-0c51-4c55-9d6f-39c5d013bcb0
ms.openlocfilehash: 1b14f7a7d0c1d682c641ab441dc3e40c23688392
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463255"
---
# <a name="precedence-and-order-of-evaluation"></a>Přednost a pořadí vyhodnocení

Priorita a asociativita operátorů jazyka C ovlivní seskupování a vyhodnocování operandů ve výrazech. Priorita operátoru má smysl pouze v případě, že jsou přítomny operátory s nižší nebo vyšší prioritou. Výrazy s operátory s vyšší prioritou jsou vyhodnoceny jako první. Prioritu lze popsat také slovem „vazba“. O operátorech s vyšší prioritou se říká, že mají silnější vazbu.

Následující tabulka shrnuje prioritu a asociativitu (tedy pořadí, v němž jsou vyhodnoceny operandy) operátorů jazyka C v pořadí dle priority od nejvyšší k nejnižší. Vyskytne-li se několik operátorů pohromadě, mají stejnou prioritu a jsou vyhodnoceny dle své asociativity. Operátory v tabulce jsou popsány v oddílech začínajících oddílem [Příponové operátory](../c-language/postfix-operators.md). Zbytek tohoto oddílu poskytuje obecné informace o prioritě a asociativitě.

## <a name="precedence-and-associativity-of-c-operators"></a>Priorita a asociativita operátorů jazyka C

|Symbol <sup>1</sup>|Typ operace|Asociativita|
|-------------|-----------------------|-------------------|
|**\[ ] ( ) . ->**<br /><br />**++** **--** (přípona)|Výraz|Zleva doprava|
**sizeof & \* + – ~!**<br /><br />**++--** (předpona)|Unární|Zprava doleva|
|*zaokrouhlovat*|Unární|Zprava doleva|
|**\* / %**|Násobení|Zleva doprava|
|**+ -**|Additive|Zleva doprava|
|**\<\< >>**|Bitový posun|Zleva doprava|
|**\< > \<= >=**|Relační|Zleva doprava|
|**== !=**|Rovnost|Zleva doprava|
|**&**|Bitový operátor AND|Zleva doprava|
|**^**|Bitový exkluzivní operátor OR|Zleva doprava|
|**&#124;**|Bitový inkluzivní operátor OR|Zleva doprava|
|**&&**|Logický operátor AND|Zleva doprava|
|**&#124;&#124;**|Logický operátor OR|Zleva doprava|
|**? :**|Podmíněný výraz|Zprava doleva|
|**= \*= /= %=**<br /><br /> **+= -= \<\<= >>= &=**<br /><br /> **^= &#124;=**|Jednoduché a složené přiřazení <sup>2</sup>|Zprava doleva|
|**,**|Sekvenční vyhodnocení|Zleva doprava|

1. Operátory jsou uvedeny v sestupném pořadí dle priority. Je-li několik operátorů uvedeno na stejném řádku nebo ve skupině, mají stejnou prioritu.

1. Všechny operátory jednoduchého a složeného přiřazení mají stejnou prioritu.

Výraz může obsahovat několik operátorů shodné priority. Vyskytne-li se na stejné úrovni ve výrazu několik takových operátorů, vyhodnocování pokračuje dle asociativity operátorů, tedy zleva doprava nebo zprava doleva. Směr vyhodnocení neovlivní výsledky výrazů, které obsahují více než jedno násobení (<strong>\*</strong>), sčítání (**+**), nebo binární bitový (**&**, **&#124;**, nebo **^**) operátor na stejné úrovni. Pořadí operací není v jazyce definováno. Dokáže-li kompilátor zaručit konzistentní výsledek, může takové výrazy vyhodnotit v libovolném pořadí.

Pouze sekvenční vyhodnocení (**,**), logický- a (**&&**), logický operátor OR (**||**), podmíněný výraz (**?:** ), a operátorů volání funkce představují body sekvence a zaručují konkrétní pořadí vyhodnocení svých operandů. Operátorem volání funkce je sada závorek za identifikátorem funkce. Operátor sekvenčního vyhodnocení (**,**) zaručuje vyhodnocení operandů zleva doprava. (Povšimněte si, že operátor čárky ve volání funkce není totéž jako operátor sekvenčního vyhodnocení, a žádnou takovou záruku tak neposkytuje.) Další informace najdete v tématu [body sekvence](../c-language/c-sequence-points.md).

Logické operátory rovněž zaručují vyhodnocení svých operandů zleva doprava. Vyhodnocují však nejmenší počet operandů potřebných k určení výsledků výrazu. Tento postup se nazývá „zkrácené“ vyhodnocení. Některé operandy výrazu tedy nemusí být vyhodnoceny. Například ve výrazu

`x && y++`

je druhý operand, `y++`, vyhodnocen pouze v případě, že operand `x` je vyhodnocen na hodnotu true (nenulovou). Operand `y` tedy nebude navýšen, bude-li operand `x` vyhodnocen na hodnotu false (0).

## <a name="examples"></a>Příklady

Následující seznam ukazuje, jak kompilátor automaticky sváže několik vzorových výrazů:

|Výraz|Automatické vázání|
|----------------|-----------------------|
|& b &#124; &#124; c|(& b). &#124; &#124; c|
|a = b &#124;&#124; c|a = (b &#124; &#124; c).|
|q && r &#124;&#124; s--|(q & & r) &#124; &#124; s--|

V prvním výrazu bitový – a – operátor (**&**) má vyšší prioritu než logický operátor OR – operátor (**||**), takže `a & b` tvoří první operand operace logického operátoru OR.

Ve druhém výrazu logický operátor OR (**||**) má vyšší prioritu než operátor jednoduchého přiřazení (**=**), takže `b || c` seskupen jako Chcete-li operand pravé strany v přiřazení. Povšimněte si, že hodnota přiřazená proměnné `a` je 0 nebo 1.

Třetí výraz ukazuje výraz správného tvaru, který může být vyhodnocen na neočekávaný výsledek. Logický- a – operátor (**&&**) má vyšší prioritu než logický operátor OR – operátor (**||**), takže `q && r` seskupen jako operand. Protože logické operátory zaručují vyhodnocování operandů zleva doprava, `q && r` je vyhodnoceno před `s--`. Nicméně pokud `q && r` vyhodnocen na nenulovou hodnotu, `s--` není vyhodnocen, a `s` není snížena. Pokud nesnížení `s` způsobilo potíže v programu, `s--` by se měla zobrazit jako první operand výrazu, nebo `s` by měla být snížena v samostatné operaci.

Následující výraz není platný a vyvolá při kompilaci diagnostickou zprávu:

|Neplatný výraz|Výchozí seskupení|
|------------------------|----------------------|
|p == 0? p += 1: p += 2|(p == 0? p += 1: p) += 2|

V tomto výrazu operátor rovnosti (**==**) má nejvyšší prioritu, takže `p == 0` seskupen jako operand. Operátor podmíněného výrazu (**?:**) má druhou nejvyšší prioritu. Jeho prvním operandem je výraz `p == 0`, jeho druhým operandem pak výraz `p += 1`. Za poslední operand v operátoru podmíněného výrazu je však považován výraz `p` místo výrazu `p += 2`, protože tento výskyt proměnné `p` je více svázán s operátorem podmíněného výrazu než s operátorem složeného přiřazení. Výraz `+= 2` nemá operand na levé straně, dojde tedy k chybě syntaxe. Chcete-li zabránit chybám tohoto typu a vytvářet čitelnější kód, měly by být použity závorky. Závorky by měly být použity například jako v ukázce níže, která předchozí příklad opravuje a ujasňuje:

`( p == 0 ) ? ( p += 1 ) : ( p += 2 )`

## <a name="see-also"></a>Viz také

[Operátory jazyka C](../c-language/c-operators.md)
