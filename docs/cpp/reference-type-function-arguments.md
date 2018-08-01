---
title: Argumenty funkce typu odkazu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad8fc85a37aec80d09ed6df9280a78de0540f01
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408605"
---
# <a name="reference-type-function-arguments"></a>Argumenty funkce typu odkazu
Často je efektivnější funkcím předávat reference namísto velkých objektů. To umožňuje kompilátoru předat adresu objektu při zachování syntaxe, která by byla použita k přístupu k objektu. Prohlédněte si následující příklad používající strukturu `Date`:  
  
```cpp 
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
  
 Předchozí kód ukazuje, že členy struktury předané referencí jsou zpřístupněny pomocí operátoru výběru členů (**.**) namísto operátoru volby členu ukazatel (**->**).  
  
 Ačkoli argumenty předané jako typy referencí používají syntaxi typů typech bez ukazatele, zachovávají důležitou vlastnost typů ukazatelů: lze, pokud nejsou deklarovány jako je **const**. Jelikož účelem předcházejícího kódu není upravit objekt `GDate`, je vhodnějším prototypem funkce tento prototyp:  
  
```cpp 
long JulianFromGregorian( const Date& GDate );  
```  
  
 Tento prototyp zaručuje, že funkce `JulianFromGregorian` nezmění svůj argument.  
  
 Všechny funkce prototyp přijímá typ odkazu může přijmout objekt stejného typu na jeho místo, protože existuje standardní převod z *typename* na * typename ***&**.  
  
## <a name="see-also"></a>Viz také:  
 [Odkazy](../cpp/references-cpp.md)