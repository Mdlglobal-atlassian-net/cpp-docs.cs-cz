---
title: Testování pro nalezení chyb extrakce
ms.date: 11/04/2016
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
ms.openlocfilehash: db551a21fd33665d83b11373f040be158406d492
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453669"
---
# <a name="testing-for-extraction-errors"></a>Testování pro nalezení chyb extrakce

Funkce zpracování chyb výstupu, které jsou popsány ve [funkcích zpracování chyb](../standard-library/output-file-stream-member-functions.md), se vztahují na vstupní datové proudy. Testování chyb během extrakce je důležité. Vezměte v úvahu tento příkaz:

```cpp
cin>> n;
```

Pokud `n` je celé číslo se znaménkem, hodnota větší než 32 767 (maximální povolená hodnota nebo MAX_INT) nastaví `fail` bit datového proudu a `cin` objekt se stane nepoužitelným. Všechna další extrakce mají za následek okamžité vrácení bez uložení hodnoty.

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)
