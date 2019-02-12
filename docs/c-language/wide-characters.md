---
title: Široké znaky
ms.date: 11/04/2016
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
ms.openlocfilehash: 868acf0abd26a1f4b5533bb997fb9ea09a27954b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151959"
---
# <a name="wide-characters"></a>Široké znaky

**ANSI 3.1.3.4** hodnota celočíselné znakové konstanty obsahující více než jeden znak nebo konstantu širokého znaku, který obsahuje více než jeden vícebajtový znak

Běžná znaková konstanta 'ab' má celočíselnou hodnotu (int)0x6162. Když je více než jeden bajt, jsou dříve přečtené bajty posunuty vlevo o hodnotu **CHAR_BIT** a následující bajt je porovnán pomocí bitového operátoru OR operátoru s nízkou **CHAR_BIT** bits. Počet bajtů ve vícebajtové znakové konstantě nemůže překročit hodnotu sizeof(int), která je pro 32bitový cílový kód 4.

Vícebajtová znaková konstanta je přečtena dle popisu výše a hodnota je převedena na konstantu širokého znaku pomocí funkce modulu runtime `mbtowc`. Není-li výsledek platnou konstantou širokého znaku, je vygenerována chyba. V každém případě je počet bajtů vyšetřených funkcí `mbtowc` omezen na hodnotu `MB_CUR_MAX`.

## <a name="see-also"></a>Viz také:

[Znaky](../c-language/characters.md)
