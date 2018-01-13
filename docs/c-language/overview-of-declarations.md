---
title: "Přehled deklarací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa6285504a194d909dec7a446437ca9f584272a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-declarations"></a>Přehled deklarací
"Prohlášení" Určuje interpretace a atributy sadu identifikátory. Deklaraci, která taky Určuje, že úložiště, které budou rezervovány pro objekt nebo funkce s názvem identifikátorem se nazývá "definition". C deklarace proměnné, funkce a typy mají tuto syntaxi:  
  
## <a name="syntax"></a>Syntaxe  
 `declaration`:  
 *specifikátory deklarace* *atribut seq*opt*init. deklarátor seznamu*opt**;**  
  
 /\**atribut seq*opt je Microsoft konkrétní * /  
  
 *specifikátory deklarace*:  
 *specifikátor třídy úložiště specifikátory deklarace*opt  
  
 *Specifikátor typu deklarace – specifikátory*opt  
  
 *Kvalifikátor typu deklarace – specifikátory*opt  
  
 *Init – deklarátor seznamu*:  
 *Init – deklarátor*  
  
 *Init – deklarátor seznamu* , *init deklarátor*  
  
 *Init – deklarátor*:  
 *deklarátor*  
  
 *deklarátor***=***inicializátoru*   
  
> [!NOTE]
>  Tuto syntaxi pro `declaration` neopakuje v následujících částech. Syntaxe v následujících částech obvykle začíná `declarator` nonterminal.  
  
 Deklarace v *init. deklarátor seznamu* obsahovat identifikátory se s názvem; *init* je zkratkou pro inicializátor. *Init. deklarátor seznamu* je textový soubor s oddělovači pořadí deklarátory, z nichž každá může mít další typ informace, nebo inicializátoru nebo obojí. `declarator` Obsahuje identifikátory, pokud existuje, je deklarován. *Specifikátory deklarace* nonterminal se skládá z posloupnost specifikátory typu a třídy úložiště, které indikují propojení, trvání uložení a alespoň část typu entity, které označují deklarátory. Proto deklarace vytvořené kombinaci specifikátory třídy úložiště, specifikátory typu, kvalifikátory typu, deklarátor a inicializátory.  
  
 Deklarace může obsahovat jednu nebo více volitelných atributů uvedenými v *atribut seq*; *seq* je zkratkou pro pořadí. Tyto atributy specifické pro společnost Microsoft provést celou řadu funkcí, které jsou podrobněji v této příručce.  
  
 Obecné formou deklarace proměnné *specifikátor typu* poskytuje datový typ proměnné. *Specifikátor typu* může být složené, jako když je typ upraveném **const** nebo `volatile`. `declarator` Poskytuje název proměnné, které by mohly mít upravit tak, aby deklarovat pole nebo ukazatel typu. Například  
  
```  
int const *fp;  
```  
  
 deklaruje proměnné s názvem `fp` jako ukazatel na neupravitelnými (**const**) `int` hodnotu. V deklaraci můžete definovat více než jednu proměnnou pomocí více deklarátory, oddělených čárkami.  
  
 Deklaraci musí mít alespoň jeden deklarátor nebo jeho specifikace typu musí deklarovat značku struktury, sjednocení značka nebo členy výčtu. Deklarátory zadejte zbývající informace o identifikátoru. Deklarátor je identifikátor, který lze upravit do závorek (**[]**), hvězdičky (**\***), nebo závorky ( **()** ) deklarovat pole, ukazatele, nebo typ, funkce v uvedeném pořadí. Pokud deklarace jednoduchých proměnných (například znak, celé číslo a položky s plovoucí desetinnou čárkou), nebo struktury a sjednocení jednoduché proměnné `declarator` je právě identifikátor. Další informace o deklarátory najdete v tématu [deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md).  
  
 Všechny definice jsou implicitně deklarace, ale ne všechny deklarace jsou definice. Například deklarace proměnných, které začínají `extern` – specifikátor třídy úložiště "odkazují," místo "definování" deklarace. Pokud má proměnná externí uvedené dříve, než je definován, nebo pokud je definována v jiné zdrojový soubor z jednoho místa se používají `extern` deklarace je nezbytné. Úložiště není přidělena "odkazující" deklarace, ani jde inicializovat proměnné v deklaracích.  
  
 Třídy úložiště nebo typu (nebo obě) je vyžadováno deklarace proměnných. S výjimkou `__declspec`, v deklaraci je povolen pouze jeden – specifikátor třídy úložiště, a ne všechny specifikátory třídy úložiště jsou povoleny v každé kontextu. `__declspec` Třídy úložiště je povolená s dalšími specifikátory třídy úložiště, a je povolená více než jednou. Specifikátor třídy úložiště prohlášení ovlivňuje způsob je deklarovaný položky uložené a inicializovat a které části program může odkazovat položky.  
  
 *Specifikátor třídy úložiště* zahrnují terminály, které jsou definované v jazyce C **automaticky**, `extern`, **zaregistrovat**, **statické**a `typedef`. Zahrnuje také Microsoft C *specifikátor třídy úložiště* terminálu `__declspec`. Všechny *specifikátor třídy úložiště* terminály s výjimkou `typedef` a `__declspec` jsou popsané v [třídy úložiště](../c-language/c-storage-classes.md). V tématu [Typedef – deklarace](../c-language/typedef-declarations.md) informace o `typedef`. V tématu [rozšířené atributy třídy úložiště](../c-language/c-extended-storage-class-attributes.md) informace o `__declspec`.  
  
 Umístění prohlášení v rámci zdrojový program a přítomnosti nebo absenci dalších deklarace proměnné jsou důležité faktory při určení životnost proměnné. Může být více redeclarations, ale jenom jednu definici. Definice však může vyskytovat v více než jednu jednotku překlad. Pro objekty s vnitřní propojení, toto pravidlo vztahuje samostatně jednotlivé překlad jednotky, protože interně propojené objekty jsou jedinečné pro překlad jednotky. Pro objekty s externím propojením toto pravidlo platí pro celou aplikaci. V tématu [doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) Další informace o viditelnosti.  
  
 Specifikátory typu poskytují několik informací o datových typech identifikátorů. Specifikátor typu výchozí je `int`. Další informace najdete v tématu [specifikátory typu](../c-language/c-type-specifiers.md). Specifikátory typu můžete definovat také typ značky, struktury a sjednocení součást názvy a konstanty výčtu. Další informace najdete v části [deklarace výčtů](../c-language/c-enumeration-declarations.md), [deklarace struktury](../c-language/structure-declarations.md), a [deklarace sjednocení](../c-language/union-declarations.md).  
  
 Existují dva *kvalifikátor typu* terminály: **const** a `volatile`. Tyto kvalifikátory zadat další vlastnosti z typů, které jsou relevantní jenom v případě, že přístup k objektům tohoto typu prostřednictvím hodnoty l. Další informace o **const** a `volatile`, najdete v části [kvalifikátory typu](../c-language/type-qualifiers.md). Definice hodnoty l, najdete v části [L-Value a R-Value výrazy](../c-language/l-value-and-r-value-expressions.md).  
  
## <a name="see-also"></a>Viz také  
 [Souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md)   
 [Deklarace a typy](../c-language/declarations-and-types.md)   
 [Souhrn deklarací](../c-language/summary-of-declarations.md)