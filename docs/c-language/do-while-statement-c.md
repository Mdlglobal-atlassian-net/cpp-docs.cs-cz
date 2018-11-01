---
title: do-while – příkaz (C)
ms.date: 11/04/2016
f1_keywords:
- do
- while
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
ms.openlocfilehash: f2548ec60c7ee36d46d385cd7e7dda7bcfc2758d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462904"
---
# <a name="do-while-statement-c"></a>do-while – příkaz (C)

*Proveďte – zatímco* příkaz umožňuje opakujte příkaz nebo složený příkaz, dokud nebude NEPRAVDA zadaným výrazem.

## <a name="syntax"></a>Syntaxe

*příkaz iterace*: &nbsp; &nbsp; &nbsp; &nbsp; **proveďte**  *příkaz*  **během (** *výraz*  **);**

*Výraz* v *proveďte – zatímco* vyhodnotí po provedení tělo smyčky. Tělo smyčky, proto je vždy alespoň jednou spuštěn.

*Výraz* musí mít aritmetický typ nebo typ ukazatele. Spuštění probíhá následujícím způsobem:

1. Provede se tělo příkazu.

1. Dále *výraz* vyhodnocena. Pokud *výraz* má hodnotu false, *proveďte-při* příkaz skončí a předá řízení dalšímu příkazu v programu. Pokud *výraz* má hodnotu true (nenulový), proces se opakuje, počínaje krokem 1.

*Proveďte-při* příkaz může také skončit při **přerušení**, **goto**, nebo **vrátit** je proveden příkaz v rámci těla příkazu.

Toto je příklad *proveďte – zatímco* – příkaz:

```C
do
{
    y = f( x );
    x--;
} while ( x > 0 );
```

V tomto *proveďte – zatímco* prohlášení, dva příkazy `y = f( x );` a `x--;` jsou spouštěny, bez ohledu na počáteční hodnotu `x`. Potom `x > 0` vyhodnocena. Pokud `x` je větší než 0, je tělo příkazu spustit znovu a `x > 0` je již znovu. Tělo příkazu je proveden opakovaně tak dlouho, dokud `x` zůstane větší než 0. Provádění *proveďte – zatímco* příkaz skončí, když `x` stane 0 nebo záporná. Tělo smyčky je provedena alespoň jednou.

## <a name="see-also"></a>Viz také

[do-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)
