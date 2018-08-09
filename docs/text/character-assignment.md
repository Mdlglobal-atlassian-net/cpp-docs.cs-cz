---
title: Přiřazení znaků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 084cfd69a3742db10e09e9d97974a0666fa31a47
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010409"
---
# <a name="character-assignment"></a>Přiřazení znaků
Zvažte následující příklad, ve kterém **při** smyčky vyhledá v řetězci, zkopíruje všechny znaky s výjimkou "X" do jiného řetězce:  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
        *sz1++ = *sz2++;  
    else  
        sz2++;  
}  
```  
  
 Kód zkopíruje bajt `sz2` do umístění, na které odkazuje `sz1`, pak inkrementuje `sz1` přijímat další bajt. Avšak v tom případě další znak v `sz2` je dvoubajtové znakové přiřazení `sz1` zkopíruje pouze první bajt. Následující kód používá přenosné funkce znak bezpečně zkopírovat a druhý se zvýší `sz1` a `sz2` správně:  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
    {  
        _mbscpy_s( sz1, 1, sz2 );  
        sz1 = _mbsinc( sz1 );  
        sz2 = _mbsinc( sz2 );  
    }  
    else  
        sz2 = _mbsinc( sz2 );  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Porovnávání znaků](../text/character-comparison.md)