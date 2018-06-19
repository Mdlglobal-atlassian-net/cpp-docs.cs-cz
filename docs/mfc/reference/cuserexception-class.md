---
title: Třída CUserException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CUserException
dev_langs:
- C++
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1701f6894ba3b44205526c59bad7ef635c1bbbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369470"
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
