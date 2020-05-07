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
ms.openlocfilehash: eb18b6244318b595e67cc45f99dfcde314866f55
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825675"
---
# <a name="switch-statement-c"></a>`switch`– Příkaz (C)

Příkazy __`switch`__ a __`case`__ slouží k řízení složitých operací podmíněného a větvení. __`switch`__ Příkaz přenáší řízení do příkazu v rámci jeho těla.

## <a name="syntax"></a>Syntaxe

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`switch (`__&nbsp;*`expression`* &nbsp;__`)`__&nbsp;*`statement`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>Poznámky

__`switch`__ Příkaz způsobí, že se ovládací prvek převede *`labeled-statement`* na jeden v těle jeho příkazu v závislosti na hodnotě *`expression`*.

Hodnoty *`expression`* a Each *`constant-expression`* musí mít celočíselný typ. *`constant-expression`* Musí mít v době kompilace nejednoznačnou konstantní celočíselnou hodnotu.

Řízení se předá **`case`** příkazu, *`constant-expression`* jehož hodnota odpovídá hodnotě *`expression`*. __`switch`__ Příkaz může obsahovat libovolný počet __`case`__ instancí. Avšak žádné dvě *`constant-expression`* hodnoty v rámci stejného __`switch`__ příkazu nemohou mít stejnou hodnotu. Provádění těla __`switch`__ příkazu začíná prvním příkazem v nebo po shodě *`labeled-statement`*. Spuštění pokračuje až do konce těla nebo do doby, než __`break`__ příkaz přenese řízení mimo tělo.

Použití __`switch`__ příkazu obvykle vypadá nějak takto:

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

__`break`__ Příkaz můžete použít k ukončení zpracování určitého popisku příkazu v rámci __`switch`__ příkazu. Větví je na konec __`switch`__ příkazu. Bez __`break`__ příkazu, program pokračuje dalším příkazem s popiskem, spouští příkazy až do chvíle __`break`__ , kdy je dosaženo konce příkazu. V některých situacích může být toto pokračování žádoucí.

Příkaz __`default`__ je proveden, pokud není __`case`__ *`constant-expression`* žádná hodnota rovna hodnotě *`expression`*. Pokud není žádný __`default`__ příkaz a nenajde se žádná __`case`__ shoda, není proveden žádný příkaz v __`switch`__ těle. Může existovat maximálně jeden __`default`__ příkaz. __`default`__ Příkaz nemusí být na konci. Může se objevit kdekoli v těle __`switch`__ příkazu. Popisek __`case`__ nebo __`default`__ se může vyskytovat jenom uvnitř __`switch`__ příkazu.

Typ __`switch`__ *`expression`* __`case`__ a *`constant-expression`* musí být integrální. Hodnota každého __`case`__ *`constant-expression`* musí být jedinečná v rámci těla příkazu.

Popisky __`case`__ a __`default`__ textu __`switch`__ příkazu jsou významné pouze v počátečním testu, který určuje, kde se spustí spuštění v těle příkazu. __`switch`__ příkazy mohou být vnořené. Všechny statické proměnné jsou inicializovány před provedením __`switch`__ do libovolných příkazů.

> [!NOTE]
> Deklarace mohou být uvedeny na začátku složeného příkazu tvořícího __`switch`__ tělo, ale inicializace obsažená v deklaracích se neprovádí. __`switch`__ Příkaz přenáší řízení přímo do spustitelného příkazu v rámci těla a vynechá řádky, které obsahují inicializace.

Následující příklady ilustrují __`switch`__ příkazy:

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

Všechny tři __`switch`__ příkazy těla v tomto příkladu jsou spuštěny `c` `'A'`, pokud je rovno, protože žádný __`break`__ příkaz není zobrazen před následujícím __`case`__. Ovládací prvek spuštění se přenese do prvního příkazu`capital_a++;`() a pokračuje v pořadí podle zbytku těla. Pokud `c` je rovno `'a'`, `letter_a` a `total` jsou zvýšeny. Je `total` zvýšena pouze v `c` případě, `'A'` že `'a'`není rovno nebo.

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

V tomto příkladu __`break`__ příkaz sleduje jednotlivé příkazy __`switch`__ těla. __`break`__ Příkaz vynutí ukončení od těla příkazu po provedení jednoho příkazu. Pokud `i` je rovno-1, je `n` pouze zvýšena. __`break`__ Následující příkaz `n++;` způsobí, že řízení provádění vychází z těla příkazu a vynechává zbývající příkazy. Podobně, pokud `i` je rovno 0, je `z` pouze zvýšena hodnota; Pokud `i` je rovno 1, pouze `p` se zvýší. Poslední __`break`__ příkaz není nezbytně nutný, protože ovládací prvek předá tělo na konci složeného příkazu. Zahrnuje konzistenci.

Jeden příkaz může obsahovat více __`case`__ popisků, jak ukazuje následující příklad:

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

Microsoft C neomezuje počet __`case`__ hodnot v __`switch`__ příkazu. Počet je omezen pouze dostupnou pamětí. ANSI C vyžaduje, aby v __`case`__ __`switch`__ příkazu bylo povolené aspoň 257 popisků.

V default případě Microsoft C je povolena rozšíření společnosti Microsoft. Tato rozšíření zakažte pomocí možnosti kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="see-also"></a>Viz také

[switchPříkaz (C++)](../cpp/switch-statement-cpp.md)
