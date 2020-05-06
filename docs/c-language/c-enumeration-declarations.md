---
title: Deklarace výčtů v jazyce C
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
ms.openlocfilehash: bc238dd0088558233d84f8bbd15d06743e133449
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326011"
---
# <a name="c-enumeration-declarations"></a>Deklarace výčtů v jazyce C

Výčet se skládá ze sady pojmenovaných celočíselných konstant. Deklarace výčtového typu poskytuje název (volitelné) značky výčtu a definuje sadu pojmenovaných celočíselných identifikátorů (označované jako "množina výčtu", "konstanty enumerátoru", enumerátory "nebo" Členové "). Proměnná s typem výčtu ukládá jednu z hodnot sady výčtu definované tímto typem.

Proměnné `enum` typu lze použít ve výrazech indexování a jako operandy všech aritmetických a relačních operátorů. Výčty poskytují alternativu ke `#define` direktivě preprocesoru s výhodami, které lze vygenerovat pro vás a dodržují normální pravidla určování rozsahu.

Ve standardu ANSI C jsou výrazy definující hodnotu konstanty enumerátoru vždy `int` typu; Proto úložiště přidružené k proměnné výčtu je úložiště vyžadované pro jednu `int` hodnotu. Konstanta výčtu nebo hodnota výčtového typu může být použita kdekoli jazyk C, který povoluje celočíselný výraz.

## <a name="syntax"></a>Syntaxe

*specifikátor výčtu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<sub>výslovný souhlas</sub> s *identifikátorem* **výčtu** **{** *Enumerator-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *identifikátor* výčtu

Nepovinný *identifikátor* název typ výčtu definovaný *seznamem výčtu*. Tento identifikátor se často označuje jako "tag" výčtu určeného seznamem. Specifikátor typu formuláře

```
enum identifier
{
    enumerator-list
}
```

deklaruje *identifikátor* , který bude značka výčtu určeného neterminálovým *seznamem výčtu* . *Seznam enumerátor-list* definuje "obsah enumerátoru". *Seznam enumerátor-list* je podrobněji popsán níže.

Pokud je deklarace značky viditelná, následné deklarace, které používají značku, ale vynechat *seznam výčtu* , určují dříve deklarovaný typ výčtu. Značka musí odkazovat na definovaný typ výčtu a tento typ výčtu musí být v aktuálním oboru. Vzhledem k tomu, že je typ výčtu definován jinde, *seznam výčtu* se v této deklaraci nezobrazí. Deklarace typů odvozených z výčtů a `typedef` deklarací pro výčtové typy mohou používat značku výčtu před definováním typu výčtu.

## <a name="syntax"></a>Syntaxe

*seznam enumerátorů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*čítače*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerátor – seznam* **,** *enumerátor*

*enumerátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výčet – konstanta*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumeration –* **=** konstantní *výraz*

*konstanta výčtu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*

Každá *konstanta Enumeration* v *seznamu výčtu* vyjmenovává hodnotu sady výčtu. Ve výchozím nastavení je první *konstanta výčtu* přidružena k hodnotě 0. Další *konstanta výčtu* v seznamu je přidružena k hodnotě ( *konstantní výraz* + 1), pokud ji explicitně nepřidružíte k jiné hodnotě. Název *konstanty Enumeration* je ekvivalentní hodnotě.

Výchozí sekvenci hodnot můžete přepsat pomocí *výrazu Enumeration-Constant = constant-expression* . Proto pokud se v *seznamu enumerátorů*objeví *výčet-konstanta = konstantní-výraz* , je *konstanta výčtu* přidružena k hodnotě zadané *konstantním výrazem*. *Konstantní výraz* musí mít `int` typ a může být záporný.

Následující pravidla platí pro členy sady výčtu:

- Sada výčtu může obsahovat duplicitní konstantní hodnoty. Například můžete přidružit hodnotu 0 ke dvěma různým identifikátorům, které jsou pravděpodobně pojmenované `null` a `zero`, ve stejné sadě.

- Identifikátory v seznamu výčtu musí být odlišné od jiných identifikátorů ve stejném oboru se stejnou viditelností, včetně běžných názvů proměnných a identifikátorů v jiných výčtových seznamech.

- Značky výčtu dodržují normální pravidla oboru. Musí se lišit od jiných značek výčtu, struktury a sjednocení se stejnou viditelností.

## <a name="examples"></a>Příklady

Tyto příklady ilustrují deklarace výčtu:

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

Hodnota 0 je `saturday` ve výchozím nastavení přidružena. Identifikátor `sunday` je explicitně nastaven na hodnotu 0. Zbývajícím identifikátorem jsou ve výchozím nastavení zadány hodnoty od 1 do 5.

V tomto příkladu je hodnota ze sady `DAY` přiřazena proměnné. `today`

```
enum DAY today = wednesday;
```

Všimněte si, že název konstanty výčtu slouží k přiřazení hodnoty. Vzhledem k `DAY` tomu, že byl již dříve deklarován typ výčtu, `DAY` je nutné zadat pouze značku výčtu.

Chcete-li explicitně přiřadit celočíselnou hodnotu proměnné výčtového typu dat, použijte přetypování typu:

```
workday = ( enum DAY ) ( day_value - 1 );
```

Toto přetypování je doporučeno v jazyce C, ale není vyžadováno.

```
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */
{
    false,     /* false = 0, true = 1 */
    true
};

enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */
```

Tato deklarace se dá taky zadat jako

```
enum BOOLEAN { false, true } end_flag, match_flag;\
```

nebo jako

```
enum BOOLEAN { false, true } end_flag;
enum BOOLEAN match_flag;
```

Příklad, který používá tyto proměnné, může vypadat takto:

```
if ( match_flag == false )
    {
     .
     .   /* statement */
     .
    }
    end_flag = true;
```

Lze také deklarovat nepojmenované datové typy enumerátoru. Název datového typu je vynechán, ale proměnné lze deklarovat. Proměnná `response` je proměnná typu, který je definován:

```
enum { yes, no } response;
```

## <a name="see-also"></a>Viz také

[Výčty](../cpp/enumerations-cpp.md)
