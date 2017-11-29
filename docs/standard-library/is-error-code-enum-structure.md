---
title: "is_error_code_enum – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: future/std::is_error_code_enum
dev_langs: C++
ms.assetid: 84ae4b99-66d2-41ba-9b50-645fcbe14630
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f9af1193c168796b73866a26e654c2c18c85f318
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iserrorcodeenum-structure"></a>is_error_code_enum – struktura
Specializace, která označuje, že [future_errc](../standard-library/future-enums.md#future_errc) je vhodný pro ukládání [error_code](../standard-library/error-code-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <>
struct is_error_code_enum<Future_errc> : public true_type;
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<budoucí >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<budoucí >](../standard-library/future.md)


