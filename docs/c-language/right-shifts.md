---
title: Klikněte pravým tlačítkem myši Staffhubu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f31ebddb38d1eb1cafe9495f8c121811ec502524
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032408"
---
# <a name="right-shifts"></a>Posuny doprava

Výsledek pravého posunutí záporné hodnoty celočíselného typu se znaménkem

Posunutí záporné hodnoty doprava dává polovinu absolutní hodnoty zaokrouhlené dolů. Například podepsané `short` hodnotu-253 (hexadecimální 0xFF03, binární 11111111 00000011) posunuta jeden bit doprava vytvoří-127 (hexadecimální 0xFF81, Binárně 11111111 10000001). Pozitivní 253 se posune doprava vytvoří hodnotu + 126.

Posuny doprava zachovává bit znaménka celočíselných typů se znaménkem. Posune-li se celé číslo se znaménkem doprava, zůstane nejvýznamnější bit nastaven. Například, pokud je 0xF0000000 se znaménkem `int`, pravé posunutí 0xf8000000. Posunutí záporné `int` doprava 32krát vytvoří 0xFFFFFFFF.

Posune-li se celé číslo bez znaménka doprava, je nejvýznamnější bit vymazán. Například je-li 0xF000 bez znaménka, výsledek je 0x7800. Posun `unsigned` nebo kladné `int` doprava 32krát vytvoří 0x00000000.

## <a name="see-also"></a>Viz také

[Celá čísla](../c-language/integers.md)