---
title: CDynamicParameterAccessor::GetParamIO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetParamIO
- CDynamicParameterAccessor::GetParamIO
- ATL.CDynamicParameterAccessor.GetParamIO
- CDynamicParameterAccessor.GetParamIO
- ATL::CDynamicParameterAccessor::GetParamIO
dev_langs: C++
helpviewer_keywords: GetParamIO method
ms.assetid: 9c485e39-c67e-4df7-a707-c773019c4d1e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d09eee048e737b19b21f6d71518d2b70702df8a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicparameteraccessorgetparamio"></a>CDynamicParameterAccessor::GetParamIO
Určuje, zda je zadaný parametr vstupní nebo výstupní parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      bool GetParamIO(   
   DBORDINAL nParam,   
   DBPARAMIO * pParamIO    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `nParam`  
 [v] Parametr číslo (posun od 1). Parametr 0 je vyhrazena pro vrácené hodnoty. Parametr číslo je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. V tématu [setParam –](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.  
  
 *pParamIO*  
 Ukazatel na proměnné obsahující **DBPARAMIO** typ zadaného parametru (vstup nebo výstup). Je definován následujícím způsobem:  
  
```  
typedef DWORD DBPARAMIO;  
  
enum DBPARAMIOENUM {  
    DBPARAMIO_NOTPARAM   = 0,  
    DBPARAMIO_INPUT      = 0x1,  
    DBPARAMIO_OUTPUT     = 0x2  
};  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** v případě úspěchu nebo **false** při selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)