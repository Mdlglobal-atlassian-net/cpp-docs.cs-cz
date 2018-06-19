---
title: Třída CNotSupportedException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
dev_langs:
- C++
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 510f9db4a7e5688df76baafa868846fd1614f584
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367487"
---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException – třída
Představuje výjimku, která je výsledkem požadavku nepodporované funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CNotSupportedException : public CSimpleException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|Vytvoří `CNotSupportedException` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Žádné další kvalifikace je nezbytné nebo možné.  
  
 Další informace o používání `CNotSupportedException`, najdete v článku [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CNotSupportedException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="cnotsupportedexception"></a>  CNotSupportedException::CNotSupportedException  
 Vytvoří `CNotSupportedException` objektu.  
  
```  
CNotSupportedException();
```  
  
### <a name="remarks"></a>Poznámky  
 Nepoužívejte tento konstruktor přímo, ale spíš volání globální funkce [afxthrownotsupportedexception –](exception-processing.md#afxthrownotsupportedexception). Další informace o zpracování výjimek, najdete v článku [zpracování výjimek v jazyce MFC](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [CException – třída](cexception-class.md)   
 [Graf hierarchie](../hierarchy-chart.md)


