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
ms.openlocfilehash: 77aefe41fecf003218343710ef090eebf99446a8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857109"
---
# <a name="c-storage-classes"></a>Třídy úložiště jazyka C

"Třída úložiště" proměnné určuje, zda má položka životnost "Global" nebo "local". C volá tyto dvě životnosti "static" a "automaticky". Položka s globální životností existuje a má hodnotu po celou dobu provádění programu. Všechny funkce mají globální životnost.

Automatické proměnné nebo proměnné s místními životnostmi jsou přiděleny nové úložiště pokaždé, když ovládací prvek pro spuštění projde do bloku, ve kterém jsou definovány. Když se spuštění vrátí, proměnné již nemají smysluplné hodnoty.

Jazyk C poskytuje následující specifikátory třídy úložiště:

## <a name="syntax"></a>Syntaxe

*specifikátor třídy úložiště*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**auto**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**registraci**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;**definice** typu &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *Rozšířený--modifikátor-SEQ* **)**  /\* \*specifický pro společnost Microsoft /

S výjimkou `__declspec`lze v deklaraci *specifikátoru deklarace* použít pouze jeden *specifikátor úložiště-Class* . Pokud není vytvořena žádná specifikace třídy úložiště, deklarace v rámci bloku vytvoří automatické objekty.

Položky deklarované pomocí specifikátoru **auto** nebo **Register** mají místní životnost. Položky deklarované se specifikátorem **static** nebo `extern` mají globální životnost.

Vzhledem k tomu, že `typedef` a `__declspec` jsou sémanticky odlišné od dalších čtyř terminálových *specifikátorů třídy úložiště* , jsou popsány samostatně. Konkrétní informace o `typedef`naleznete v tématu [deklarace typedef](../c-language/typedef-declarations.md). Konkrétní informace o `__declspec`najdete v tématu [Rozšířené atributy tříd úložiště](../c-language/c-extended-storage-class-attributes.md).

Umístění proměnných a deklarací funkcí v rámci zdrojových souborů má vliv také na třídu úložiště a viditelnost. Deklarace mimo všechny definice funkcí se říká, že se zobrazí na externí úrovni. Deklarace v rámci definic funkcí se zobrazí na úrovni "interní".

Přesný význam každého specifikátoru třídy úložiště závisí na dvou faktorech:

- Zda se deklarace zobrazuje na externí nebo interní úrovni

- Zda je deklarovaná položka proměnná nebo funkce

[Specifikátory třídy úložiště pro deklarace na externí úrovni](../c-language/storage-class-specifiers-for-external-level-declarations.md) a [specifikátory třídy úložiště pro deklarace na interní úrovni](../c-language/storage-class-specifiers-for-internal-level-declarations.md) popisují v každém typu deklarace terminály *specifikátoru úložiště* a vysvětlují výchozí chování při vynechání *specifikátoru třídy úložiště* z proměnné. [Specifikátory třídy úložiště s deklaracemi funkcí](../c-language/storage-class-specifiers-with-function-declarations.md) probírají specifikátory třídy úložiště používané s funkcemi.

## <a name="see-also"></a>Viz také:

[Deklarace a typy](../c-language/declarations-and-types.md)
