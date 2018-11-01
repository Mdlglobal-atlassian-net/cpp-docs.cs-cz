---
title: MxCsr
ms.date: 11/04/2016
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
ms.openlocfilehash: d411223634aec6d11413ac1f5b1fb04dba7498e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497369"
---
# <a name="mxcsr"></a>MxCsr

Stav registrace také zahrnuje MxCsr. Konvence volání tento registr rozděluje volatile část a stálé část. Volatile část se skládá z příznaky 6 stavu MXCSR [0:5], zatímco zbytek do registru MXCSR [6:15], je považován za stálé.

Stálé část je nastaven na následující standardní hodnoty na začátku spuštění programu:

```
MXCSR[6]         : Denormals are zeros - 0
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)
```

Volaný, který změní libovolné stálé pole v rámci MXCSR musí obnovit před vrácením volající funkci. Kromě toho volající, který změní některé z těchto polí musí obnovit na standardní hodnoty před vyvoláním volaného Pokud smlouvou volaný očekává, že změněné hodnoty.

Existují dvě výjimky k pravidlům týkající se jiných volatility příznaky ovládacích prvků:

- Ve funkcích, kde zdokumentovaných účel danou funkci stálé MxCsr příznaků.

- Pokud je prokazatelně správné, že porušení pravidla výsledky v programech, které se chová/znamená, že stejně jako program, ve kterém nejsou porušena tato pravidla, například prostřednictvím analýzy celého programu.

Žádné předpoklady nelze realizovat týkající se stavu volatile část MXCSR přes hranice funkce, pokud není výslovně uvedeno v dokumentaci funkce.

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)