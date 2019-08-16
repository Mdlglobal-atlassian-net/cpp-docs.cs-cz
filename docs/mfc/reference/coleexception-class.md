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
ms.openlocfilehash: 96061f704d9df6cd788e362652b6ed22a7ffa999
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503949"
---
# <a name="coleexception-class"></a>COleException – třída

Představuje podmínku výjimky vztahující se k operaci OLE.

## <a name="syntax"></a>Syntaxe

```
class COleException : public CException
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleException::P rávce](#process)|Přeloží Zachycenou výjimku na návratový kód OLE.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|Obsahuje stavový kód, který označuje důvod výjimky.|

## <a name="remarks"></a>Poznámky

`COleException` Třída zahrnuje veřejný datový člen, který obsahuje stavový kód označující důvod výjimky.

Obecně byste neměli vytvořit `COleException` objekt přímo; místo toho byste měli volat [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Další informace o výjimkách naleznete v článcích [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [výjimky: Výjimky](../../mfc/exceptions-ole-exceptions.md)OLE

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CException –](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="m_sc"></a>COleException::m_sc

Tento datový člen obsahuje stavový kód OLE, který označuje důvod výjimky.

```
SCODE m_sc;
```

### <a name="remarks"></a>Poznámky

Hodnota této proměnné je nastavena hodnotou [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Další informace o Code naleznete v tématu [Struktura kódů chyb modelu COM](/windows/win32/com/structure-of-com-error-codes) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

##  <a name="process"></a>COleException::P rávce

Zavolejte členskou funkci **procesu** pro překlad zachycené výjimky na stavový kód OLE.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Parametry

*pAnyException*<br/>
Ukazatel na Zachycenou výjimku.

### <a name="return-value"></a>Návratová hodnota

Stavový kód OLE.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato funkce je **statická**.

Další informace o Code naleznete v tématu [Struktura kódů chyb modelu COM](/windows/win32/com/structure-of-com-error-codes) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver:: CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Viz také:

[CALCDRIV Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
