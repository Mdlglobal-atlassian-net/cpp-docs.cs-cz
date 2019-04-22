---
title: Coledispatchexception – třída
ms.date: 11/04/2016
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
ms.openlocfilehash: 2d5b9d2a0dc1e716ea8cb20f0d0dcb4c5d765079
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769053"
---
# <a name="coledispatchexception-class"></a>Coledispatchexception – třída

Zpracovává výjimky, které jsou specifické pro OLE `IDispatch` rozhraní, které je klíčovou součástí automatizace OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDispatchException : public CException
```

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Kontextové nápovědy pro chybu.|
|[COleDispatchException::m_strDescription](#m_strdescription)|Popis slovní chyby.|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Soubor pro použití s nápovědy `m_dwHelpContext`.|
|[COleDispatchException::m_strSource](#m_strsource)|Aplikace, která generují výjimku.|
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-určitý kód chyby.|

## <a name="remarks"></a>Poznámky

Stejně jako ostatní výjimky třídy odvozené z `CException` základní třídy, `COleDispatchException` jde použít s THROW, THROW_LAST, TRY, CATCH, AND_CATCH a END_CATCH makra.

Obecně byste měli volat [afxthrowoledispatchexception –](exception-processing.md#afxthrowoledispatchexception) a vytvořte výjimku `COleDispatchException` objektu.

Další informace o výjimkách, najdete v článcích [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [výjimky: OLE – výjimky](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

##  <a name="m_dwhelpcontext"></a>  COleDispatchException::m_dwHelpContext

Identifikuje kontextové nápovědy v nápovědě aplikace (. Soubor HLP).

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>Poznámky

Tento člen je nastavený podle funkce [afxthrowoledispatchexception –](exception-processing.md#afxthrowoledispatchexception) když dojde k výjimce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

##  <a name="m_strdescription"></a>  COleDispatchException::m_strDescription

Obsahuje popis slovní chyby, jako je například "Disk je plný."

```
CString m_strDescription;
```

### <a name="remarks"></a>Poznámky

Tento člen je nastavený podle funkce [afxthrowoledispatchexception –](exception-processing.md#afxthrowoledispatchexception) když dojde k výjimce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

##  <a name="m_strhelpfile"></a>  COleDispatchException::m_strHelpFile

Rozhraní framework vyplní tento řetězec s názvem souboru nápovědy aplikace.

```
CString m_strHelpFile;
```

##  <a name="m_strsource"></a>  COleDispatchException::m_strSource

Rozhraní framework vyplní tento řetězec s názvem aplikace, která generovala výjimku.

```
CString m_strSource;
```

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

##  <a name="m_wcode"></a>  COleDispatchException::m_wCode

Obsahuje kód chyby, která je specifická pro vaši aplikaci.

```
WORD m_wCode;
```

### <a name="remarks"></a>Poznámky

Tento člen je nastavený podle funkce [afxthrowoledispatchexception –](exception-processing.md#afxthrowoledispatchexception) když dojde k výjimce.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDispatchDriver – třída](../../mfc/reference/coledispatchdriver-class.md)<br/>
[COleException – třída](../../mfc/reference/coleexception-class.md)
