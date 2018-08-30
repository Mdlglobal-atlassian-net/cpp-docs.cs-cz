---
title: Přehled deklarací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac843ef83d2de4f9cf84a44c67859becaead6ec6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218501"
---
# <a name="overview-of-declarations"></a>Přehled deklarací
"Deklarace" Určuje atributy sadu identifikátorů a interpretace. Deklarace, která také způsobí, že úložiště, které budou rezervovány pro objekt nebo funkce s názvem podle identifikátoru se nazývá "definice". Deklarace proměnné, funkce a typy v jazyce C mají tuto syntaxi:  
  
## <a name="syntax"></a>Syntaxe

*deklarace*:  
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *sekvence atributů*<sub>optimalizované</sub> *init-declarator-list*<sub>optimalizované</sub>**;**

/\* *sekvence atributů*<sub>optimalizované</sub> je konkrétní Microsoft * /

*specifikátory deklarace*:  
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specifikátory deklarace*<sub>optimalizované</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub>  

*init-declarator-list*:  
&nbsp;&nbsp;&nbsp;&nbsp;*Init-declarator*  
&nbsp;&nbsp;&nbsp;&nbsp;*Init-declarator-list* **,** *init-declarator*  

*Init-declarator*:  
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarátor*  
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor* **=** *inicializátor*  
  
> [!NOTE]
> Tato syntaxe pro *deklarace* neopakuje v následujících částech. Syntaxe v následujících částech obvykle začíná *deklarátor* neterminálu.  
  
 Deklarace v *init-declarator-list* obsahovat identifikátory jmenován; *init* je zkratka pro inicializátor. *Init-declarator-list* je čárkou oddělený posloupnost deklarátory, z nichž každá může mít informace o dalších typu inicializátor nebo obojí. *Deklarátor* obsahuje identifikátory, pokud existuje, byl deklarován. *Specifikátory deklarace* neterminálu se skládá z posloupnost specifikátory typu a třídy úložiště, které označují propojení, dobou trvání úložiště a alespoň části typu entity, které označují deklarátory. Deklarace jsou proto skládá z kombinace specifikátory úložiště třídy specifikátory typu, kvalifikátory typu, deklarátory a inicializátory.  
  
 Deklarace může obsahovat jednu nebo více volitelných atributů uvedenými v *sekvence atributů*; *seq* je zkratka pro pořadí. Tyto atributy specifické pro společnost Microsoft provádět celou řadu funkcí, které jsou popsány podrobně v této knize.  
  
 Ve formuláři Obecné v deklaraci proměnné *specifikátor typu* poskytuje datový typ proměnné. *Specifikátor typu* může být složené, jako když je změněn na typ podle **const** nebo `volatile`. `declarator` Poskytuje název proměnné, případně upravit tak, aby deklarace pole nebo typ ukazatele. Například  
  
```  
int const *fp;  
```  
  
 deklaruje proměnnou s názvem `fp` jako ukazatel na jsou neupravitelnými (**const**) `int` hodnotu. Více než jednu proměnnou můžete definovat v deklaraci pomocí víc deklarátorů, oddělené čárkami.  
  
 Deklarace musí mít aspoň jeden deklarátor nebo specifikátor jeho typ musí deklarovat značku struktury, sjednocení značku nebo členy výčtu. Deklarátory zadejte zbývající informace o identifikátoru. Deklarátor je identifikátor, který můžete upravit pomocí závorek (**[] č.**), hvězdičky (<strong>\*</strong>), nebo složených závorek ( **()** ) Chcete-li deklarovat pole, ukazatel, nebo typ, funkce v uvedeném pořadí. Když deklarujete jednoduché proměnné (jako je znak, celé číslo a položky s plovoucí desetinnou čárkou), nebo struktury a sjednocení jednoduché proměnné `declarator` je právě identifikátor. Další informace o deklarátorech naleznete v tématu [deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md).  
  
 Všechny definice jsou implicitně deklarace, ale ne všechny deklarace jsou definice. Například deklarace proměnných, které začínají `extern` specifikátor storage-class "odkazují," místo "definující" deklarace. Pokud k externí proměnné, je možné odkazovat dříve, než je definován, nebo pokud je definován v jiném zdrojovém souboru z jednoho, kde se používá `extern` deklarace je nezbytné. Úložiště není přidělaná "odkazující" deklarace ani lze inicializovat proměnné na deklaracích.  
  
 Třída úložiště typu (nebo obojí) se vyžaduje v deklaracích proměnných. S výjimkou `__declspec`pouze jednu třídu úložiště specifikátor je povolený v deklaraci a ne všechny Specifikátory paměťových tříd nejsou povoleny v každé kontextu. `__declspec` Třída úložiště je povolená s dalšími specifikátory třídy úložiště a je povolen více než jednou. Specifikátor třídy úložiště deklarace ovlivňuje, jak je deklarovaný položky uložené a inicializován a které části programu může odkazovat na položky.  
  
 *Storage-class-specifier* terminály, které jsou definovány v jazyce C obsahují **automaticky**, `extern`, **zaregistrovat**, **statické**a `typedef`. Kromě toho Microsoft C zahrnuje *storage-class-specifier* terminálu `__declspec`. Všechny *storage-class-specifier* terminály s výjimkou `typedef` a `__declspec` jsou popsány v [třídy úložiště](../c-language/c-storage-classes.md). Zobrazit [deklarace Typedef](../c-language/typedef-declarations.md) informace o `typedef`. Zobrazit [rozšířené atributy třídy úložiště](../c-language/c-extended-storage-class-attributes.md) informace o `__declspec`.  
  
 Umístění deklarace v rámci zdrojového programu a přítomnosti nebo nepřítomnosti jiné deklarace proměnné jsou důležité faktory při určení platnosti proměnných. Může existovat více redeclarations, ale jenom jednu definici. Definice však mohou objevit v více než jedné jednotky překladu. Pro objekty s vnitřním propojením toto pravidlo platí samostatně pro každou jednotku převodu, protože vnitřně propojené objekty jsou jedinečné pro jednotku překladu. Pro objekty s externí vazbou. Toto pravidlo platí pro celý program. Zobrazit [životnost, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) Další informace o viditelnosti.  
  
 Specifikátory typu poskytnout určité informace o datových typech identifikátorů. Výchozí specifikátor typu je `int`. Další informace najdete v tématu [specifikátory typu](../c-language/c-type-specifiers.md). Specifikátory typu můžete také definovat tagy typu, struktury a sjednocení komponenty názvy a konstanty výčtu. Další informace najdete v části [deklarace výčtů](../c-language/c-enumeration-declarations.md), [deklarace struktur](../c-language/structure-declarations.md), a [deklarace sjednocení](../c-language/union-declarations.md).  
  
 Existují dva *kvalifikátor typu* terminály: **const** a `volatile`. Kvalifikátory zadat další vlastnosti typů, které jsou relevantní pouze v případě, že objekty tohoto typu přístupu s využitím l hodnoty. Další informace o **const** a `volatile`, naleznete v tématu [kvalifikátory typu](../c-language/type-qualifiers.md). Definici l hodnoty naleznete v tématu [výrazy L-Value a R-Value](../c-language/l-value-and-r-value-expressions.md).  
  
## <a name="see-also"></a>Viz také  
 [Souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md)   
 [Deklarace a typy](../c-language/declarations-and-types.md)   
 [Souhrn deklarací](../c-language/summary-of-declarations.md)