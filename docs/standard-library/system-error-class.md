---
title: "system_error – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: system_error/std::system_error
dev_langs: C++
helpviewer_keywords: system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3795f289a454503e80aa06d281543cd94aaa0a55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="systemerror-class"></a>system_error – třída
Představuje základní třídu pro všechny výjimky vydané nahlásit nízké úrovně systémové chybě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class system_error : public runtime_error {  
public:  
    explicit system_error(error_code _Errcode,
    const string& _Message = "");

    system_error(error_code _Errcode,
    const char *_Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const string& _Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const char *_Message);
const error_code& code() const throw();
const error_code& code() const throw();

 };  
```  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty vrácené `what` ve třídě [výjimka](../standard-library/exception-class.md) sestavený ze `_Message` a uložené objektu typu [error_code](../standard-library/error-code-class.md) (buď `code` nebo `error_code(_Errval, _Errcat)`).  
  
 Členská funkce `code` vrátí uložené [error_code](../standard-library/error-code-class.md) objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<system_error – >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<system_error>](../standard-library/system-error.md)

