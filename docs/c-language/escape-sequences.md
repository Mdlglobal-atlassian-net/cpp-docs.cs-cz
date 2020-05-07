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
- "form feed \f escape sequence"
- "\v escape sequence"
- control character escape sequences
- " symbol in escape sequences"
- octal escape sequence
- escape characters
- "newline character \n escape sequence"
- nongraphic control characters
- question mark, literal
- "\n escape sequence"
- "vertical tab \v escape sequence"
- "\a escape sequence"
- '? symbol'
- '? symbol, escape sequence character'
- "	 escape sequence"
- backspace escape sequence
ms.assetid: 5aef377f-a76c-4d5c-aa04-8308758ad6a8
ms.openlocfilehash: 5de0b5f1a73fcfb6ea0325bea3247ebe4c85d411
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375826"
---
# <a name="escape-sequences"></a>Řídicí sekvence

Kombinace znaků sestávající z zpětného lomítka**\\**() následovaného písmenem nebo kombinací číslic se nazývají "řídicí sekvence". Pro zapsání znaku nového řádku, jednoduchých uvozovek nebo určitých jiných znaků ve znakových konstantách, je nutné použít řídicí sekvence. Řídicí sekvence je považována za jeden znak, a proto je platná jako znaková konstanta.

Řídicí sekvence se obvykle používají k určení akce, jako například návrat na začátek řádku a pohyb tabelátoru na terminálech a tiskárnách. Používají se také k poskytnutí literálů pro netisknutelné znaky a znaky, které obvykle mají zvláštní význam, jako je například dvojité uvozovky (**"**). V následující tabulce jsou uvedeny řídicí sekvence ANSI a co představují.

Všimněte si, že otazník před zpětným lomítkem (**\\?**) určuje znak otazníku v případech, kdy by byla sekvence znaků chybně interpretována jako trigraph. Další informace najdete v tématu [trigraphs](../c-language/trigraphs.md) .

### <a name="escape-sequences"></a>Řídicí sekvence

|Řídicí sekvence|Představuje|
|---------------------|----------------|
|**\**|Zvonek (alarm)|
|**\b**|Backspace|
|**\f**|Informační kanál formuláře|
|**\n**|Nový řádek|
|**\r**|Návrat na začátek řádku|
|**\t**|Horizontální tabulátor|
|**\v**|Vertikální tabulátor|
|**\\'**|Jednoduché uvozovky|
|**\\"**|Dvojité uvozovky|
|**\\\\**|Zpětné lomítko|
|**\\?**|Literální znak otazníku|
|**\\***OOO*|Znak ASCII v osmičkové soustavě|
|**\x** *HH*|Znak ASCII v šestnáctkové soustavě|
|**\x** *hhhh*|Znak Unicode v šestnáctkovém zápisu, pokud je tato řídicí sekvence použita v širokoznaké konstantě nebo literálu řetězce kódování Unicode.<br /><br /> Příkladem je `WCHAR f = L'\x4e00'` nebo `WCHAR b[] = L"The Chinese character for one is \x4e00"`.|

**Specifické pro Microsoft**

Pokud zpětné lomítko předchází znaku, který není uveden v tabulce, kompilátor zpracovává nedefinovaný znak jako znak samotný. Například `\c` je považován za `c`.

**Specifické pro konec Microsoftu**

Řídicí sekvence umožňují odeslat negrafické řídicí znaky na zobrazovací zařízení. Například znak ESC (**\ 033**) se často používá jako první znak řídicího příkazu pro terminál nebo tiskárnu. Některé řídicí sekvence jsou specifické pro zařízení. Například svislé sekvence kláves a řídicí sekvence (**\v** a **\f**) na obrazovce neovlivňují výstup obrazovky, ale provádějí vhodné operace s tiskárnou.

Zpětné lomítko (**\\**) můžete použít také jako znak pro pokračování. Když znak nového řádku (ekvivalentní stisknutí klávesy RETURN) okamžitě následuje lomítko, kompilátor ignoruje zpětné lomítko a znak nového řádku a považuje nový řádek za součást předchozího řádku. To je užitečné především pro definice preprocesoru delší než jeden řádek. Příklad:

```
#define assert(exp) \
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )
```

## <a name="see-also"></a>Viz také

[Konstanty znaků jazyka C](../c-language/c-character-constants.md)
