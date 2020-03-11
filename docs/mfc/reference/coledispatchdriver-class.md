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
ms.openlocfilehash: fa88147b57b0506f7f9ab96d4a5d2f43fdd75458
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855485"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver – třída

Implementuje stranu klienta automatizace OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDispatchDriver
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDispatchDriver:: COleDispatchDriver](#coledispatchdriver)|Vytvoří objekt `COleDispatchDriver`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDispatchDriver:: AttachDispatch](#attachdispatch)|Připojí `IDispatch` připojení k objektu `COleDispatchDriver`.|
|[COleDispatchDriver:: CreateDispatch](#createdispatch)|Vytvoří `IDispatch` připojení a připojí ho k objektu `COleDispatchDriver`.|
|[COleDispatchDriver::D etachDispatch](#detachdispatch)|Odpojí `IDispatch` připojení, a to bez jeho uvolnění.|
|[COleDispatchDriver:: GetProperty](#getproperty)|Získá vlastnost Automation.|
|[COleDispatchDriver:: InvokeHelper](#invokehelper)|Pomocný objekt pro volání metod automatizace|
|[COleDispatchDriver:: ReleaseDispatch](#releasedispatch)|Uvolní `IDispatch` připojení.|
|[COleDispatchDriver:: SetProperty](#setproperty)|Nastaví vlastnost Automation.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[COleDispatchDriver:: operator =](#operator_eq)|Zkopíruje zdrojovou hodnotu do objektu `COleDispatchDriver`.|
|[COleDispatchDriver:: operator LPDISPATCH](#operator_lpdispatch)|Přistupuje k základnímu ukazateli `IDispatch`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleDispatchDriver:: m_bAutoRelease](#m_bautorelease)|Určuje, zda se má uvolnit `IDispatch` během `ReleaseDispatch` nebo zničení objektu.|
|[COleDispatchDriver:: m_lpDispatch](#m_lpdispatch)|Určuje ukazatel na rozhraní `IDispatch` připojené k tomuto `COleDispatchDriver`.|

## <a name="remarks"></a>Poznámky

`COleDispatchDriver` nemá základní třídu.

Odesílající rozhraní OLE poskytují přístup k metodám a vlastnostem objektu. Členské funkce `COleDispatchDriver` připojit, odpojit, vytvořit a uvolnit Dispatch připojení typu `IDispatch`. Jiné členské funkce používají seznamy argumentů proměnných pro zjednodušení volání `IDispatch::Invoke`.

Tuto třídu lze použít přímo, ale je obecně používána pouze třídami vytvořenými průvodcem přidáním třídy. Když vytváříte nové C++ třídy importem knihovny typů, nové třídy jsou odvozeny z `COleDispatchDriver`.

Další informace o používání `COleDispatchDriver`najdete v následujících článcích:

- [Klienti automatizace](../../mfc/automation-clients.md)

- [Automatizační servery](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`COleDispatchDriver`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="attachdispatch"></a>COleDispatchDriver:: AttachDispatch

Chcete-li připojit ukazatel `IDispatch` k objektu `COleDispatchDriver`, zavolejte členskou funkci `AttachDispatch`. Další informace naleznete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Ukazatel na objekt OLE `IDispatch`, který se má připojit k objektu `COleDispatchDriver`.

*bAutoRelease*<br/>
Určuje, zda má být odeslání uvolněno, když se tento objekt dostane mimo rozsah.

### <a name="remarks"></a>Poznámky

Tato funkce uvolní libovolný `IDispatch` ukazatel, který je již připojen k objektu `COleDispatchDriver`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

##  <a name="coledispatchdriver"></a>COleDispatchDriver:: COleDispatchDriver

Vytvoří objekt `COleDispatchDriver`.

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Ukazatel na objekt OLE `IDispatch`, který se má připojit k objektu `COleDispatchDriver`.

*bAutoRelease*<br/>
Určuje, zda má být odeslání uvolněno, když se tento objekt dostane mimo rozsah.

*dispatchSrc*<br/>
Odkaz na existující objekt `COleDispatchDriver`.

### <a name="remarks"></a>Poznámky

`COleDispatchDriver`formuláře (`LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **true**) připojuje rozhraní [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) .

`COleDispatchDriver`formuláře ( **const**`COleDispatchDriver`& `dispatchSrc`) zkopíruje existující objekt `COleDispatchDriver` a zvýší počet odkazů.

Ve formuláři `COleDispatchDriver`() se vytvoří objekt `COleDispatchDriver`, ale nepřipojí rozhraní `IDispatch`. Před použitím `COleDispatchDriver`() bez argumentů byste k němu měli připojit `IDispatch`, a to buď pomocí [COleDispatchDriver:: CreateDispatch](#createdispatch) , nebo [COleDispatchDriver:: AttachDispatch](#attachdispatch). Další informace naleznete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver:: CreateDispatch](#createdispatch).

##  <a name="createdispatch"></a>COleDispatchDriver:: CreateDispatch

Vytvoří objekt rozhraní [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) a připojí ho k objektu `COleDispatchDriver`.

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*CLSID*<br/>
ID třídy objektu připojení `IDispatch`, který se má vytvořit

*pError*<br/>
Ukazatel na objekt výjimka OLE, který bude obsahovat stavový kód vyplývající z vytvoření.

*lpszProgID*<br/>
Ukazatel na programový identifikátor, jako je například Excel. Document. 5, objektu automatizace, pro který má být vytvořen objekt dispatch.

### <a name="return-value"></a>Návratová hodnota

Nenulové při úspěchu; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

##  <a name="detachdispatch"></a>COleDispatchDriver::D etachDispatch

Odpojí aktuální `IDispatch` připojení od tohoto objektu.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dříve připojený objekt OLE `IDispatch`.

### <a name="remarks"></a>Poznámky

`IDispatch` není uvolněn.

Další informace o typu LPDISPATCH naleznete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

##  <a name="getproperty"></a>COleDispatchDriver:: GetProperty

Získá vlastnost objektu určenou parametrem *dwDispID*.

```
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Určuje vlastnost, která má být načtena.

*vtProp*<br/>
Určuje vlastnost, která má být načtena. Možné hodnoty naleznete v části poznámky pro [COleDispatchDriver:: InvokeHelper](#invokehelper).

*pvProp*<br/>
Adresa proměnné, která bude přijímat hodnotu vlastnosti. Musí odpovídat typu zadanému parametrem *vtProp*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

##  <a name="invokehelper"></a>COleDispatchDriver:: InvokeHelper

Volá metodu objektu nebo vlastnost určenou v *dwDispID*v kontextu určeném parametrem *wFlags*.

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
Určuje metodu nebo vlastnost, která má být vyvolána.

*wFlags*<br/>
Příznaky popisující kontext volání `IDispatch::Invoke`. . Seznam možných hodnot naleznete v parametru *wFlags* v [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) v Windows SDK.

*vtRet*<br/>
Určuje typ vrácené hodnoty. Možné hodnoty najdete v části poznámky.

*pvRet*<br/>
Adresa proměnné, která bude přijímat hodnotu vlastnosti nebo návratovou hodnotu. Musí odpovídat typu zadanému parametrem *vtRet*.

*pbParamInfo*<br/>
Ukazatel na řetězec zakončený hodnotou NULL bajtů, který určuje typy parametrů následující po *pbParamInfo*.

*...*<br/>
Seznam proměnných parametrů typu určených v *pbParamInfo*.

### <a name="remarks"></a>Poznámky

Parametr *pbParamInfo* určuje typy parametrů předaných metodě nebo vlastnosti. Seznam proměnných argumentů je reprezentován **...** v deklaraci syntaxe.

Možné hodnoty argumentu *vtRet* jsou pořízeny z výčtu VarEnum. Možné hodnoty jsou následující:

|Písmeno|Návratový typ|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**KR**|
|VT_DATE|**DATE** (Datum)|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**LOGICK**|
|VT_VARIANT|**VARIANTY**|
|VT_UNKNOWN|LPUNKNOWN|

Argument *pbParamInfo* je seznam oddělený mezerami **VTS_** konstantami. Jedna nebo více těchto hodnot oddělených mezerami (nejedná se o čárky), určuje seznam parametrů funkce. Možné hodnoty jsou uvedeny pomocí makra [EVENT_CUSTOM](event-maps.md#event_custom) .

Tato funkce převede parametry na hodnoty VARIANTARG a poté vyvolá metodu [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) . Pokud volání `Invoke` selže, tato funkce vyvolá výjimku. Pokud je Code (Stavový kód) vrácený `IDispatch::Invoke` DISP_E_EXCEPTION, tato funkce vyvolá objekt [COleException](../../mfc/reference/coleexception-class.md) ; v opačném případě vyvolá výjimku [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Další informace naleznete v tématu [VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant), [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)a [Struktura kódů chyb modelu COM](/windows/win32/com/structure-of-com-error-codes) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver:: CreateDispatch](#createdispatch).

##  <a name="m_bautorelease"></a>COleDispatchDriver:: m_bAutoRelease

Pokud je nastaveno na TRUE, objekt COM, ke kterému se přistupovalo pomocí [m_lpDispatch](#m_lpdispatch) , se automaticky uvolní při volání [ReleaseDispatch](#releasedispatch) nebo při zničení tohoto objektu `COleDispatchDriver`.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je `m_bAutoRelease` v konstruktoru nastaven na hodnotu TRUE.

Další informace o uvolňování objektů COM naleznete v tématu [implementace počítání odkazů](/windows/win32/com/implementing-reference-counting) a [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

##  <a name="m_lpdispatch"></a>COleDispatchDriver:: m_lpDispatch

Ukazatel na rozhraní `IDispatch` připojené k tomuto `COleDispatchDriver`.

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Poznámky

Datový člen `m_lpDispatch` je veřejná proměnná typu LPDISPATCH.

Další informace najdete v tématu věnovaném rozhraní [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver:: AttachDispatch](#attachdispatch).

##  <a name="operator_eq"></a>COleDispatchDriver:: operator =

Zkopíruje zdrojovou hodnotu do objektu `COleDispatchDriver`.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*dispatchSrc*<br/>
Ukazatel na existující objekt `COleDispatchDriver`.

##  <a name="operator_lpdispatch"></a>COleDispatchDriver:: operator LPDISPATCH

Přistupuje k základnímu `IDispatch` ukazateli objektu `COleDispatchDriver`.

```
operator LPDISPATCH();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

##  <a name="releasedispatch"></a>COleDispatchDriver:: ReleaseDispatch

Uvolní `IDispatch` připojení. Další informace najdete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) .

```
void ReleaseDispatch();
```

### <a name="remarks"></a>Poznámky

Pokud bylo pro toto připojení nastaveno automatické vydání, tato funkce volá `IDispatch::Release` před uvolněním rozhraní.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver:: AttachDispatch](#attachdispatch).

##  <a name="setproperty"></a>COleDispatchDriver:: SetProperty

Nastaví vlastnost objektu OLE určenou parametrem *dwDispID*.

```
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Určuje vlastnost, která má být nastavena.

*vtProp*<br/>
Určuje typ vlastnosti, která se má nastavit. Možné hodnoty naleznete v části poznámky pro [COleDispatchDriver:: InvokeHelper](#invokehelper).

*...*<br/>
Jeden parametr typu určený parametrem *vtProp*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Viz také

[CALCDRIV Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[ACDUAL Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
