---
title: '#define – direktiva (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: b72e2468b9e9984237c81f5cdb3c5691fe95cbd0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216275"
---
# <a name="define-directive-cc"></a>#define Direktiva (CC++/)

**#Define** vytvoří *makro*, které je přidružení identifikátoru nebo parametrizovaného identifikátoru s řetězcem tokenu. Po definování makra může kompilátor nahradit řetězec tokenu pro každý výskyt identifikátoru ve zdrojovém souboru.

## <a name="syntax"></a>Syntaxe

> **#define** *identifikátor* *token – řetězec* <sub>výslovný souhlas</sub>\
> **#define** *identifikátor* **(** <sub>souhlas</sub>**s** identifikátorem,... **,** *identifikátor* <sub>výslovný souhlas</sub> **)** *token –* <sub>vyjádření</sub> řetězce

## <a name="remarks"></a>Poznámky

Direktiva **#define** způsobí, že kompilátor nahradí *řetězec tokenu* pro každý výskyt *identifikátoru* ve zdrojovém souboru. *Identifikátor* je nahrazen pouze v případě, že tvoří token. To znamená, že *identifikátor* není nahrazen, pokud se zobrazí v komentáři, v řetězci nebo jako součást delšího identifikátoru. Další informace najdete v tématu [tokeny](../cpp/tokens-cpp.md).

Argument *token-String* se skládá z řady tokenů, jako jsou klíčová slova, konstanty nebo příkazy Complete. Jeden nebo více prázdných znaků musí oddělit *řetězec tokenu* od *identifikátoru*. Tento prázdný znak není považován za součást nahrazeného textu, ani není prázdným znakem, který následuje za posledním tokenem textu.

Bez token *-String* odebere výskyty identifikátoru ze zdrojového souboru. `#define` *Identifikátor* zůstává definován a lze jej testovat pomocí `#if defined` direktiv a. `#ifdef`

Druhá forma syntaxe definuje makro podobné funkci s parametry. Tento formulář přijme volitelný seznam parametrů, které musí být uvedeny v závorkách. Po definování makra se každým dalším výskytem *identifikátoru*(<sub>opt opt</sub>,...,<sub>opt opt</sub> ) nahradí verze argumentu *řetězce tokenu* , který má skutečné argumenty. nahradily se formálními parametry.

Formální názvy parametrů se zobrazí v *řetězci tokenu* k označení umístění, kde jsou nahrazeny skutečné hodnoty. Každý název parametru se může v *řetězci tokenu*objevit víckrát a názvy se můžou objevit v libovolném pořadí. Počet argumentů v volání musí odpovídat počtu parametrů v definici makra. Liberalizace použití závorek zaručuje správné interpretaci složitých skutečných argumentů.

Formální parametry v seznamu jsou odděleny čárkami. Každý název v seznamu musí být jedinečný a seznam musí být uzavřený v závorkách. Žádné mezery nesmí oddělovat *identifikátor* a levou závorku. Použijte zřetězení řádků – umístěte zpětné lomítko (`\`) těsně před znak nového řádku – pro dlouhé direktivy na více zdrojových řádcích. Rozsah formálního názvu parametru rozšiřuje na nový řádek, který ukončuje *řetězec tokenu*.

Pokud bylo makro definováno ve formuláři druhé syntaxe, následné textové instance následované seznamem argumentů označují volání makra. Skutečné argumenty, které následují po instanci *identifikátoru* ve zdrojovém souboru, odpovídají odpovídajícím formálním parametrům v definici makra. Každý formální parametr v *řetězci tokenu* , který není před operátorem převodu`#`(), charakterizace (`#@`) nebo token-vložení (`##`), nebo nenásledován `##` operátorem, je nahrazen odpovídajícím skutečný argument. Všechna makra ve skutečném argumentu jsou rozbalena před tím, než direktiva nahradí formální parametr. (Operátory jsou popsány v části [operátory preprocesoru](../preprocessor/preprocessor-operators.md).)

Následující příklady maker s argumenty ilustrují druhou formu syntaxe **#define** :

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

Argumenty s vedlejšími účinky někdy způsobují, že makra vytvářejí neočekávané výsledky. Daný formální parametr se může v *řetězci tokenu*objevit více než jednou. Pokud je tento formální parametr nahrazen výrazem s vedlejšími účinky, výraz s vedlejšími účinky může být vyhodnocen více než jednou. (Podívejte se na příklady v části [operátor vložení tokenu (# #)](../preprocessor/token-pasting-operator-hash-hash.md).)

`#undef` Direktiva způsobí zapomenutí Definice preprocesoru identifikátoru. Další informace najdete v [direktivě #undef](../preprocessor/hash-undef-directive-c-cpp.md) .

Pokud název definovaného makra nastane v *řetězci tokenu* (i v důsledku jiného rozšíření makra), není rozbalen.

Druhý **#define** pro makro se stejným názvem vygeneruje upozornění, pokud druhá sekvence tokenu není shodná s prvním.

**Specifické pro společnost Microsoft**

Pokud je nováC++ definice syntakticky shodná s původní definicí, můžete znovu definovat makro společnosti Microsoft C/s. Jinými slovy, dvě definice mohou mít různé názvy parametrů. Toto chování se liší od ANSI C, které vyžaduje, aby byly dvě definice lexikální.

Například následující dvě makra jsou shodná s výjimkou názvů parametrů. ANSI C nepovoluje taková předefinování, ale Microsoft C jeC++ zkompiluje bez chyby.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

Na druhé straně následující dvě makra nejsou totožná a vygenerují upozornění v Microsoft C/C++.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**Specifické pro konec Microsoftu**

Tento příklad ukazuje direktivu **#define** :

```C
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```

První příkaz definuje identifikátor `WIDTH` jako celočíselnou konstantu 80 a definuje `LENGTH` z hlediska `WIDTH` a celočíselnou konstantu 10. Každý výskyt `LENGTH` je nahrazen řetězcem (`WIDTH + 10`). V takovém případě `WIDTH + 10` je každý výskyt nahrazen výrazem (`80 + 10`). Závorky kolem `WIDTH + 10` jsou důležité, protože ovládají výklad v příkazech, jako jsou následující:

```C
var = LENGTH * 20;
```

Po fázi předzpracování se příkaz zobrazí jako:

```C
var = ( 80 + 10 ) * 20;
```

který se vyhodnotí jako 1800. Bez závorek je výsledkem:

```C
var = 80 + 10 * 20;
```

který se vyhodnotí jako 280.

**Specifické pro společnost Microsoft**

Definování maker a konstant pomocí možnosti [/d](../build/reference/d-preprocessor-definitions.md) Compiler má stejný účinek jako použití direktivy předběžného zpracování **#define** na začátku souboru. Pomocí možnosti/D lze definovat až 30 maker.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)
