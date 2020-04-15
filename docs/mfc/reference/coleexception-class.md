---
title: COleException – třída
ms.date: 11/04/2016
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
ms.openlocfilehash: 737c9e669990f4de6ae18cdc7662c131ad61516f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375013"
---
# <a name="coleexception-class"></a>COleException – třída

Představuje podmínku výjimky související s operací OLE.

## <a name="syntax"></a>Syntaxe

```
class COleException : public CException
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleException::Process](#process)|Přeloží zachycenou výjimku do návratového kódu OLE.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|Obsahuje stavový kód, který označuje důvod výjimky.|

## <a name="remarks"></a>Poznámky

Třída `COleException` obsahuje veřejný datový člen, který obsahuje stavový kód označující důvod výjimky.

Obecně byste neměli vytvářet `COleException` objekt přímo; místo toho byste měli volat [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Další informace o výjimkách naleznete v článcích [Zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [Výjimky: Ole Výjimky](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="coleexceptionm_sc"></a><a name="m_sc"></a>COleException::m_sc

Tento datový člen obsahuje stavový kód OLE, který označuje důvod výjimky.

```
SCODE m_sc;
```

### <a name="remarks"></a>Poznámky

Hodnota této proměnné je nastavena [afxThrowOleException](exception-processing.md#afxthrowoleexception).

Další informace o kódu SCODE naleznete [v tématu Struktura kódů chyb COM](/windows/win32/com/structure-of-com-error-codes) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

## <a name="coleexceptionprocess"></a><a name="process"></a>COleException::Process

Volání **process** členské funkce přeložit zachycené výjimky do stavového kódu OLE.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Parametry

*pAnyException*<br/>
Ukazatel na výjimku zachycené.

### <a name="return-value"></a>Návratová hodnota

Stavový kód OLE.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Tato funkce je **statická**.

Další informace o kódu SCODE naleznete [v tématu Struktura kódů chyb COM](/windows/win32/com/structure-of-com-error-codes) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [cOleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Viz také

[Vzorek knihovny MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
