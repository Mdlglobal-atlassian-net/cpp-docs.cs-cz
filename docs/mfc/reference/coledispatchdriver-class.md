---
title: COleDispatchDriver – třída
ms.date: 11/04/2016
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
helpviewer_keywords:
- COleDispatchDriver [MFC], COleDispatchDriver
- COleDispatchDriver [MFC], AttachDispatch
- COleDispatchDriver [MFC], CreateDispatch
- COleDispatchDriver [MFC], DetachDispatch
- COleDispatchDriver [MFC], GetProperty
- COleDispatchDriver [MFC], InvokeHelper
- COleDispatchDriver [MFC], ReleaseDispatch
- COleDispatchDriver [MFC], SetProperty
- COleDispatchDriver [MFC], m_bAutoRelease
- COleDispatchDriver [MFC], m_lpDispatch
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
ms.openlocfilehash: c22097c3a686857a6a5698033b7395c5d15f2570
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366083"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver – třída

Implementuje straně klienta automatizace OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDispatchDriver
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|Vytvoří `COleDispatchDriver` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Připojí `IDispatch` se k `COleDispatchDriver` objektu.|
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Vytvoří `IDispatch` připojení a připojí ho `COleDispatchDriver` k objektu.|
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Odpojí `IDispatch` připojení, aniž by ho uvolnil.|
|[COleDispatchDriver::GetProperty](#getproperty)|Získá vlastnost automatizace.|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Pomocník pro volání metod automatizace.|
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Uvolní `IDispatch` připojení.|
|[COleDispatchDriver::SetProperty](#setproperty)|Nastaví vlastnost automatizace.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[COleDispatchDriver::operátor =](#operator_eq)|Zkopíruje zdrojovou `COleDispatchDriver` hodnotu do objektu.|
|[COleDispatchDriver::operátor LPDISPATCH](#operator_lpdispatch)|Přistupuje k podkladovému `IDispatch` ukazateli.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Určuje, zda má `IDispatch` `ReleaseDispatch` být během nebo zničení objektu vydáno.|
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Označuje ukazatel na `IDispatch` rozhraní připojené `COleDispatchDriver`k tomuto .|

## <a name="remarks"></a>Poznámky

`COleDispatchDriver`nemá základní třídu.

Rozhraní OLE odeslání poskytují přístup k metodám a vlastnostem objektu. Členské funkce `COleDispatchDriver` připojit, odpojit, vytvořit a uvolnit `IDispatch`odeslání připojení typu . Jiné členské funkce používají seznamy `IDispatch::Invoke`proměnných argumentů ke zjednodušení volání .

Tuto třídu lze použít přímo, ale obecně se používá pouze třídy vytvořené průvodcem Přidat třídu. Při vytváření nových tříd jazyka C++ importem knihovny typů `COleDispatchDriver`jsou nové třídy odvozeny z aplikace .

Další informace o `COleDispatchDriver`používání naleznete v následujících článcích:

- [Klienti automatizace](../../mfc/automation-clients.md)

- [Automatizační servery](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`COleDispatchDriver`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a>COleDispatchDriver::AttachDispatch

Volání `AttachDispatch` členské funkce připojit `IDispatch` ukazatel `COleDispatchDriver` k objektu. Další informace naleznete [v tématu Implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Ukazatel na `IDispatch` objekt OLE, který `COleDispatchDriver` má být připojen k objektu.

*bAutoRelease*<br/>
Určuje, zda má být odeslání uvolněno, když tento objekt přejde mimo rozsah.

### <a name="remarks"></a>Poznámky

Tato funkce uvolní `IDispatch` všechny ukazatele, které `COleDispatchDriver` je již připojenk objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a>COleDispatchDriver::COleDispatchDriver

Vytvoří `COleDispatchDriver` objekt.

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Ukazatel na `IDispatch` objekt OLE, který `COleDispatchDriver` má být připojen k objektu.

*bAutoRelease*<br/>
Určuje, zda má být odeslání uvolněno, když tento objekt přejde mimo rozsah.

*dispečinkSrc*<br/>
Odkaz na `COleDispatchDriver` existující objekt.

### <a name="remarks"></a>Poznámky

Formulář `COleDispatchDriver`( `LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **TRUE**) spojuje rozhraní [IDispatch.](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

Formulář `COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) `COleDispatchDriver` zkopíruje existující objekt a zvýrazní počet odkazů.

Formulář `COleDispatchDriver`( ) `COleDispatchDriver` vytvoří objekt, ale `IDispatch` nepřipojí rozhraní. Před `COleDispatchDriver`použitím ( ) bez argumentů `IDispatch` byste se k němu měli připojit pomocí [cOleDispatchDriver::CreateDispatch](#createdispatch) nebo [COleDispatchDriver::AttachDispatch](#attachdispatch). Další informace naleznete [v tématu Implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Příklad

  Viz příklad [cOleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a>COleDispatchDriver::CreateDispatch

Vytvoří objekt rozhraní [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) a připojí `COleDispatchDriver` jej k objektu.

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
ID třídy `IDispatch` objektu připojení, který má být vytvořen.

*chyba*<br/>
Ukazatel na objekt výjimky OLE, který bude obsahovat stavový kód vyplývající z vytvoření.

*lpszProgID*<br/>
Ukazatel na programový identifikátor, například "Excel.Document.5", objektu automatizace, pro který má být objekt odeslání vytvořen.

### <a name="return-value"></a>Návratová hodnota

Nenulová na úspěch; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a>COleDispatchDriver::DetachDispatch

Odpojí aktuální `IDispatch` připojení od tohoto objektu.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dříve připojený `IDispatch` objekt OLE.

### <a name="remarks"></a>Poznámky

Není `IDispatch` uvolněna.

Další informace o typu LPDISPATCH naleznete v [tématu Implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a>COleDispatchDriver::GetProperty

Získá vlastnost objektu určenou *dwDispID*.

```
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identifikuje vlastnost, která má být načtena.

*vtProp*<br/>
Určuje vlastnost, která má být načtena. Možné hodnoty naleznete v části Poznámky pro [COleDispatchDriver::InvokeHelper](#invokehelper).

*pvProp*<br/>
Adresa proměnné, která obdrží hodnotu vlastnosti. Musí odpovídat typu určenému *vtProp*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a>COleDispatchDriver::InvokeHelper

Volá metodu nebo vlastnost objektu určenou *identifikátorem dwDispID*v kontextu určeném *parametrem wFlags*.

```
void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identifikuje metodu nebo vlastnost, která má být vyvolána.

*wPříznaky*<br/>
Příznaky popisující kontext volání `IDispatch::Invoke`. . Seznam možných hodnot naleznete v parametru *wFlags* v [iDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) v sadě Windows SDK.

*vtRet*<br/>
Určuje typ vrácené hodnoty. Možné hodnoty naleznete v části Poznámky.

*pvRet*<br/>
Adresa proměnné, která obdrží hodnotu vlastnosti nebo vrácenou hodnotu. Musí odpovídat typu určenému *vtRet*.

*pbParamInfo*<br/>
Ukazatel na řetězec bajtů ukončený nulou určující typy parametrů následujících *po pbParamInfo*.

*...*<br/>
Variabilní seznam parametrů, typů určených v *pbParamInfo*.

### <a name="remarks"></a>Poznámky

Parametr *pbParamInfo* určuje typy parametrů předaných metodě nebo vlastnosti. Seznam proměnných argumentů je reprezentován **...** v deklaraci syntaxe.

Možné hodnoty pro argument *vtRet* jsou převzaty z výčtu VARENUM. Možné hodnoty jsou následující:

|Symbol|Návratový typ|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**Datum**|
|VT_BSTR|Bstr|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**Bool**|
|VT_VARIANT|**VARIANT**|
|VT_UNKNOWN|LPUNKNOWN|

Argument *pbParamInfo* je seznam **VTS_** konstant oddělených mezerami. Jedna nebo více těchto hodnot oddělených mezerami (nikoli čárkami) určuje seznam parametrů funkce. Možné hodnoty jsou uvedeny s [EVENT_CUSTOM](event-maps.md#event_custom) makro.

Tato funkce převede parametry na hodnoty VARIANTARG a potom vyvolá metodu [IDispatch::Invoke.](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) Pokud volání `Invoke` nezdaří, tato funkce vyvolá výjimku. Pokud SCODE (stavový kód) vrácena `IDispatch::Invoke` DISP_E_EXCEPTION, tato funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md) objektu; jinak vyvolá [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Další informace naleznete v [tématech VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant), [Implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)a [Structure of COM Error Codes](/windows/win32/com/structure-of-com-error-codes) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [cOleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a>COleDispatchDriver::m_bAutoRelease

Pokud true, objekt COM přistupovat [m_lpDispatch](#m_lpdispatch) bude automaticky uvolněna při `COleDispatchDriver` [ReleaseDispatch](#releasedispatch) je volána nebo při zničení tohoto objektu.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Poznámky

Ve výchozím `m_bAutoRelease` nastavení je v konstruktoru nastavena na hodnotu TRUE.

Další informace o uvolnění objektů MODELU COM naleznete v [tématu Implementace počítání odkazů](/windows/win32/com/implementing-reference-counting) a [IUnknown::Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a>COleDispatchDriver::m_lpDispatch

Ukazatel na `IDispatch` rozhraní připojené k `COleDispatchDriver`tomuto .

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Poznámky

Datový `m_lpDispatch` člen je veřejná proměnná typu LPDISPATCH.

Další informace naleznete v tématu [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [cOleDispatchDriver::AttachDispatch](#attachdispatch).

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a>COleDispatchDriver::operátor =

Zkopíruje zdrojovou `COleDispatchDriver` hodnotu do objektu.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*dispečinkSrc*<br/>
Ukazatel na existující `COleDispatchDriver` objekt.

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a>COleDispatchDriver::operátor LPDISPATCH

Přistupuje k podkladovému `IDispatch` ukazateli objektu. `COleDispatchDriver`

```
operator LPDISPATCH();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a>COleDispatchDriver::ReleaseDispatch

Uvolní `IDispatch` připojení. Další informace naleznete [v tématu Implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```
void ReleaseDispatch();
```

### <a name="remarks"></a>Poznámky

Pokud bylo pro toto připojení nastaveno `IDispatch::Release` automatické vydání, tato funkce volá před uvolněním rozhraní.

### <a name="example"></a>Příklad

  Viz příklad [cOleDispatchDriver::AttachDispatch](#attachdispatch).

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a>COleDispatchDriver::SetProperty

Nastaví vlastnost objektu OLE určenou *identifikátorem dwDispID*.

```
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identifikuje vlastnost, která má být nastavena.

*vtProp*<br/>
Určuje typ vlastnosti, která má být nastavena. Možné hodnoty naleznete v části Poznámky pro [COleDispatchDriver::InvokeHelper](#invokehelper).

*...*<br/>
Jeden parametr typu určeného *vtProp*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Viz také

[Vzorek knihovny MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
