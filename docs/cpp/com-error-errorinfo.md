---
title: _com_error::ErrorInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fbc735dfae1b30209eccfd14f1170826fb07680
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410990"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Konkrétní Microsoft**  
  
 Načte **IErrorInfo** objekt předaný konstruktoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IErrorInfo * ErrorInfo( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Nezpracovaná **IErrorInfo** položky předaný do konstruktoru.  
  
## <a name="remarks"></a>Poznámky  
 Načte zapouzdřené **IErrorInfo** položky v `_com_error` objekt, nebo **NULL** Pokud žádné **IErrorInfo** se zaznamenává položka. Volající musí volat **verze** prostřednictvím vráceného objektu po dokončení jeho použití.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)