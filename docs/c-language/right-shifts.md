---
title: Posuny doprava
ms.date: 11/04/2016
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
ms.openlocfilehash: c34373f69a41ad65031753cd352098dce7e98ef4
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149476"
---
# <a name="right-shifts"></a>Posuny doprava

Výsledek pravého posunutí záporné hodnoty celočíselného typu se znaménkem

Posunutí záporné hodnoty doprava dává polovinu absolutní hodnoty zaokrouhlené dolů. Například podepsané `short` hodnotu-253 (hexadecimální 0xFF03, binární 11111111 00000011) posunuta jeden bit doprava vytvoří-127 (hexadecimální 0xFF81, Binárně 11111111 10000001). Pozitivní 253 se posune doprava vytvoří hodnotu + 126.

Posuny doprava zachovává bit znaménka celočíselných typů se znaménkem. Posune-li se celé číslo se znaménkem doprava, zůstane nejvýznamnější bit nastaven. Například, pokud je 0xF0000000 se znaménkem `int`, pravé posunutí 0xf8000000. Posunutí záporné `int` doprava 32krát vytvoří 0xFFFFFFFF.

Posune-li se celé číslo bez znaménka doprava, je nejvýznamnější bit vymazán. Například je-li 0xF000 bez znaménka, výsledek je 0x7800. Posun `unsigned` nebo kladné `int` doprava 32krát vytvoří 0x00000000.

## <a name="see-also"></a>Viz také:

[Celá čísla](../c-language/integers.md)
