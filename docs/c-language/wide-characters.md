---
title: Široké znaky
ms.date: 11/04/2016
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
ms.openlocfilehash: 868acf0abd26a1f4b5533bb997fb9ea09a27954b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290999"
---
# <a name="wide-characters"></a>Široké znaky

**3.1.3.4 ANSI** Hodnota celočíselné znakové konstanty, která obsahuje více než jeden znak nebo konstantu celé znaky, která obsahuje více než jeden vícebajtový znak

Běžná znaková konstanta 'ab' má celočíselnou hodnotu (int)0x6162. Pokud existuje více než jeden bajt, dříve přečtené bajty jsou posunuty doleva podle hodnoty **CHAR_BIT** a další bajt se porovnává pomocí bitového operátoru OR s nízkou **CHAR_BITou** bitů. Počet bajtů ve vícebajtové znakové konstantě nemůže překročit hodnotu sizeof(int), která je pro 32bitový cílový kód 4.

Vícebajtová znaková konstanta je přečtena dle popisu výše a hodnota je převedena na konstantu širokého znaku pomocí funkce modulu runtime `mbtowc`. Není-li výsledek platnou konstantou širokého znaku, je vygenerována chyba. V každém případě je počet bajtů vyšetřených funkcí `mbtowc` omezen na hodnotu `MB_CUR_MAX`.

## <a name="see-also"></a>Viz také

[Znaky](../c-language/characters.md)
