---
title: ICommandTextImpl::SetCommandText | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
dev_langs:
- C++
helpviewer_keywords:
- SetCommandText method
ms.assetid: 7271bfb0-7a8b-4281-b3e8-7c80b9fe79d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2a45b1f2bbe2318d1a08b80a7370b4077a985c03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099674"
---
# <a name="icommandtextimplsetcommandtext"></a>ICommandTextImpl::SetCommandText
Nastaví text příkazu, nahradí existující text příkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(SetCommandText)(REFGUID rguidDialect,   
   LPCOLESTR pwszCommand);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [ICommandTextImpl – třída](../../data/oledb/icommandtextimpl-class.md)   
 [ICommandTextImpl::GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)