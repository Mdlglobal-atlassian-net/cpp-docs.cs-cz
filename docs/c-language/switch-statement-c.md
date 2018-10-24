---
title: Přepnout Statement (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- switch
dev_langs:
- C++
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ac5fb523e1b1340d031cd5256995568b9b9e2a2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034119"
---
# <a name="switch-statement-c"></a>switch – příkaz (C)

`switch` a **případ** příkazy nápovědy komplexní větvení a podmíněného operace u ovládacího prvku. `switch` Příkaz přenese ovládací prvek v rámci svého těla příkazu.

## <a name="syntax"></a>Syntaxe

*příkaz výběru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Přepnout (** *výraz* **)** *– příkaz*

*příkaz s popiskem*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**případ**  *konstantní výraz*  **:**  *– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Výchozí:**  *– příkaz*

Ovládací prvek se předá příkazu jehož **případ** *konstantní výraz* odpovídá hodnotě **přepnout (** *výraz* **)**. `switch` Výraz může obsahovat libovolný počet **případ** instancí, ale žádné dvě konstanty velikosti písmen v rámci stejného `switch` může obsahovat stejnou hodnotu. Spuštění těla příkazu začíná u příkazu, vybrané a pokračuje až do konce subjektu, nebo dokud **přerušení** příkaz předává řízení mimo tělo.

Použití `switch` příkaz obvykle vypadá nějak takto:

```C
switch ( expression )
{
    // declarations
    // . . .
    case constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        break;
    default:
        // statements executed if expression does not equal
        // any case constant_expression
}
```

Můžete použít **přerušení** příkaz k ukončení zpracování konkrétního případu v `switch` příkazu a do větve na konec objektu `switch` příkazu. Bez **přerušení**, program bude pokračovat na další případ provádění příkazů, dokud **přerušení** nebo je dosažen konec příkazu. V některých případech může být žádoucí tento pokračování.

**Výchozí** Pokud ne, je proveden příkaz **případ** *konstantní výraz* rovná hodnotě **přepnout (**  *výraz* **)**. Pokud **výchozí** příkazu je vynechán a ne **případ** shoda nenajde, žádný z příkazů v `switch` provádějí textu. Může existovat maximálně jeden **výchozí** příkazu. **Výchozí** příkaz se nemusí nacházet na konci; může vyskytovat kdekoli v těle `switch` příkazu. A **případ** nebo **výchozí** popisek může být použito pouze uvnitř `switch` příkazu.

Typ `switch` *výraz* a **případ** *konstantní výraz* musí být integrálního typu. Hodnota každého **případ** *konstantní výraz* musí být jedinečný v rámci těla příkazu.

**Případ** a **výchozí** popisky `switch` tělo s příkazy významných je pouze v počátečním testu, která určuje, kde spuštění do těla příkazu. Mohou být vnořené příkazy přepínače. Všechny statické proměnné jsou inicializovány před provedením do libovolného `switch` příkazy.

> [!NOTE]
> Deklarace mohou objevit v čele složený příkaz tvořící `switch` textu, ale inicializace součástí deklarace se neprovádí. `switch` Příkaz předá řízení přímo v těle obcházení řádky, které obsahují inicializace byl spustitelný příkaz.

Následující příklady znázorňují `switch` příkazy:

```C
switch( c )
{
    case 'A':
        capa++;
    case 'a':
        lettera++;
    default :
        total++;
}
```

Všechny tři příkazy nástroje `switch` textu v tomto příkladu jsou spouštěny, pokud `c` rovná `'A'` od **přerušení** před následující případ se nezobrazí příkaz. Spuštění ovládací prvek bude převeden na prvním příkazem (`capa++;`) a bude pokračovat v pořadí, postupujte podle zbývajících kroků textu. Pokud `c` rovná `'a'`, `lettera` a `total` jsou zvětšeny. Pouze `total` se zvýší, pokud `c` není roven `'A'` nebo `'a'`.

```C
switch( i )
{
    case -1:
        n++;
        break;
    case 0 :
        z++;
        break;
    case 1 :
        p++;
        break;
}
```

V tomto příkladu **přerušení** příkaz následuje každý příkaz `switch` textu. **Přerušení** příkaz vynutí východ z těla příkazu po provedení jednoho příkazu. Pokud `i` je roven -1, pouze `n` se zvýší. **Přerušení** příkazem `n++;` způsobí, že řízení provádění předat mimo tělo příkazu, vynechání zbývající příkazy. Podobně pokud `i` se rovná 0, pouze `z` se zvýší; Pokud `i` je rovno 1 pouze `p` se zvýší. Finální **přerušení** příkaz není nezbytně nutné, protože řízení se předá z textu na konci složeného příkazu, ale je součástí pro zajištění konzistence.

Jeden příkaz může obsahovat více **případ** popisky, jako v následujícím příkladu:

```C
case 'a' :
case 'b' :
case 'c' :
case 'd' :
case 'e' :
case 'f' :  hexcvt(c);
```

V tomto příkladu Pokud *konstantní výraz* rovná žádné písmeno mezi `'a'` a `'f'`, `hexcvt` funkce je volána.

**Specifické pro Microsoft**

Microsoft C neomezuje počet případových hodnoty v `switch` příkazu. Počet je omezen pouze dostupnou paměť. ANSI C vyžaduje alespoň 257 povolených popisků případu v `switch` příkazu.

Výchozí nastavení pro Microsoft C je, že jsou povolena rozšíření společnosti Microsoft. Pomocí možnosti kompilátoru /Za pro zákaz těchto rozšíření.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[switch – příkaz (C++)](../cpp/switch-statement-cpp.md)