---
title: IErrorRecordsImpl::GetErrorDescriptionString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetErrorDescriptionString
- IErrorRecordsImpl.GetErrorDescriptionString
- IErrorRecordsImpl::GetErrorDescriptionString
dev_langs: C++
helpviewer_keywords: GetErrorDescriptionString method
ms.assetid: 8bc71c45-ca9f-4632-bb02-1aa9ed8086c4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a2acdf2cf0ba658077ea9f57fe8087326b3f7b2f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ierrorrecordsimplgeterrordescriptionstring"></a>IErrorRecordsImpl::GetErrorDescriptionString
Získá řetězec popis chyby z záznam chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      LPOLESTR GetErrorDescriptionString(  
   ERRORINFO& rCurError   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rCurError`  
 `ERRORINFO` v záznamu **IErrorInfo** rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec popisující chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IErrorRecordsImpl – třída](../../data/oledb/ierrorrecordsimpl-class.md)