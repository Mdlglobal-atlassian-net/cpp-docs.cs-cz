---
title: Identifikátory jazyka C | Dokumentace Microsoftu
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
ms.openlocfilehash: 910e5cb8686130a08976d63f4cc54512da2494a1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751641"
---
# <a name="c-identifiers"></a>Identifikátory jazyka C
"Identifikátory" nebo "symboly" jsou názvy proměnných, typy, funkce a popisky ve svém programu, které zadáte. Názvy identifikátorů se musí lišit v tvar a pád z klíčová slova. Klíčová slova (C nebo Microsoft) nejde použít jako identifikátory; ty jsou vyhrazené pro zvláštní použití. Vytvořit identifikátor zadáním v deklaraci proměnné, typ nebo funkce. V tomto příkladu `result` je identifikátor proměnná typu integer a `main` a `printf` jsou názvy identifikátorů pro funkce.  
  
```  
#include <stdio.h>  
  
int main()  
{  
    int result;  
  
    if ( result != 0 )  
        printf_s( "Bad file handle\n" );  
}  
```  
  
Po deklaraci, můžete v pozdější příkazy programu identifikátor pro odkazování na související hodnota.  
  
Zvláštní druh identifikátoru, volá příkaz popisek, lze použít v `goto` příkazy. (Deklarace jsou popsány v [deklarace a typy](../c-language/declarations-and-types.md) popisků příkazů jsou popsány v [příkaz goto a příkazy s popiskem](../c-language/goto-and-labeled-statements-c.md).)  
  
## <a name="syntax"></a>Syntaxe

*identifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nenumerickému*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor* *nenumerickému*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor* *číslice*

*nenumerickému*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ b c d e f g h můžu j k l mn o p q r s t u v w, x y z**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F G H MŮŽU J K L MN O P Q R S T U V W, X Y Z**

*číslice*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**
  
První znak název identifikátoru musí být `nondigit` (to znamená, první znak musí být podtržítkem nebo velké nebo malé písmeno). ANSI umožňuje šest důležité znaky v názvu identifikátor externí a 31 pro názvy identifikátorů vnitřní (uvnitř funkce). Externí identifikátory (těch, které jsou deklarovány v globálním oboru nebo s třídou úložiště deklarovány `extern`) můžou stát terčem další omezení názvů, protože tyto identifikátory musí zpracovat jiným softwarem, jako je například linkers.  
  
**Specifické pro Microsoft**  
  
Přestože ANSI umožňuje 6 významných znaků v názvech externí identifikátor a 31 pro názvy identifikátorů vnitřní (uvnitř funkce), kompilátor Microsoft C umožňuje 247 znaků v názvu identifikátor interní nebo externí. Pokud nejste obeznámeni s kompatibility ANSI, můžete změnit toto výchozí nastavení na hodnotu menší nebo větší pomocí /H (omezit délku externích názvů) možnost.  
  
**Specifické pro END Microsoft**  
  
Kompilátor jazyka C považuje velká a malá písmena být jedinečných znaků. Tato funkce volá "písmen" umožňuje vytvářet různé identifikátory, které mají stejné kontroly pravopisu ale různých případech pro jeden nebo více písmeny. Například každá z následujících identifikátorů je jedinečný:  
  
```  
add  
ADD  
Add  
aDD  
```  
  
**Specifické pro Microsoft**  
  
Nesmí být zvolen názvy identifikátorů začínajících dvěma podtržítky nebo podtržítkem, za nímž následuje velké písmeno. Standard ANSI C umožňuje názvy identifikátorů, které začínají tyto kombinace znaků, které budou rezervovány pro použití kompilátoru. Identifikátory s rozsahem souboru úrovni nesmí mít jako první dvě písmena názvy také s podtržítkem a malé písmeno. Názvy identifikátorů, které začínají tyto znaky jsou také vyhrazené. Podle konvence společnost Microsoft používá symbol podtržítka a velkého písmene zahájíte názvy maker a dvou podtržítek pro názvy klíčových slov specifických pro společnost Microsoft. Aby se zabránilo konfliktům pojmenování, vždy vyberte názvy identifikátorů, které nezačínají jednu nebo dvě podtržítka nebo názvy začínající podtržítkem, za nímž následuje velké písmeno.  
  
**Specifické pro END Microsoft**  
  
Následují příklady platné identifikátory, které odpovídají omezení názvů ANSI nebo Microsoft:  
  
```  
j  
count  
temp1  
top_of_page  
skip12  
LastNum  
```  
  
**Specifické pro Microsoft**  
  
I když identifikátory ve zdrojových souborech se ve výchozím nastavení rozlišují malá a velká písmena, symboly v souborech objektů nejsou. Microsoft C zpracovává identifikátory v rámci kompilační jednotky jako malá a velká písmena.  
  
Propojovací program společnosti Microsoft je velká a malá písmena. Je nutné zadat všechny identifikátory konzistentně podle případ.  
  
"Zdrojová znaková sada" je sada platných znaků, které se mohou objevit ve zdrojových souborech. Zdrojová sada pro Microsoft C je standardně znaková sada ASCII. Zdrojová znaková sada a spouštěcí znaková sada obsahuje znaky ASCII, použít jako řídící sekvence. Zobrazit [znakové konstanty](../c-language/c-character-constants.md) informace o provedení znakové sady.  
  
**Specifické pro END Microsoft**  
  
Má identifikátor "rozsah", což je oblast, ve kterém se označuje programu a "propojení", která určuje, zda se stejným názvem v jiném oboru odkazuje na stejný identifikátor. Tato témata jsou vysvětlené v [životnost, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md).  
  
## <a name="see-also"></a>Viz také  
[Elementy jazyka C](../c-language/elements-of-c.md)