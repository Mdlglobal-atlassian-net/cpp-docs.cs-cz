---
title: Asyncbase::get_errorcode – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- get_ErrorCode method
ms.assetid: 50b4f8a2-9a21-4ea0-bb5d-7ff524d62aea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88d2dd1d09b573b89e69d28071c7f689fa8396d7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859628"
---
# <a name="asyncbasegeterrorcode-method"></a>AsyncBase::get_ErrorCode – metoda
Načte kód chyby pro aktuální asynchronní operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   get_ErrorCode  
)(HRESULT* errorCode) override;  
```  
  
#### <a name="parameters"></a>Parametry  
 `errorCode`  
 Umístění, kde jsou uložené aktuální kód chyby.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném E_ILLEGAL_METHOD_CALL, pokud je uzavřený aktuální asynchronní operace.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)