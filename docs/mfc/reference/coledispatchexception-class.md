---
title: Třída COleDispatchException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed492198c5c667fa1ffadcaa9a3bcc0461c16d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="coledispatchexception-class"></a>COleDispatchException – třída
Zpracovává výjimky, které jsou specifické pro OLE `IDispatch` rozhraní, které je klíčovou součástí automatizace OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDispatchException : public CException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Kontext nápovědy došlo k chybě.|  
|[COleDispatchException::m_strDescription](#m_strdescription)|Slovní popis chyby.|  
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Soubor pro použití s nápovědy `m_dwHelpContext`.|  
|[COleDispatchException::m_strSource](#m_strsource)|Aplikace, které vygenerovalo výjimku.|  
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-určitý kód chyby.|  
  
## <a name="remarks"></a>Poznámky  
 Jako další výjimky třídy odvozené od `CException` základní třídy, `COleDispatchException` lze použít s **THROW**, `THROW_LAST`, **zkuste**, **CATCH**, `AND_CATCH`, a `END_CATCH` makra.  
  
 Obecně platí, by měly volat [afxthrowoledispatchexception –](exception-processing.md#afxthrowoledispatchexception) k vytvoření a throw `COleDispatchException` objektu.  
  
 Další informace o výjimky, najdete v článcích [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [výjimky: výjimky OLE](../../mfc/exceptions-ole-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleDispatchException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
##  <a name="m_dwhelpcontext"></a>  COleDispatchException::m_dwHelpContext  
 Identifikuje kontextu Nápověda v nápovědě aplikace (. Soubor HLP).  
  
```  
DWORD m_dwHelpContext;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen se nastavuje pomocí funkce [afxthrowoledispatchexception –](exception-processing.md#afxthrowoledispatchexception) kdy je vyvolána výjimka.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_strdescription"></a>  COleDispatchException::m_strDescription  
 Obsahuje popis ústní chyby, jako je například "Disk plný."  
  
```  
CString m_strDescription;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen se nastavuje pomocí funkce [afxthrowoledispatchexception –](exception-processing.md#afxthrowoledispatchexception) kdy je vyvolána výjimka.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_strhelpfile"></a>  COleDispatchException::m_strHelpFile  
 Rozhraní framework vyplní tento řetězec s názvem souboru nápovědy aplikace.  
  
```  
CString m_strHelpFile;  
```  
  
##  <a name="m_strsource"></a>  COleDispatchException::m_strSource  
 Rozhraní framework vyplní tento řetězec s názvem aplikace, které vygenerovalo výjimku.  
  
```  
CString m_strSource;  
```  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_wcode"></a>  COleDispatchException::m_wCode  
 Obsahuje kód chyby specifický pro vaši aplikaci.  
  
```  
WORD m_wCode;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen se nastavuje pomocí funkce [afxthrowoledispatchexception –](exception-processing.md#afxthrowoledispatchexception) kdy je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CALCDRIV](../../visual-cpp-samples.md)   
 [CException – třída](../../mfc/reference/cexception-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDispatchDriver – třída](../../mfc/reference/coledispatchdriver-class.md)   
 [COleException – třída](../../mfc/reference/coleexception-class.md)
