---
title: Řídicí sekvence
ms.date: 11/04/2016
helpviewer_keywords:
- "\r escape sequence"
- double backslash
- horizontal-tab 	 escape sequence
- (') single quotation mark
- "bell character \a escape sequence"
- escape sequences
- hexadecimal escape sequence
- carriage returns
- tab 	 escape sequence
- "\f escape sequence"
- quotation marks, single
- "formfeed \f escape sequence"
- "\v escape sequence"
- control character escape sequences
- " symbol in escape sequences"
- octal escape sequence
- escape characters
- "newline character \n escape sequence"
- nongraphic control characters
- question mark, literal
- "\nescape sequence"
- "vertical tab \v escape sequence"
- "\a escape sequence"
- '? symbol'
- '? symbol, escape sequence character'
- "	 escape sequence"
- backspace escape sequence
ms.assetid: 5aef377f-a76c-4d5c-aa04-8308758ad6a8
ms.openlocfilehash: 810d091b923bd976a4a8bbe6814e8ddc0b243bcd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431197"
---
# <a name="escape-sequences"></a>Řídicí sekvence

Kombinace znaků obsahující zpětné lomítko (**\\**) následované písmenem nebo kombinací číslic se nazývají "řídicí sekvence". Pro zapsání znaku nového řádku, jednoduchých uvozovek nebo určitých jiných znaků ve znakových konstantách, je nutné použít řídicí sekvence. Řídicí sekvence je považována za jeden znak, a proto je platná jako znaková konstanta.

Řídicí sekvence se obvykle používají k určení akce, jako například návrat na začátek řádku a pohyb tabelátoru na terminálech a tiskárnách. Také se používají pro literální reprezentaci netisknutelných znaků a znaků, které mají obvykle zvláštní význam, jako je například dvojité uvozovky (**"**). V následující tabulce jsou uvedeny řídicí sekvence ANSI a co představují.

Všimněte si, že otazníku předchází znak zpětného lomítka (**\\?**) určuje literálu otazníku v případech, kde by být posloupnost znaků špatně interpretována jako Triplet. Zobrazit [Trigraphs](../c-language/trigraphs.md) Další informace.

### <a name="escape-sequences"></a>Řídicí sekvence

|Řídicí sekvence|Představuje|
|---------------------|----------------|
|**\a**|Zvonek (alarm)|
|**\b**|Backspace|
|**\f**|Formfeed|
|**\n**|Nový řádek|
|**\r**|Návrat na začátek řádku|
|**\t**|Horizontální tabulátor|
|**\v**|Vertikální tabulátor|
|**\\'**|Jednoduché uvozovky|
|**\\"**|Dvojité uvozovky|
|**\\\\**|Zpětné lomítko|
|**\\?**|Literální znak otazníku|
|**\\** *ooo*|Znak ASCII v osmičkové soustavě|
|**\x** *hh*|Znak ASCII v šestnáctkové soustavě|
|**\x** *hhhh*|Znak Unicode v šestnáctkovém zápisu, pokud je tato řídicí sekvence použita v širokoznaké konstantě nebo literálu řetězce kódování Unicode.<br /><br /> Například `WCHAR f = L'\x4e00'` nebo `WCHAR b[] = L"The Chinese character for one is \x4e00"`.|

**Specifické pro Microsoft**

Pokud zpětné lomítko předchází znaku, který není uveden v tabulce, kompilátor zpracovává nedefinovaný znak jako znak samotný. Například `\c` je považován za `c`.

**Specifické pro END Microsoft**

Řídicí sekvence umožňují odeslat negrafické řídicí znaky na zobrazovací zařízení. Například znak ESC (**\033**) se často používá jako první znak ovládacího příkazu pro terminál nebo tiskárnu. Některé řídicí sekvence jsou specifické pro zařízení. Například vertikálního tabelátoru a formfeed řídicí sekvence (**\v** a **\f**) nemají vliv na výstup obrazovky, ale provádějí příslušné operace při tisku.

Můžete také použít zpětné lomítko (**\\**) jako znak pro pokračování. Když znak nového řádku (ekvivalentní stisknutí klávesy RETURN) okamžitě následuje lomítko, kompilátor ignoruje zpětné lomítko a znak nového řádku a považuje nový řádek za součást předchozího řádku. To je užitečné především pro definice preprocesoru delší než jeden řádek. Příklad:

```
#define assert(exp) \
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )
```

## <a name="see-also"></a>Viz také

[Konstanty znaků jazyka C](../c-language/c-character-constants.md)