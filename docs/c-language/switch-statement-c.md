---
title: switch– Příkaz (C)
ms.date: 04/25/2020
f1_keywords:
- switch
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- switch
- case
- default
- break
ms.openlocfilehash: 12163e85110092e3e372fa496cf42efd7574ea8d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167673"
---
# <a name="opno-locswitch-statement-c"></a>switch– Příkaz (C)

Příkazy **switch** a **case** slouží k řízení složitých operací podmíněného a větvení. **switch** Příkaz přenáší řízení do příkazu v rámci jeho těla.

## <a name="syntax"></a>Syntaxe

*příkaz výběru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`switch (`***expression* **`)`** *příkaz* výrazu

*příkaz s popiskem*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`case`**  *příkaz konstantního výrazu***`:`***statement*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`default :`**  *vydá*

Řízení se předá příkazu, **case** *konstantní výraz* odpovídá hodnotě ** switch (** *výraz* **)**. **switch** Příkaz může obsahovat libovolný počet **case** instancí. Nicméně žádné dvě case konstanty v rámci stejného **switch** příkazu nemohou mít stejnou hodnotu. Provádění těla příkazu začíná na vybraném příkazu. Pokračuje až do konce těla nebo do doby, než **break** příkaz přenese řízení z těla.

Použití **switch** příkazu obvykle vypadá nějak takto:

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

**break** Příkaz můžete použít k ukončení zpracování určitého popisku příkazu v rámci **switch** příkazu. Větví je na konec **switch** příkazu. Bez **break** příkazu, program pokračuje dalším příkazem s popiskem, spouští příkazy až do chvíle **break** , kdy je dosaženo konce příkazu. V některých situacích může být toto pokračování žádoucí.

Příkaz **default** je proveden, **case** Pokud není *konstantní výraz* roven hodnotě ** switch (** *výraz* **)**. Pokud není žádný **default** příkaz a nenajde se žádná **case** shoda, není proveden žádný příkaz v **switch** těle. Může existovat maximálně jeden **default** příkaz. **default** Příkaz nemusí být na konci. Může se objevit kdekoli v těle **switch** příkazu. Popisek **case** nebo **default** se může vyskytovat jenom uvnitř **switch** příkazu.

Typ **switch** *výrazu* a **case** *konstantní výraz* musí být integrální. Hodnota každého **case** *konstantního výrazu* musí být jedinečná v rámci těla příkazu.

Popisky **case** a **default** textu **switch** příkazu jsou významné pouze v počátečním testu, který určuje, kde se spustí spuštění v těle příkazu. **switch** příkazy mohou být vnořené. Všechny statické proměnné jsou inicializovány před provedením **switch** do libovolných příkazů.

> [!NOTE]
> Deklarace mohou být uvedeny na začátku složeného příkazu tvořícího **switch** tělo, ale inicializace obsažená v deklaracích se neprovádí. **switch** Příkaz přenáší řízení přímo do spustitelného příkazu v rámci těla a vynechá řádky, které obsahují inicializace.

Následující příklady ilustrují **switch** příkazy:

```C
switch( c )
{
    case 'A':
        capital_a++;
    case 'a':
        letter_a++;
    default :
        total++;
}
```

Všechny tři **switch** příkazy těla v tomto příkladu jsou spuštěny `c` `'A'`, pokud je rovno, protože žádný **break** příkaz není zobrazen před následujícím case. Ovládací prvek spuštění se přenese do prvního příkazu`capital_a++;`() a pokračuje v pořadí podle zbytku těla. Pokud `c` je rovno `'a'`, `letter_a` a `total` jsou zvýšeny. Je `total` zvýšena pouze v `c` případě, `'A'` že `'a'`není rovno nebo.

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

V tomto příkladu **break** příkaz sleduje jednotlivé příkazy **switch** těla. **break** Příkaz vynutí ukončení od těla příkazu po provedení jednoho příkazu. Pokud `i` je rovno-1, je `n` pouze zvýšena. **break** Následující příkaz `n++;` způsobí, že řízení provádění vychází z těla příkazu a vynechává zbývající příkazy. Podobně, pokud `i` je rovno 0, je `z` pouze zvýšena hodnota; Pokud `i` je rovno 1, pouze `p` se zvýší. Poslední **break** příkaz není nezbytně nutný, protože ovládací prvek předá tělo na konci složeného příkazu. Zahrnuje konzistenci.

Jeden příkaz může obsahovat více **case** popisků, jak ukazuje následující příklad:

```C
switch( c )
{
    case 'a' :
    case 'b' :
    case 'c' :
    case 'd' :
    case 'e' :
    case 'f' :  convert_hex(c);
}
```

V tomto příkladu, pokud *konstantní výraz* se rovná jakémukoliv písmenu mezi `'a'` a `'f'`, je `convert_hex` funkce volána.

### <a name="microsoft-specific"></a>specifické pro společnost Microsoft

Microsoft C neomezuje počet case hodnot v **switch** příkazu. Počet je omezen pouze dostupnou pamětí. ANSI C vyžaduje, aby v case **switch** příkazu bylo povolené aspoň 257 popisků.

V default případě Microsoft C je povolena rozšíření společnosti Microsoft. Tato rozšíření zakažte pomocí možnosti kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="see-also"></a>Viz také

[switchPříkaz (C++)](../cpp/switch-statement-cpp.md)
