---
title: _com_error::HRESULTToWCode | Dokumentace Microsoftu
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
ms.openlocfilehash: f0ddac28c4f39cdf11abbdf38c3af5d00c22413a
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401903"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode
**Specifické pro Microsoft**  
  
 Mapuje 32-bit HRESULT na 16 bitů `wCode`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *hr*  
 Hodnota HRESULT 32-bit má být mapována na 16 bitů `wCode`.  
  
## <a name="return-value"></a>Návratová hodnota  
 16bitové `wCode` namapované na základě hodnoty HRESULT 32-bit.  
  
## <a name="remarks"></a>Poznámky  
 Zobrazit [_com_error::WCode](../cpp/com-error-wcode.md) Další informace.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error – třída](../cpp/com-error-class.md)