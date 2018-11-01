---
title: Manipulátory vstupního datového proudu
ms.date: 11/04/2016
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
ms.openlocfilehash: 17f18aa127b84538229b3cf4e4246dfefb6c1f98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517959"
---
# <a name="input-stream-manipulators"></a>Manipulátory vstupního datového proudu

Mnoho manipulátory, jako například [setprecision](../standard-library/iomanip-functions.md#setprecision), jsou definovány pro `ios` třídy a tedy platí pro vstupní datové proudy. Několik manipulátory, ale ve skutečnosti vliv objektů vstupního datového proudu. To, které, nejdůležitější jsou manipulátory základ číselné soustavy `dec`, `oct`, a `hex`, které určují základní převod používá s čísly ze vstupního datového proudu.

Na extrakci `hex` manipulátor umožňuje zpracování různé vstupní formáty. Například, c C, 0xc, 0xC, 0Xc a 0XC jsou všechny interpretováno jako desítkové celé číslo 12. Jakéhokoliv znaku jiného než 0 – 9, A až F, a až f, x nebo X ukončí převod čísla. Proto pořadí `"124n5"` je převeden na číslo 124 s [basic_ios::fail](../standard-library/basic-ios-class.md#fail) nastaven bit.

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)<br/>
