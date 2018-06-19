---
title: Třída COleException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
dev_langs:
- C++
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46f554e375e8c0185e8c2b75c81eeae5ee615c51
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370468"
---
# <a name="coleexception-class"></a>COleException – třída
Představuje podmínku výjimky související s operace OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleException : public CException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleException::Process](#process)|Přeloží Zachycenou výjimku do OLE návratový kód.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleException::m_sc](#m_sc)|Obsahuje kód stavu, který označuje důvod výjimky.|  
  
## <a name="remarks"></a>Poznámky  
 `COleException` Třída zahrnuje veřejná data člena, který obsahuje stavový kód označující důvod pro výjimku.  
  
 Obecně byste je neměli vytvářet `COleException` objekt přímo; místo toho by měly volat [afxthrowoleexception –](exception-processing.md#afxthrowoleexception).  
  
 Další informace o výjimky, najdete v článcích [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [výjimky: výjimky OLE](../../mfc/exceptions-ole-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
##  <a name="m_sc"></a>  COleException::m_sc  
 Tento člen dat obsahuje kód OLE stav, který označuje důvod výjimky.  
  
```  
SCODE m_sc;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato proměnná hodnotu nastavuje [afxthrowoleexception –](exception-processing.md#afxthrowoleexception).  
  
 Další informace o `SCODE`, najdete v části [struktura kódy chyb COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]  
  
##  <a name="process"></a>  COleException::Process  
 Volání **proces** – členská funkce přeložit Zachycenou výjimku do OLE stavový kód.  
  
```  
static SCODE PASCAL Process(const CException* pAnyException);
```  
  
### <a name="parameters"></a>Parametry  
 *pAnyException*  
 Ukazatel na Zachycenou výjimku.  
  
### <a name="return-value"></a>Návratová hodnota  
 OLE stavový kód.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato funkce je **statické**.  
  
 Další informace o `SCODE`, najdete v části [struktura kódy chyb COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CALCDRIV](../../visual-cpp-samples.md)   
 [CException – třída](../../mfc/reference/cexception-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



