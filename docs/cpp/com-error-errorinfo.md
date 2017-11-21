---
title: _com_error::ErrorInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::ErrorInfo
dev_langs: C++
helpviewer_keywords: ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3e968a3b9814aeec898d4e157781b58c40a87e25
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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