---
title: "Třída CUserException | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CUserException
dev_langs: C++
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4613f2ba06ffa697df219172b98a5cf193c1f3b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cuserexception-class"></a>CUserException – třída
Došlo k ukončení operace koncového uživatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CUserException : public CSimpleException  
```  
  
## <a name="remarks"></a>Poznámky  
 Použít `CUserException` když chcete použít mechanismus výjimek throw/catch výjimky specifické pro aplikaci. "User" v názvu třídy jde interpretovat jako "Moje uživatele udělala něco výjimečných potřebuji ke zpracování."  
  
 A `CUserException` je obvykle vyvolána po volání metody globální funkce `AfxMessageBox` upozorní uživatele, které operace se nezdařila. Když píšete obslužnou rutinu výjimky, ošetření výjimky speciálně, protože uživatel obvykle již byla oznámena selhání. Rozhraní, v některých případech vyvolá výjimku. Chcete-li throw `CUserException` sami, upozornit uživatele a pak zavolají globální funkce `AfxThrowUserException`.  
  
 V následujícím příkladu funkci obsahující operace, které může dojít k selhání upozorní uživatele a vyvolá `CUserException`. Volání funkce zachytí výjimky a zpracovává speciálně:  
  
 [!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]  
  
 Další informace o používání `CUserException`, najdete v článku [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CUserException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CException – třída](../../mfc/reference/cexception-class.md)
