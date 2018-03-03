---
title: "Třída CInvalidArgException | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
dev_langs:
- C++
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 03f9bea1c9e5e88856bbf5a5aa2e824a2c99963c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cinvalidargexception-class"></a>CInvalidArgException – třída
Tato třída reprezentuje podmínku neplatný argument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CInvalidArgException : public CSimpleException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|Konstruktor|  
  
## <a name="remarks"></a>Poznámky  
 A `CInvalidArgException` objekt představuje podmínku neplatný argument.  
  
 Další informace o zpracování výjimek, najdete v článku [CException – třída](../../mfc/reference/cexception-class.md) tématu a [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CInvalidArgException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="cinvalidargexception"></a>CInvalidArgException::CInvalidArgException  
 Konstruktor  
  
```  
CInvalidArgException();
```  
  
### <a name="remarks"></a>Poznámky  
 Nepoužívejte tento konstruktor přímo. volání globální funkce **AfxThrowInvalidArgException**.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CSimpleException – třída](../../mfc/reference/csimpleexception-class.md)
