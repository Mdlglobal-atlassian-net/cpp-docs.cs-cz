---
title: Argumenty funkce typu odkazu | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- functions [C++], paramters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b94f6b89ec00cc044cbaa93a4f0f914860db71e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="reference-type-function-arguments"></a>Argumenty funkce typu odkazu
Často je efektivnější funkcím předávat reference namísto velkých objektů. To umožňuje kompilátoru předat adresu objektu při zachování syntaxe, která by byla použita k přístupu k objektu. Prohlédněte si následující příklad používající strukturu `Date`:  
  
```  
// reference_type_function_arguments.cpp  
struct Date  
{  
short DayOfWeek;  
short Month;  
short Day;  
short Year;  
};  
  
// Create a Julian date of the form DDDYYYY  
// from a Gregorian date.  
long JulianFromGregorian( Date& GDate )  
{  
static int cDaysInMonth[] = {  
31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31  
   };  
long JDate = 0;  
// Add in days for months already elapsed.  
for ( int i = 0; i < GDate.Month - 1; ++i )  
JDate += cDaysInMonth[i];  
// Add in days for this month.  
JDate += GDate.Day;  
  
// Check for leap year.  
if ( GDate.Year % 100 != 0 && GDate.Year % 4 == 0 )  
JDate++;  
// Add in year.  
JDate *= 10000;  
JDate += GDate.Year;  
  
return JDate;  
}  
  
int main()  
{  
}  
```  
  
 Předchozí kód ukazuje, že členů struktury předaná odkaz ke kterým se přistupuje pomocí operátoru výběru členů (**.**) místo výběru členů operátor ukazatele (**->**).  
  
 I když argumentů předaných jako odkazové typy sledovat syntaxe typů bez ukazatele, zachovávají jedna důležité charakteristika typů ukazatele: jejich lze měnit, pokud deklarovaný jako **const**. Jelikož účelem předcházejícího kódu není upravit objekt `GDate`, je vhodnějším prototypem funkce tento prototyp:  
  
```  
long JulianFromGregorian( const Date& GDate );  
```  
  
 Tento prototyp zaručuje, že funkce `JulianFromGregorian` nezmění svůj argument.  
  
 Všechny funkce deklaraci jako trvá odkazového typu může přijmout objekt stejného typu místo ní, protože je standardní převod z *typename* k *typename*  **&** .  
  
## <a name="see-also"></a>Viz také  
 [Odkazy](../cpp/references-cpp.md)