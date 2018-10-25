---
title: Coleexception – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 2705a1889e7b9c9c0960cce45b8dc7b411e16982
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060999"
---
# <a name="coleexception-class"></a>Coleexception – třída

Představuje podmínku výjimky vztahující se k operaci OLE.

## <a name="syntax"></a>Syntaxe

```
class COleException : public CException
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleException::Process](#process)|Přeloží zachycené výjimky do návratový kód OLE.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|Obsahuje kód stavu, který označuje důvod výjimky.|

## <a name="remarks"></a>Poznámky

`COleException` Třída zahrnuje data veřejného člena, který obsahuje stavový kód označující důvod výjimky.

Obecně platí, nevytvářejte `COleException` objektu přímo; místo toho byste měli volat [afxthrowoleexception –](exception-processing.md#afxthrowoleexception).

Další informace o výjimkách, najdete v článcích [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [výjimky: výjimky OLE](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

##  <a name="m_sc"></a>  COleException::m_sc

Tomuto datovému členu obsahuje OLE stavový kód, který označuje důvod výjimky.

```
SCODE m_sc;
```

### <a name="remarks"></a>Poznámky

Hodnota této proměnné je nastavena [afxthrowoleexception –](exception-processing.md#afxthrowoleexception).

Další informace o SCODE najdete v tématu [struktura kódy chyb COM](/windows/desktop/com/structure-of-com-error-codes) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

##  <a name="process"></a>  COleException::Process

Volání **procesu** členské funkce pro převod zachycené výjimky do OLE stavový kód.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Parametry

*pAnyException*<br/>
Ukazatel na zachycené výjimky.

### <a name="return-value"></a>Návratová hodnota

OLE stavový kód.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato funkce je **statické**.

Další informace o SCODE najdete v tématu [struktura kódy chyb COM](/windows/desktop/com/structure-of-com-error-codes) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC CALCDRIV](../../visual-cpp-samples.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

