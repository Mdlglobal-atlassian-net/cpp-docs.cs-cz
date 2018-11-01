---
title: Testování pro nalezení chyb extrakce
ms.date: 11/04/2016
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
ms.openlocfilehash: 62d9c94f366ec666acf2179803c62e4a3ccd7e6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629226"
---
# <a name="testing-for-extraction-errors"></a>Testování pro nalezení chyb extrakce

Výstup funkcí pro zpracování chyb, popsané v [funkce zpracování chyb](../standard-library/output-file-stream-member-functions.md), platí pro vstupní datové proudy. Testování pro nalezení chyb během extrakce, je důležité. Vezměte v úvahu tento příkaz:

```cpp
cin>> n;
```

Pokud `n` je celé číslo se znaménkem, hodnotu větší než 32 767 (maximální povolená hodnota nebo MAX_INT) nastaví datový proud `fail` bit a `cin` objekt se stane nepoužitelné. Všechny následné extrakce za následek okamžité vrácení se žádná hodnota uložena.

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)<br/>
