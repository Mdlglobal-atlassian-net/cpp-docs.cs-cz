---
title: "&lt;codecvt –&gt; výčty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords: std::codecvt_mode
caps.latest.revision: "10"
manager: ghogen
ms.openlocfilehash: bba1b53abb7286c64bdaf79ec8cb2004ba67a9dd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt –&gt; výčty
  
##  <a name="codecvt_mode"></a>codecvt_mode – výčet  
 Určuje konfigurační informace pro [národního prostředí](../standard-library/locale-class.md) omezující vlastnosti.  
  
```  
enum codecvt_mode {  
    consume_header = 4,  
    generate_header = 2,  
    little_endian = 1  
 };  
```  
  
### <a name="remarks"></a>Poznámky  
 Výčet definuje tři konstanty, které poskytují informace o konfiguraci pro národní prostředí omezující vlastnosti deklarované v [ \<codecvt – >](../standard-library/codecvt.md). Odlišné hodnoty jsou:  
  
- `consume_header`, využívat sekvenci počáteční záhlaví při čtení vícebajtové pořadí a určit endianitou následné vícebajtové pořadí čtení  
  
- `generate_header`, generovat v sekvenci počáteční záhlaví při zápisu vícebajtové pořadí inzerovat endianitou následné vícebajtové pořadí má být zapsán  
  
- `little_endian`, generovat vícebajtové pořadí podle little endian oproti výchozí pořadí big endian  
  
 Tyto konstanty může být sloučeny pomocí operátoru OR společně v libovolné kombinace.  
  
## <a name="see-also"></a>Viz také  
 [\<codecvt – >](../standard-library/codecvt.md)

