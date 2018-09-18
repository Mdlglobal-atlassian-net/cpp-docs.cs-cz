---
title: Proveďte-while Statement (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- do
- while
dev_langs:
- C++
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef670aca60b2e3156ea70480a1dafc315ae60624
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061471"
---
# <a name="do-while-statement-c"></a>do-while – příkaz (C)

*Proveďte – zatímco* příkaz umožňuje opakujte příkaz nebo složený příkaz, dokud nebude NEPRAVDA zadaným výrazem.

## <a name="syntax"></a>Syntaxe

*příkaz iterace*: &nbsp; &nbsp; &nbsp; &nbsp; **proveďte***příkaz***během (** *výraz***);** 

*Výraz* v *proveďte – zatímco* vyhodnotí po provedení tělo smyčky. Tělo smyčky, proto je vždy alespoň jednou spuštěn.

*Výraz* musí mít aritmetický typ nebo typ ukazatele. Spuštění probíhá následujícím způsobem:

1. Provede se tělo příkazu.

2. Dále *výraz* vyhodnocena. Pokud *výraz* má hodnotu false, *proveďte-při* příkaz skončí a předá řízení dalšímu příkazu v programu. Pokud *výraz* má hodnotu true (nenulový), proces se opakuje, počínaje krokem 1.

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