---
title: Posuny doprava
ms.date: 11/04/2016
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
ms.openlocfilehash: c34373f69a41ad65031753cd352098dce7e98ef4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158356"
---
# <a name="right-shifts"></a>Posuny doprava

Výsledek pravého posunu typu integrál záporné hodnoty se znaménkem

Posunutí záporné hodnoty doprava dává polovinu absolutní hodnoty zaokrouhlené dolů. Například podepsaná `short` hodnota-253 (Hex 0xFF03, binary 11111111 00000011) posunutá doprava o jeden bit vytvoří-127 (Hex 0xFF81, binární 11111111 10000001). Kladné 253 posunuté vpravo vytvoří + 126.

Posunutí doprava zachovávají bit znaménka u podepsaných integrálních typů. Posune-li se celé číslo se znaménkem doprava, zůstane nejvýznamnější bit nastaven. Například pokud je 0xF0000000 podepsaný `int`, pravý posun vytvoří 0xF8000000. Posunutí negativního `int` pravého pravého 32ého času vytvoří 0xFFFFFFFF.

Posune-li se celé číslo bez znaménka doprava, je nejvýznamnější bit vymazán. Například pokud je 0xF000 bez znaménka, výsledek je 0x7800. Posunutí kladného `unsigned` `int` a pravého času 32 vytvoří 0x00000000.

## <a name="see-also"></a>Viz také

[Celá čísla](../c-language/integers.md)
