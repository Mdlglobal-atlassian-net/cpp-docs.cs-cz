---
title: Přednost a pořadí vyhodnocení
ms.date: 07/11/2019
helpviewer_keywords:
- associativity of operators [C++]
- precedence [C++], operators
- data binding [C++], operator precedence
- operators [C++], precedence
ms.assetid: 201f7864-0c51-4c55-9d6f-39c5d013bcb0
ms.openlocfilehash: 327a5a5344f17f1d84e0cebc1371d56426c95deb
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861080"
---
# <a name="precedence-and-order-of-evaluation"></a>Přednost a pořadí vyhodnocení

Priorita a asociativita operátorů jazyka C ovlivní seskupování a vyhodnocování operandů ve výrazech. Priorita operátoru má smysl pouze v případě, že jsou přítomny operátory s nižší nebo vyšší prioritou. Výrazy s operátory s vyšší prioritou jsou vyhodnoceny jako první. Prioritu lze popsat také slovem „vazba“. O operátorech s vyšší prioritou se říká, že mají silnější vazbu.

Následující tabulka shrnuje prioritu a asociativitu (tedy pořadí, v němž jsou vyhodnoceny operandy) operátorů jazyka C v pořadí dle priority od nejvyšší k nejnižší. Vyskytne-li se několik operátorů pohromadě, mají stejnou prioritu a jsou vyhodnoceny dle své asociativity. Operátory v tabulce jsou popsány v oddílech od [operátorů přípon](../c-language/postfix-operators.md). Zbytek tohoto oddílu poskytuje obecné informace o prioritě a asociativitě.

## <a name="precedence-and-associativity-of-c-operators"></a>Priorita a asociativita operátorů jazyka C

| Symbol <sup>1</sup> | Typ operace | Asociativita |
|-------------|-----------------------|-------------------|
| `[` `]` `(` `)` `.` `->`<br/>`++``--` (přípona) | Expression | Zleva doprava |
| **sizeof** `&` `*` `+` `-` `~` `!`<br/>`++``--` (předpona) | Unární | Zprava doleva |
| *přetypování* | Unární | Zprava doleva |
| `*` `/` `%` | Multiplikativní | Zleva doprava |
| `+` `-` | Přičítáním | Zleva doprava |
| `<<` `>>` | Bitový posun | Zleva doprava |
| `<` `>` `<=` `>=` | Relační | Zleva doprava |
| `==` `!=` | Rovnost | Zleva doprava |
| `&` | Bitový operátor AND | Zleva doprava |
| `^` | Bitový exkluzivní operátor OR | Zleva doprava |
| `|` | Bitový inkluzivní operátor OR | Zleva doprava |
| `&&` | Logický operátor AND | Zleva doprava |
| `||` | Logický operátor OR | Zleva doprava |
| `? :` | Podmíněný výraz | Zprava doleva |
| `=` `*=` `/=` `%=`<br/>`+=` `-=` `<<=` `>>=` `&=`<br/>`^=` `|=` | Jednoduché a složené přiřazení <sup>2</sup> | Zprava doleva |
| `,` | Sekvenční vyhodnocení | Zleva doprava |

<sup>1</sup> operátory jsou uvedeny v sestupném pořadí podle priority. Je-li několik operátorů uvedeno na stejném řádku nebo ve skupině, mají stejnou prioritu.

<sup>2</sup> všechny jednoduché a složené operátory přiřazení mají stejnou prioritu.

Výraz může obsahovat několik operátorů shodné priority. Vyskytne-li se na stejné úrovni ve výrazu několik takových operátorů, vyhodnocování pokračuje dle asociativity operátorů, tedy zleva doprava nebo zprava doleva. Směr vyhodnocení nemá vliv na výsledky výrazů, které obsahují více než jeden operátor násobení`*`(), sčítání (`+`) nebo binární bitové kopie (`&`, `|`nebo `^`) na stejné úrovni. Pořadí operací není v jazyce definováno. Dokáže-li kompilátor zaručit konzistentní výsledek, může takové výrazy vyhodnotit v libovolném pořadí.

Pouze sekvence sekvenčního vyhodnocení (`,`), logický operátor and (`&&`), logického operátoru`||`or (), podmíněného`? :`výrazu () a volání funkce představují body sekvence, a proto zaručují konkrétní pořadí vyhodnocení pro své operandy. Operátorem volání funkce je sada závorek za identifikátorem funkce. Operátor sekvenčního vyhodnocení (`,`) zaručuje vyhodnocení jeho operandů zleva doprava. (Operátor čárka ve volání funkce není stejný jako operátor sekvenčního vyhodnocení a neposkytuje žádnou takovou záruku.) Další informace naleznete v tématu [body sekvence](c-sequence-points.md).

Logické operátory rovněž zaručují vyhodnocení svých operandů zleva doprava. Vyhodnocují však nejmenší počet operandů potřebných k určení výsledků výrazu. Tento postup se nazývá „zkrácené“ vyhodnocení. Některé operandy výrazu tedy nemusí být vyhodnoceny. Například ve výrazu

`x && y++`

je druhý operand, `y++`, vyhodnocen pouze v případě, že operand `x` je vyhodnocen na hodnotu true (nenulovou). Operand `y` tedy nebude navýšen, bude-li operand `x` vyhodnocen na hodnotu false (0).

## <a name="examples"></a>Příklady

Následující seznam ukazuje, jak kompilátor automaticky sváže několik vzorových výrazů:

| Expression | Automatické vázání |
|----------------|-----------------------|
| `a & b || c` | `(a & b) || c` |
| `a = b || c` | `a = (b || c)` |
| `q && r || s--` | `(q && r) || s--` |

V prvním výrazu bitový operátor AND (`&`) má vyšší prioritu než logický operátor OR (`||`), proto výraz `a & b` tvoří první operand operace logického operátoru OR.

Ve druhém výrazu má logický operátor OR (`||`) vyšší prioritu než operátor jednoduchého přiřazení (`=`), proto je výraz `b || c` v přiřazení seskupen jako operand pravé strany. Povšimněte si, že hodnota přiřazená proměnné `a` je 0 nebo 1.

Třetí výraz ukazuje výraz správného tvaru, který může být vyhodnocen na neočekávaný výsledek. Logický operátor AND (`&&`) má vyšší prioritu než logický operátor OR (`||`), proto je výraz `q && r` seskupen jako operand. Vzhledem k tomu, že logické operátory zaručují vyhodnocování operandů zleva doprava `q && r` , je vyhodnocen před `s--`. Pokud `q && r` se však vyhodnotí jako nenulová hodnota, `s--` není vyhodnocena a `s` není snížena. Pokud `s` by snížení hodnoty způsobilo, že by došlo k problému `s--` v programu, měl by se zobrazit jako první operand výrazu `s` , nebo by měl být snížen v samostatné operaci.

Následující výraz není platný a vyvolá při kompilaci diagnostickou zprávu:

| Neplatný výraz | Výchozí seskupení |
|------------------------|----------------------|
| `p == 0 ? p += 1: p += 2` | `( p == 0 ? p += 1 : p ) += 2` |

V tomto výrazu má operátor rovnosti (`==`) nejvyšší prioritu, proto je výraz `p == 0` seskupen jako operand. Operátor podmíněného výrazu (`? :`) má druhou nejvyšší prioritu. Jeho prvním operandem je výraz `p == 0`, jeho druhým operandem pak výraz `p += 1`. Za poslední operand v operátoru podmíněného výrazu je však považován výraz `p` místo výrazu `p += 2`, protože tento výskyt proměnné `p` je více svázán s operátorem podmíněného výrazu než s operátorem složeného přiřazení. Výraz `+= 2` nemá operand na levé straně, dojde tedy k chybě syntaxe. Chcete-li zabránit chybám tohoto typu a vytvářet čitelnější kód, měly by být použity závorky. Závorky by měly být použity například jako v ukázce níže, která předchozí příklad opravuje a ujasňuje:

`( p == 0 ) ? ( p += 1 ) : ( p += 2 )`

## <a name="see-also"></a>Viz také

[Operátory jazyka C](c-operators.md)
