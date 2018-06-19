---
title: _com_error::WCodeToHRESULT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCodeToHRESULT
dev_langs:
- C++
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31b9df8305d0eea772979904f63847f6d6c2325a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413372"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT
**Konkrétní Microsoft**  
  
 Mapuje 16bitové `wCode` na 32-bit `HRESULT`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `wCode`  
 16bitová hodnota `wCode`, která má být mapována na 32bitovou hodnotu `HRESULT`.  
  
## <a name="return-value"></a>Návratová hodnota  
 32bitová hodnota `HRESULT` mapovaná z 16bitové hodnoty `wCode`.  
  
## <a name="remarks"></a>Poznámky  
 Najdete v článku [wcode –](../cpp/com-error-wcode.md) – členská funkce.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error – třída](../cpp/com-error-class.md)