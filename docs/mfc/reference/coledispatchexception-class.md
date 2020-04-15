---
title: Třída COleDispatchException
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
ms.openlocfilehash: 4572b639b757569d8e3cfa731f99c123762f3900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375067"
---
# <a name="coledispatchexception-class"></a>Třída COleDispatchException

Zpracovává výjimky specifické pro `IDispatch` rozhraní OLE, které je klíčovou součástí automatizace OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDispatchException : public CException
```

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Kontext nápovědy pro chybu.|
|[COleDispatchException::m_strDescription](#m_strdescription)|Slovní popis chyby.|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Soubor nápovědy, `m_dwHelpContext`který chcete použít s .|
|[COleDispatchException::m_strSource](#m_strsource)|Aplikace, která vygenerovala výjimku.|
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-specifický kód chyby.|

## <a name="remarks"></a>Poznámky

Stejně jako ostatní třídy `CException` výjimek `COleDispatchException` odvozené ze základní třídy lze použít s makry THROW, THROW_LAST, TRY, CATCH, AND_CATCH a END_CATCH.

Obecně byste měli volat [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) k `COleDispatchException` vytvoření a vyvolání objektu.

Další informace o výjimkách naleznete v článcích [Zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [Výjimky: Ole Výjimky](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="coledispatchexceptionm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>COleDispatchException::m_dwHelpContext

Identifikuje kontext nápovědy v nápovědě aplikace (. HLP).

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>Poznámky

Tento člen je nastaven funkcí [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) při vyvolání výjimky.

### <a name="example"></a>Příklad

  Viz příklad [cOleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_strdescription"></a><a name="m_strdescription"></a>COleDispatchException::m_strDescription

Obsahuje popis slovní chyby, například "Disk je plný".

```
CString m_strDescription;
```

### <a name="remarks"></a>Poznámky

Tento člen je nastaven funkcí [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) při vyvolání výjimky.

### <a name="example"></a>Příklad

  Viz příklad [cOleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_strhelpfile"></a><a name="m_strhelpfile"></a>COleDispatchException::m_strHelpFile

Rozhraní framework vyplní tento řetězec názvem souboru nápovědy aplikace.

```
CString m_strHelpFile;
```

## <a name="coledispatchexceptionm_strsource"></a><a name="m_strsource"></a>COleDispatchException::m_strSource

Rozhraní framework vyplní tento řetězec s názvem aplikace, která vygenerovala výjimku.

```
CString m_strSource;
```

### <a name="example"></a>Příklad

  Viz příklad [cOleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_wcode"></a><a name="m_wcode"></a>COleDispatchException::m_wCode

Obsahuje kód chyby specifický pro vaši aplikaci.

```
WORD m_wCode;
```

### <a name="remarks"></a>Poznámky

Tento člen je nastaven funkcí [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) při vyvolání výjimky.

## <a name="see-also"></a>Viz také

[Vzorek knihovny MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDispatchDriver – třída](../../mfc/reference/coledispatchdriver-class.md)<br/>
[COleException – třída](../../mfc/reference/coleexception-class.md)
