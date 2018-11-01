---
title: Třídy úložiště jazyka C
ms.date: 08/31/2018
helpviewer_keywords:
- static variables, lifetime
- storage classes
- lifetime, variables
- specifiers, storage class
- storage class specifiers, C storage classes
- storage duration
ms.assetid: 893fb929-f7a9-43dc-a0b3-29cb1ef845c1
ms.openlocfilehash: cb472ea0db67e0fd8d7f2a8e2af4513ffb0fbe1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466180"
---
# <a name="c-storage-classes"></a>Třídy úložiště jazyka C

"Třídy úložiště" proměnné a určuje, zda položka má "globální" nebo "místní" doba života. C volá tyto dva životnosti "statická" a "automatické". Položka s globální životností existuje a má hodnotu v průběhu provádění programu. Všechny funkce mají globální životnost.

Automatické proměnné nebo proměnné s místní životnost, jsou přiděleny nové úložiště předá každý ovládací prvek v době provádění do bloku ve které jsou definovány. Při spuštění se vrátí, proměnné již smysluplné hodnoty.

Jazyk C poskytuje následující specifikátory třídy úložiště:

## <a name="syntax"></a>Syntaxe

*Storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Automaticky**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Registrace**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Statická**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Definice TypeDef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *extended-decl-modifier-seq* **)**  / \* specifické pro Microsoft \*/

S výjimkou `__declspec`, lze použít pouze jednu *storage-class-specifier* v *Specifikátor deklarace* v deklaraci. Pokud je provedeno bez specifikace paměťové třídy, vytvořte deklarace v rámci bloku automatických objektů.

Položky deklarované s **automaticky** nebo **zaregistrovat** specifikátor mají místní životnost. Položky deklarované s **statické** nebo `extern` specifikátor mají globální životnost.

Protože `typedef` a `__declspec` jsou sémanticky rozdílné z těchto čtyř *storage-class-specifier* terminály, jsou popsána samostatně. Podrobnější informace o `typedef`, naleznete v tématu [deklarace Typedef](../c-language/typedef-declarations.md). Podrobnější informace o `__declspec`, naleznete v tématu [rozšířené atributy třídy úložiště](../c-language/c-extended-storage-class-attributes.md).

Umístění deklarace proměnných a funkcí v rámci zdrojové soubory ovlivní také třídu úložiště a viditelnost. Deklarace mimo všechny definice funkcí se říká, že se vyskytují na úrovni "vnější úrovni." Deklarace v rámci definice funkce se zobrazí na "vnitřní úrovni."

Přesné význam jednotlivých – specifikátor třídy úložiště závisí na dva faktory:

- Určuje, zda se zobrazí deklarace na externí nebo interní úrovni

- Určuje, zda je položka deklarované proměnné nebo funkce

[Specifikátory třídy úložiště pro deklarace na externí úrovni](../c-language/storage-class-specifiers-for-external-level-declarations.md) a [specifikátory třídy úložiště pro deklarace na interní úrovni](../c-language/storage-class-specifiers-for-internal-level-declarations.md) popisují *storage-class-specifier* terminály v každý druh deklarace a výchozí chování při *storage-class-specifier* je vynecháno z proměnné. [Specifikátory třídy úložiště s deklaracemi funkce](../c-language/storage-class-specifiers-with-function-declarations.md) popisuje specifikátory třídy úložiště použít s funkcemi.

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)
