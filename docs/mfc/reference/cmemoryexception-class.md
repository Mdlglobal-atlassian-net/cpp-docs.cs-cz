---
title: "Třída CMemoryException | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
dev_langs: C++
helpviewer_keywords: CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13130321dd26612b2bbd24457e02e09ce5fe1ec6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmemoryexception-class"></a>CMemoryException – třída
Představuje podmínku nedostatku paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMemoryException : public CSimpleException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMemoryException::CMemoryException](#cmemoryexception)|Vytvoří `CMemoryException` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Žádné další kvalifikace je nezbytné nebo možné. Paměť je vyvolána automaticky **nové**. Pokud píšete vašich vlastních funkcích paměti, pomocí `malloc`, pro příklad, pak jsou zodpovědný za generování výjimek paměti.  
  
 Další informace o `CMemoryException`, najdete v článku [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CMemoryException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="cmemoryexception"></a>CMemoryException::CMemoryException  
 Vytvoří `CMemoryException` objektu.  
  
```  
CMemoryException();  
```  
  
### <a name="remarks"></a>Poznámky  
 Nepoužívejte tento konstruktor přímo, ale spíš volání globální funkce [afxthrowmemoryexception –](exception-processing.md#afxthrowmemoryexception). globální funkce můžete v situacích, z důvodu nedostatku paměti úspěšné, protože ji vytvoří objekt výjimky v dříve přidělené paměti. Další informace o zpracování výjimek, najdete v článku [výjimky](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [CException – třída](cexception-class.md)   
 [Graf hierarchie](../hierarchy-chart.md)



