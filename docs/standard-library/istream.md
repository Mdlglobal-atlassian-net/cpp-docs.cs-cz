---
title: '&lt;IStream on Request&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
dev_langs: C++
helpviewer_keywords: istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 570a23dff65c6c4838d85083b25507bbf0f68e44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ltistreamgt"></a>&lt;IStream on Request&gt;
Definuje basic_istream – třída šablony, která zprostředkovává extrakce pro iostreams, a basic_iostream – třída šablony, která zprostředkovává vložení a extrakce. Záhlaví definuje také související manipulator. Tento soubor záhlaví je obvykle zahrnuté pro můžete pomocí jiné záhlaví iostreams; Máte zřídka se zahrnuje přímo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <istream>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[iostream](../standard-library/istream-typedefs.md#iostream)|Typ `basic_iostream` specializované na `char`.|  
|[IStream on Request](../standard-library/istream-typedefs.md#istream)|Typ `basic_istream` specializované na `char`.|  
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Typ `basic_iostream` specializované na **wchar**.|  
|[wistream](../standard-library/istream-typedefs.md#wistream)|Typ `basic_istream` specializované na **wchar**.|  
  
### <a name="manipulators"></a>Manipulátory  
  
|||  
|-|-|  
|[ws](../standard-library/istream-functions.md#ws)|Přeskočí mezer v datovém proudu.|  
|[swap](../standard-library/istream-functions.md#istream_swap)|Výměny dva objekty datového proudu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor >>](../standard-library/istream-operators.md#op_gt_gt)|Extrahuje znaky a řetězce z datového proudu.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[basic_iostream –](../standard-library/basic-iostream-class.md)|Datový proud třídu, která můžete provést i vstup a výstup.|  
|[basic_istream –](../standard-library/basic-istream-class.md)|Šablony třídy popisuje objekt, který řídí extrakce elementů a kódovaného objekty z datového proudu vyrovnávací paměť elementy typu **Elem**, také známé jako [char_type –](../standard-library/basic-ios-class.md#char_type), jehož vlastnosti znak jsou Určuje třídu **Tr**, také známé jako [traits_type –](../standard-library/basic-ios-class.md#traits_type).|  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)



