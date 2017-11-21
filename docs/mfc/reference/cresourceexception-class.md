---
title: "Třída CResourceException | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs: C++
helpviewer_keywords: CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 497ced5337a44bb0d72be734cfea35a30ead383b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cresourceexception-class"></a>CResourceException – třída
Generovány, pokud systém Windows nemůže najít nebo přidělit požadovaný prostředek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CResourceException : public CSimpleException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CResourceException::CResourceException](#cresourceexception)|Vytvoří `CResourceException` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Žádné další kvalifikace je nezbytné nebo možné.  
  
 Další informace o používání `CResourceException`, najdete v článku [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CResourceException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cresourceexception"></a>CResourceException::CResourceException  
 Vytvoří `CResourceException` objektu.  
  
```  
CResourceException();
```  
  
### <a name="remarks"></a>Poznámky  
 Nepoužívejte tento konstruktor přímo, ale spíš volání globální funkce [afxthrowresourceexception –](exception-processing.md#afxthrowresourceexception). Další informace o výjimkách, najdete v článku [zpracování výjimek v jazyce MFC](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [CException – třída](cexception-class.md)   
 [Graf hierarchie](../hierarchy-chart.md)


