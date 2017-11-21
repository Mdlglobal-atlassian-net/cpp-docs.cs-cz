---
title: "future_error – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: future/std::future_error
dev_langs: C++
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cdb482dd71e19ad784e0e878432d800a384d57fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="futureerror-class"></a>future_error – třída
Popisuje výjimka objekt, který může být vyvolána metodami typů, které spravují [budoucí](../standard-library/future-class.md) objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<budoucí >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [logic_error – třída](../standard-library/logic-error-class.md)   
 [error_code – třída](../standard-library/error-code-class.md)
