---
title: "&lt;ostream –&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
dev_langs: C++
helpviewer_keywords: ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d4805086fb3d63d16f5f9ce6bf3b9e900b436569
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ltostreamgt"></a>&lt;ostream –&gt;
Definuje třídu šablony [basic_ostream](../standard-library/basic-ostream-class.md), která zprostředkovává vložení pro iostreams. Záhlaví také definuje několik související manipulátory. (Tuto hlavičku je obvykle zahrnuté pro můžete jiným iostreams záhlaví. Je potřeba jen zřídka ho zahrňte přímo.)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <ostream>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[ostream –](../standard-library/ostream-typedefs.md#ostream)|Umožňuje vytvořit typ z `basic_ostream` který se specializuje na `char` a `char_traits` specializované na `char`.|  
|[wostream –](../standard-library/ostream-typedefs.md#wostream)|Umožňuje vytvořit typ z `basic_ostream` který se specializuje na `wchar_t` a `char_traits` specializované na `wchar_t`.|  
  
### <a name="manipulators"></a>Manipulátory  
  
|||  
|-|-|  
|[endl](../standard-library/ostream-functions.md#endl)|Ukončí řádku a vyprázdní vyrovnávací paměť.|  
|[ukončení](../standard-library/ostream-functions.md#ends)|Ukončí řetězec.|  
|[vyprázdnění](../standard-library/ostream-functions.md#flush)|Vyprázdní vyrovnávací paměť.|  
|[swap](../standard-library/ostream-functions.md#swap)|Výměny hodnoty doleva `basic_ostream` objektu parametr pro ty právo `basic_ostream` parametru objektu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor <<](../standard-library/ostream-operators.md#op_lt_lt)|Různé typy zapíše do datového proudu.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[basic_ostream –](../standard-library/basic-ostream-class.md)|Šablony třídy popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)



