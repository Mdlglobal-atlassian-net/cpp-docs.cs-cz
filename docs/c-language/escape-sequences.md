---
title: "Řídicí sekvence | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8206f239af5ab8be0f20eed0f73b4ad0f1ba7e2f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="escape-sequences"></a>Řídicí sekvence
Znak kombinace skládající se z zpětné lomítko (**\\**) následuje písmeno, nebo kombinací číslic se nazývají "řídicích sekvencí." Pro zapsání znaku nového řádku, jednoduchých uvozovek nebo určitých jiných znaků ve znakových konstantách, je nutné použít řídicí sekvence. Řídicí sekvence je považována za jeden znak, a proto je platná jako znaková konstanta.  
  
 Řídicí sekvence se obvykle používají k určení akce, jako například návrat na začátek řádku a pohyb tabelátoru na terminálech a tiskárnách. Používají se také zajistit literálu reprezentace netisknutelné znaky a znaky, které obvykle mají zvláštní význam, jako je například dvojité uvozovky (**"**). V následující tabulce jsou uvedeny řídicí sekvence ANSI a co představují.  
  
 Všimněte si, že znaky otazníku předcházet zpětné lomítko (**\\?**) určuje literálu otazník v případech, kde je sekvence znaků by dojít k nesprávné interpretaci jako trigraph. V tématu [trigraph](../c-language/trigraphs.md) Další informace.  
  
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
|**\\***ooo*|Znak ASCII v osmičkové soustavě|  
|**\x** *hh*|Znak ASCII v šestnáctkové soustavě|  
|**\x** *hhhh*|Znak Unicode v šestnáctkovém zápisu, pokud je tato řídicí sekvence použita v širokoznaké konstantě nebo literálu řetězce kódování Unicode.<br /><br /> Například `WCHAR f = L'\x4e00'` nebo `WCHAR b[] = L"The Chinese character for one is \x4e00"`.|  
  
 **Konkrétní Microsoft**  
  
 Pokud zpětné lomítko předchází znaku, který není uveden v tabulce, kompilátor zpracovává nedefinovaný znak jako znak samotný. Například `\c` je považován za `c`.  
  
 **Konkrétní Microsoft END**  
  
 Řídicí sekvence umožňují odeslat negrafické řídicí znaky na zobrazovací zařízení. Například znak ESC (**\033**) se často používá jako první znak řízení zabezpečení pro Terminálové nebo tiskárny. Některé řídicí sekvence jsou specifické pro zařízení. Pro instanci svislého – karta a formfeed řídicích sekvencí (**\v** a **\f**) neovlivní výstupu obrazovky, ale budou provádět operace odpovídající tiskárny.  
  
 Můžete také zpětné lomítko (**\\**) jako znak pokračování. Když znak nového řádku (ekvivalentní stisknutí klávesy RETURN) okamžitě následuje lomítko, kompilátor ignoruje zpětné lomítko a znak nového řádku a považuje nový řádek za součást předchozího řádku. To je užitečné především pro definice preprocesoru delší než jeden řádek. Příklad:  
  
```  
#define assert(exp) \  
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )  
```  
  
## <a name="see-also"></a>Viz také  
 [Konstanty znaků jazyka C](../c-language/c-character-constants.md)