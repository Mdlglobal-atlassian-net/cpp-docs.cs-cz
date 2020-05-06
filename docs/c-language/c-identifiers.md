---
title: Identifikátory jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
ms.openlocfilehash: 1f3abf304e6fda52e2571d0bccb8d4db5a414dfe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325660"
---
# <a name="c-identifiers"></a>Identifikátory jazyka C

"Identifikátory" nebo "symboly" jsou názvy, které zadáváte pro proměnné, typy, funkce a popisky v programu. Názvy identifikátorů se musí lišit v pravopisu a v případě libovolných klíčových slov. Jako identifikátory nemůžete použít klíčová slova (buď C nebo Microsoft). jsou vyhrazené pro speciální použití. Identifikátor vytvoříte zadáním v deklaraci proměnné, typu nebo funkce. V tomto příkladu `result` je identifikátor celočíselné proměnné a `main` a `printf` jsou názvy identifikátorů pro funkce.

```
#include <stdio.h>

int main()
{
    int result;

    if ( result != 0 )
        printf_s( "Bad file handle\n" );
}
```

Po deklarování můžete použít identifikátor v pozdějších příkazech programu pro odkazování na přidruženou hodnotu.

V `goto` příkazech lze použít speciální druh identifikátoru označovaného jako popisek příkazu. (Deklarace jsou popsány v tématu [deklarace a příkazy typů](../c-language/declarations-and-types.md) jsou popsány v [příkazech goto a labeled](../c-language/goto-and-labeled-statements-c.md).)

## <a name="syntax"></a>Syntaxe

*identifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nenumerickému*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *nečíselný* identifikátor<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*číslice* *identifikátoru*

*nečíselný*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ a b c d e f g h i j k l MN o p q r s t u w x y z**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F G H I J K L MN O P Q R S T H U W X Y Z**

*číslice*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

První znak názvu identifikátoru musí být `nondigit` (to znamená, že první znak musí být podtržítko nebo velké písmeno nebo malé písmeno). ANSI umožňuje v názvu externího identifikátoru šest významných znaků a 31 pro názvy vnitřních (v rámci funkce) identifikátorů. Externí identifikátory (ty deklarované v globálním oboru nebo deklarované s třídou `extern`úložiště) mohou podléhat dalším omezením pojmenovávání, protože tyto identifikátory musí být zpracovány jiným softwarem, jako jsou například odkazy.

**Specifické pro Microsoft**

I když ANSI umožňuje 6 významných znaků v názvech externích identifikátorů a 31 pro názvy vnitřních (v rámci funkce) identifikátorů, kompilátor jazyka Microsoft C umožňuje 247 znaků v názvu interního nebo externího identifikátoru. Pokud se vám kompatibilita ANSI netýká, můžete toto výchozí nastavení změnit na menší nebo větší číslo pomocí možnosti/H (omezit délku externích názvů).

**Specifické pro konec Microsoftu**

Kompilátor jazyka C považuje velká a malá písmena za odlišné znaky. Tato funkce označovaná jako "rozlišovat velká a malá písmena" umožňuje vytvořit jedinečné identifikátory, které mají stejnou kontrolu pravopisu, ale různé případy pro jedno nebo více písmen. Například každý z následujících identifikátorů je jedinečný:

```
add
ADD
Add
aDD
```

**Specifické pro Microsoft**

Nevybírejte názvy identifikátorů, které začínají dvěma podtržítky nebo podtržítkem následovaným velkým písmenem. Standard ANSI C umožňuje, aby názvy identifikátorů, které začínají těmito kombinacemi znaků, byly rezervovány pro použití kompilátorem. Identifikátory s rozsahem na úrovni souboru by také neměly být pojmenovány podtržítkem a malým písmenem jako první dvě písmena. Názvy identifikátorů, které začínají těmito znaky, jsou také vyhrazené. Podle konvence používá společnost Microsoft podtržítko a velké písmeno k zahájení názvů maker a dvojitých podtržítek pro názvy klíčových slov specifických pro společnost Microsoft. Aby nedošlo ke konfliktům při pojmenování, vždy vyberte názvy identifikátorů, které nezačínají jedním nebo dvěma podtržítky nebo názvy začínající podtržítkem následovaným velkým písmenem.

**Specifické pro konec Microsoftu**

Následují příklady platných identifikátorů, které odpovídají omezením názvů ANSI nebo Microsoftu:

```
j
count
temp1
top_of_page
skip12
LastNum
```

**Specifické pro Microsoft**

I když v identifikátorech ve zdrojových souborech rozlišuje velká a malá písmena ve výchozím nastavení, symboly v souborech objektů nejsou. Jazyk Microsoft C považuje identifikátory v rámci jednotky kompilace za rozlišování velkých a malých písmen.

Linker společnosti Microsoft rozlišuje velká a malá písmena. Je nutné zadat všechny identifikátory konzistentně podle velikosti písmen.

"Zdrojová znaková sada" je sada platných znaků, které se mohou objevit ve zdrojových souborech. Pro jazyk Microsoft C je zdrojovou sadou standardní znaková sada ASCII. Zdrojová znaková sada a spouštěcí znaková sada zahrnuje znaky ASCII používané jako řídicí sekvence. Informace o znakové sadě spuštění naleznete v tématu [konstanty znaků](../c-language/c-character-constants.md) .

**Specifické pro konec Microsoftu**

Identifikátor má "obor", což je oblast programu, ve které je známo, a "propojení", které určuje, zda stejný název v jiném oboru odkazuje na stejný identifikátor. Tato témata jsou vysvětlena v [oblasti životnost, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md).

## <a name="see-also"></a>Viz také

[Elementy jazyka C](../c-language/elements-of-c.md)
