---
title: "space_info – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: filesystem/std::tr2::sys::space_info
dev_langs: C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50657e33becd0fb2dae94d515f82120d6a71e342
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="spaceinfo-structure"></a>space_info – struktura
Obsahuje informace o svazku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct space_info   {
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
    };  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|`unsigned long long available`|Představuje počet bajtů, které jsou k dispozici, která bude představovat data na svazku.|  
|`unsigned long long capacity`|Představuje celkový počet bajtů, které může představovat svazku.|  
|`unsigned long long free`|Představuje počet bajtů, které nejsou používány k reprezentaci dat na svazku.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<filesystem >  
  
 **Namespace:** std::experimental::filesystem  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<FileSystem >](../standard-library/filesystem.md)   
 [místo](http://msdn.microsoft.com/en-us/7fce0b0e-523b-4598-b218-47245d0204ca)   
 [Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)

