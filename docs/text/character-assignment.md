---
title: "Znak přiřazení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: c40e7d0c6861f4815d98ad4388aade8227b43dcb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="character-assignment"></a>Přiřazení znaků
Podívejte se na následující příklad, ve kterém `while` smyčky prohledá řetězec, zkopíruje všechny znaky s výjimkou 'X' do jiného řetězce:  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
        *sz1++ = *sz2++;  
    else  
        sz2++;  
}  
```  
  
 Kód zkopíruje bajt `sz2` do umístění, na kterou odkazuje `sz1`, pak zvýší `sz1` přijímat další bajtů. Ale pokud další znak v `sz2` je dvoubajtové znakové přiřazení `sz1` zkopíruje jenom prvním bajtem. Následující kód používá přenosné funkce kopíruje znak bezpečně a se zvýší `sz1` a `sz2` správně:  
  
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
 [Porovnávání znaku](../text/character-comparison.md)