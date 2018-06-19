---
title: _com_error::HRESULTToWCode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e3955fcda665e08e5415652a1e8f1f232d0fe13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412261"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode
**Konkrétní Microsoft**  
  
 Mapuje 32-bit `HRESULT` na 16bitové `wCode`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `hr`  
 32bitovou verzi `HRESULT` nejde mapovat na 16bitové `wCode`.  
  
## <a name="return-value"></a>Návratová hodnota  
 16bitové `wCode` namapovaný z 32bitovou verzi `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [_com_error::WCode](../cpp/com-error-wcode.md) Další informace.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error – třída](../cpp/com-error-class.md)