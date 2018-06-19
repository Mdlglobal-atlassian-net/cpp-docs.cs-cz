---
title: Identifikátory jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cca0381392a1f7c2f227c3296597dc3c614ae0b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388666"
---
# <a name="c-identifiers"></a>Identifikátory jazyka C
"Identifikátory" nebo "symboly" jsou názvy, které zadáte pro proměnné, typy, funkce a popisky v programu. Identifikátor názvy se musí lišit v pravopis a případ z jakékoli klíčová slova. Klíčová slova (C nebo Microsoft) nelze použít jako identifikátory; jsou rezervovány pro speciální použití. Identifikátor vytvoříte tak, že zadáte v deklaraci proměnné, typ nebo funkci. V tomto příkladu `result` je identifikátor proměnné celé číslo, a `main` a `printf` jsou názvy identifikátor pro funkce.  
  
```  
#include <stdio.h>  
  
int main()  
{  
    int result;  
  
    if ( result != 0 )  
        printf_s( "Bad file handle\n" );  
}  
```  
  
 Po deklarovat, můžete v novější příkazy programu identifikátor k odkazování na přidružené hodnoty.  
  
 Zvláštní druh identifikátor, s názvem příkaz štítku, mohou být používány `goto` příkazy. (Deklarace jsou popsané v [deklarace a typy](../c-language/declarations-and-types.md) příkaz popisky jsou popsané v [goto a příkazy s popiskem](../c-language/goto-and-labeled-statements-c.md).)  
  
## <a name="syntax"></a>Syntaxe  
 *identifikátor*:  
 *nečíselným*  
  
 *identifikátor nečíselným*  
  
 *identifikátor číslice*  
  
 `nondigit`: jeden z  
 **_ b c d e f g h i j k l m n o p q r s t u v w x, y z**  
  
 **B C D E F G H I J K L M N O P Q R S T U V W X Y Z**  
  
 `digit`: jeden z  
 **0 1 2 3 4 5 6 7 8 9**  
  
 Název identifikátoru první znak musí být `nondigit` (tedy první znak musí být podtržítko nebo velké nebo malé písmeno). ANSI umožňuje šesti důležité znaky v názvu externí identifikátor a 31 pro názvy identifikátorů interní (v rámci funkce). Externí identifikátory (těch, které jsou deklarované v globálním oboru nebo deklarovat s třídy úložiště `extern`) mohou podléhat další omezení pro pojmenovávání, protože tyto identifikátory zpracování další software, jako je například linkers.  
  
 **Konkrétní Microsoft**  
  
 I když ANSI umožňuje 6 důležité znaky v názvech externí identifikátor a 31 pro názvy identifikátorů interní (v rámci funkce), umožňuje kompilátoru Microsoft C 247 znaků v název interních nebo externích identifikátoru. Pokud nejste s kompatibilitou ANSI dotyčné, můžete změnit toto výchozí nastavení na menší nebo větší číslo, pomocí /H (omezit délku externích názvů) možnost.  
  
 **Konkrétní Microsoft END**  
  
 Kompilátor jazyka C považuje velká a malá písmena být jedinečných znaků. Tato funkce volána "písmen" umožňuje vytváření různých identifikátorů, které mají stejnou pravopis ale odlišným případů pro jeden nebo více znaků. Každý z následujících identifikátorů je například jedinečný:  
  
```  
add  
ADD  
Add  
aDD  
```  
  
 **Konkrétní Microsoft**  
  
 Nevybírejte názvy pro identifikátory, které začínají s dvěma podtržítka nebo podtržítkem, za nímž následuje velké písmeno. ANSI C – standard umožňuje identifikátor názvy, které začínají tyto kombinace znaků, které budou rezervovány pro použití kompilátoru. Identifikátory s oborem úrovni souboru by neměl taky pojmenovaný s podtržítkem a malé písmeno jako první dvě písmena. Identifikátor názvy, které začínají tyto znaky jsou také vyhrazené. Podle konvence společnost Microsoft používá podtržítkem a velké písmeno zahájíte makro názvy a dvojité podtržítka pro názvy – klíčové slovo specifické pro společnost Microsoft. Všechny konfliktům pojmenování, vyberte vždy identifikátor názvy, které nemají na začátku jedno nebo dvě podtržítka nebo názvy, které začínají podtržítkem následuje velké písmeno.  
  
 **Konkrétní Microsoft END**  
  
 Následují příklady platný identifikátorů, které odpovídají omezení pro pojmenovávání ANSI nebo Microsoft:  
  
```  
j  
count  
temp1  
top_of_page  
skip12  
LastNum  
```  
  
 **Konkrétní Microsoft**  
  
 I když identifikátory ve zdrojových souborech se ve výchozím nastavení rozlišují malá a velká písmena, symboly v objektu soubory nejsou. Microsoft C zpracovává identifikátory v rámci kompilace jednotky jako malá a velká písmena.  
  
 Microsoft linkeru je malá a velká písmena. Je nutné zadat všechny identifikátory konzistentně podle případu.  
  
 "Znaková sada zdroje" je sada právní znaků, které se mohou objevit ve zdrojových souborech. Pro Microsoft C zdrojová sada je standardní znaková sada ASCII. Zdroj znakovou sadu a znaková sada spuštění obsahují znaky ASCII, použít jako řídicí sekvence. V tématu [konstanty znaků](../c-language/c-character-constants.md) informace o provádění znakové sady.  
  
 **Konkrétní Microsoft END**  
  
 Identifikátor má "obor", který označuje oblast, ve kterém se ví programu a "propojení", která určuje, zda se stejným názvem v jiném oboru odkazuje na stejný identifikátor. Tato témata jsou vysvětlené v [doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md).  
  
## <a name="see-also"></a>Viz také  
 [Elementy jazyka C](../c-language/elements-of-c.md)