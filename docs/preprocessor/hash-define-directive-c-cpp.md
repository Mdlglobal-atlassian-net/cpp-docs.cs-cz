---
title: '##define – direktiva (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: 8a0cc7e7836a0c82c72055fe8d9e7497995485d0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039495"
---
# <a name="define-directive-cc"></a>#define – direktiva (C++)

**#Define** vytvoří *– makro*, což je seskupení identifikátoru nebo identifikátoru parametrizované s řetězec tokenu. Po definování makra může kompilátor nahradit řetězec tokenu pro každý výskyt identifikátoru ve zdrojovém souboru.

## <a name="syntax"></a>Syntaxe

`#define` *identifikátor* *řetězci tokenu*<sub>optimalizované</sub>

`#define` *identifikátor* `(` *identifikátor*<sub>optimalizované</sub> `,` *...*  `,` *identifikátor*<sub>optimalizované</sub> `)` *řetězci tokenu*<sub>optimalizované</sub>

## <a name="remarks"></a>Poznámky

**#Define** – direktiva způsobí, že kompilátor nahradí *řetězci tokenu* pro každý výskyt *identifikátor* ve zdrojovém souboru. *Identifikátor* nahrazuje pouze v případě, že tvoří token. To znamená *identifikátor* nebude nahrazen, pokud se zobrazí v komentáři, v řetězci, nebo jako součást delšího identifikátoru. Další informace najdete v tématu [tokeny](../cpp/tokens-cpp.md).

*Řetězci tokenu* argument se skládá z řady tokenů, jako jsou klíčová slova, konstanty nebo úplná prohlášení. Jeden nebo více prázdných znaků musí oddělovat *řetězci tokenu* z *identifikátor*. Toto prázdné místo není považováno za součást nahrazeného textu, ani není libovolným prázdný znakem, který následuje za posledním tokenem textu.

A `#define` bez *řetězci tokenu* odebere výskyty *identifikátor* ze zdrojového souboru. *Identifikátor* zůstane definován a může být testován pomocí `#if defined` a `#ifdef` direktivy.

Druhá forma syntaxe definuje funkci podobnou makru s parametry. Tento tvar přijímá volitelný seznam parametrů, které musí být uvedena v závorkách. Poté, co je makro definované, každý další výskyt *identifikátor*( *identifikátor*<sub>optimalizované</sub>,..., *identifikátor* <sub>optimalizované</sub> ) je nahrazena verzi *řetězci tokenu* argument, který má skutečné argumenty nahrazené za formální parametry.

Názvy formálních parametrů se zobrazí v *řetězci tokenu* k označení míst, kde jsou nahrazeny skutečnými hodnotami. Každý název parametru se může objevit více než jednou v *řetězci tokenu*, a názvy se mohou objevit v libovolném pořadí. Počet argumentů ve volání musí odpovídat počtu parametrů v definici makra. Liberální použití závorek zaručuje správnou interpretaci složitých skutečných argumentů.

Formální parametry v seznamu jsou odděleny čárkami. Každý název v seznamu musí být jedinečný a seznam musí být uzavřen v závorkách. Žádné mezery *identifikátor* a levou závorku. Pomocí řetězení řádků – umístěte zpětné lomítko (`\`) bezprostředně před znak – pro dlouhé direktivy na několika zdrojových řádcích. Rozsah formálních parametrů názvu rozšiřuje na nový řádek, který končí *řetězci tokenu*.

Když se makro bylo definováno ve druhé formě syntaxe, následné textové instance následované seznamem argumentů značí volání makra. Skutečné argumenty, které následují po instanci *identifikátor* ve zdrojovém souboru budou odpovídat odpovídajícím formálním parametrům v definici makra. Každý formální parametr v *řetězci tokenu* , který není předcházen nastavení velikosti řetězce (`#`), zřetězení (`#@`), nebo vložení tokenu (`##`) operátor, nebo není následován `##` je operátor nahrazen příslušným skutečným argumentem. Jakékoli makro ve skutečném argumentu je rozbaleno dříve, než direktiva nahradí formální parametr. (Operátory jsou popsány v [operátory preprocesoru](../preprocessor/preprocessor-operators.md).)

Následující příklady maker s argumenty ilustrují druhou formu **#define** syntaxi:

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

Argumenty s vedlejšími účinky občas způsobují neočekávané výsledky maker. Daný formální parametr se může zobrazit více než jednou v *řetězci tokenu*. Pokud výraz s vedlejšími účinky nahrazuje tento formální parametr, může být výraz s vedlejšími účinky, vyhodnocen více než jednou. (Podívejte se na příklady v části [operátor vložení tokenu (##)](../preprocessor/token-pasting-operator-hash-hash.md).)

`#undef` – Direktiva způsobí, že definice preprocesoru identifikátoru budou vymazány. Zobrazit [direktiva #undef](../preprocessor/hash-undef-directive-c-cpp.md) Další informace.

Pokud dojde k název makra definovaného v *řetězci tokenu* (i v důsledku jiného rozšiřujícího makra), nerozbalí.

Sekundy **#define** pro makro se stejným názvem vygeneruje upozornění, pokud není druhá sekvence tokenů shodná s první.

**Microsoft Specific**

Microsoft C/C++ umožňuje znovu definovat makro, pokud je nová definice syntakticky shodná s původní definice. Jinými slovy dvě definice mohou mít různé názvy parametrů. Toto chování se liší od standardu ANSI C, který vyžaduje, aby dvě definice byly lexikálně identické.

Například následující dvě makra jsou shodná s výjimkou názvů parametrů. ANSI C nepovoluje tuto nová definice, ale Microsoft C/C++ jej zkompiluje bez chyb.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

Na druhé straně následující dvě makra nejsou stejné a vygeneruje upozornění v jazyce Microsoft C/C++.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**Specifické pro END Microsoft**

Tento příklad ukazuje, **#define** – direktiva:

```C
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```

První příkaz určuje identifikátor `WIDTH` jako celočíselnou konstantu 80 a definuje `LENGTH` z hlediska `WIDTH` a celočíselnou konstantou 10. Každý výskyt `LENGTH` nahrazuje (`WIDTH + 10`). Následně bude každý výskyt `WIDTH + 10` je nahrazen výrazem (`80 + 10`). Závorky kolem `WIDTH + 10` jsou důležité, protože řídí výklad ve vyjádřeních, jako jsou následující:

```C
var = LENGTH * 20;
```

Po fázi předzpracování se příkazu stane:

```C
var = ( 80 + 10 ) * 20;
```

který se hodnotí jako 1800. Bez závorek je výsledek:

```C
var = 80 + 10 * 20;
```

které vyhodnocuje 280.

**Microsoft Specific**

Definování maker a konstant pomocí [/D](../build/reference/d-preprocessor-definitions.md) – možnost kompilátoru má stejný účinek jako použití **#define** direktiva předzpracování na začátku souboru. Pomocí možnosti /D lze definovat až 30 maker.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)