---
title: Deklarace výčtů v jazyce C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 858f7bf440b0a53a7e9ed5bb666029b7d1135f81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091891"
---
# <a name="c-enumeration-declarations"></a>Deklarace výčtů v jazyce C

Výčet se skládá sada pojmenovaných celočíselných konstant. Typ deklarace výčtu obsahuje název značky (volitelné) výčet a definuje sadu pojmenovaných celočíselných identifikátory (nazývá "výčet sada," "konstanty enumerátoru," "enumerátory" nebo "členy"). Proměnnou s typem výčtu ukládá jedna z hodnot výčtu množiny definované podle tohoto typu.

Proměnné `enum` typ lze použít ve výrazech indexování a jako operandy všechny aritmetické a relační operátory. Výčty jako alternativu k `#define` direktivy preprocesoru, že hodnoty mohou být generovány pro vás a dodržují normální pravidel stanovení rozsahu inicializací výhody.

Ve standardu ANSI C, výrazy, které definují hodnoty pro konstantu enumerátoru vždy mít `int` typ; proto je úložiště spojené s proměnnou výčet úložiště potřebné pro jeden `int` hodnotu. Konstanta výčtu nebo hodnotu Výčtový typ lze použít kdekoli jazyka C umožňuje se celočíselný výraz.

## <a name="syntax"></a>Syntaxe

*specifikátoru výčtu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**výčet** *identifikátor*<sub>optimalizované</sub> **{** *enumerátor seznam* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**výčet** *identifikátor*

Volitelný *identifikátor* názvy typu výčtu definované v *enumerátor seznam*. Tento identifikátor se často nazývá "značka" výčet určeno v seznamu. Specifikátor typu formuláře

```
enum identifier
{
    enumerator-list
}
```

deklaruje *identifikátor* být značka výčet určené *enumerátor seznam* neterminálu. *Enumerátor seznam* definuje "obsah enumerátoru." *Enumerátor seznam* je podrobně popsaná níže.

Pokud deklarace značky je viditelné, následující deklarace využívající značky, ale vynechejte *enumerátor seznam* zadejte dříve deklarovaný výčtového typu. Značka musí odkazovat na typ výčtu definované a typu výčtu musí být v aktuálním oboru. Protože typ výčtu je definována jinde, *enumerátor seznam* zřejmě není v této deklaraci. Deklarace typů odvozených z výčtů a `typedef` deklarace pro výčtové typy lze použít výčet značku, než je definován typ výčtu.

## <a name="syntax"></a>Syntaxe

*Enumerátor seznam*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumerátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumerátor seznam* **,** *enumerátoru*

*enumerátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanta výčtu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanta výčtu* **=** *konstantního výrazu.*

*Konstanta výčtu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*

Každý *konstanta výčtu* v *seznam výčtu* názvy hodnotu výčtu sady. Ve výchozím nastavení první *konstanta výčtu* souvisí s hodnotou 0. Další *konstanta výčtu* v seznamu je přiřazena hodnota ( *konstantní výraz* + 1), pokud ji explicitně spojit s jinou hodnotou. Název *konstanta výčtu* je ekvivalentní k jeho hodnotu.

Můžete použít *konstanta výčtu = konstantní výraz* přepsat výchozí pořadí hodnot. Proto pokud *konstanta výčtu = konstantní výraz* se zobrazí v *enumerátor seznam*, *konstanta výčtu* souvisí s hodnotou Dal *konstantní výraz*. *Konstantní výraz* musí mít `int` typu a mohou být záporná.

Na členy sady výčet platí následující pravidla:

- Skupinu výčet může obsahovat duplicitní hodnoty konstant. Je třeba přidružit hodnota 0 se dva různé identifikátory, třeba s názvem `null` a `zero`, ve stejné sadě.

- Identifikátory v seznam výčtu musí být odlišný od jiné identifikátory ve stejném oboru se stejnou viditelností, včetně běžné názvy proměnných a identifikátory v seznamech výčtu.

- Výčtové tagy dodržují běžných pravidel oboru. Musí být odlišné od jiných výčet, struktury a sjednocení značky se stejnou viditelností.

## <a name="examples"></a>Příklady

Tyto příklady ilustrují deklarace výčtů:

```
enum DAY            /* Defines an enumeration type    */
{
    saturday,       /* Names day and declares a       */
    sunday = 0,     /* variable named workday with    */
    monday,         /* that type                      */
    tuesday,
    wednesday,      /* wednesday is associated with 3 */
    thursday,
    friday
} workday;
```

Hodnota 0 je spojená s `saturday` ve výchozím nastavení. Identifikátor `sunday` je explicitně nastaveno na hodnotu 0. Zbývajících identifikátorů jsou uvedeny hodnoty 1 až 5 ve výchozím nastavení.

V tomto příkladu hodnota ze sady `DAY` je přiřazená k proměnné `today`.

```
enum DAY today = wednesday;
```

Všimněte si, že název konstanta výčtu slouží k přiřazení hodnoty. Protože `DAY` typ výčtu se dřív deklaroval, pouze značky výčet `DAY` je nezbytné.

Pokud chcete explicitně přiřadit celočíselnou hodnotu proměnné výčtový datový typ, použijte přetypování typu:

```
workday = ( enum DAY ) ( day_value - 1 );
```

Toto přetypování se doporučuje v jazyce C, ale není potřeba.

```
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */
{
    false,     /* false = 0, true = 1 */
    true
};

enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */
```

Toto prohlášení je taky možné specifikovat jako

```
enum BOOLEAN { false, true } end_flag, match_flag;\
```

nebo jako

```
enum BOOLEAN { false, true } end_flag;
enum BOOLEAN match_flag;
```

Příklad, který používá tyto proměnné může vypadat takto:

```
if ( match_flag == false )
    {
     .
     .   /* statement */
     .
    }
    end_flag = true;
```

Lze také deklarovat nepojmenované výčet datových typů. Název datového typu, je tento parametr vynechán, ale můžete deklarovat proměnné. Proměnná `response` je proměnná typu definovaného:

```
enum { yes, no } response;
```

## <a name="see-also"></a>Viz také

[Výčty](../cpp/enumerations-cpp.md)