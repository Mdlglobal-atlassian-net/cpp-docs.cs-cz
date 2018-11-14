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
ms.openlocfilehash: 9d0ffba2e8b682a33dc435b0968c59844a858c72
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524934"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver – třída

implementuje na straně klienta automatizaci OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDispatchDriver
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|Vytvoří `COleDispatchDriver` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Připojí `IDispatch` připojení `COleDispatchDriver` objektu.|
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Vytvoří `IDispatch` připojení a připojí ho k `COleDispatchDriver` objektu.|
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Odpojí `IDispatch` připojení bez uvolnění ho.|
|[COleDispatchDriver::GetProperty](#getproperty)|Získá vlastnost služby automation.|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Pomocník pro volání metod služby automation.|
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Verze `IDispatch` připojení.|
|[COleDispatchDriver::SetProperty](#setproperty)|Nastaví vlastnost služby automation.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[COleDispatchDriver::operator =](#operator_eq)|Zkopíruje zdrojovou hodnotou do `COleDispatchDriver` objektu.|
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|Přistupuje k podkladovým `IDispatch` ukazatele.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Určuje, jestli se má uvolnit `IDispatch` během `ReleaseDispatch` nebo zničení objektu.|
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Označuje ukazatel `IDispatch` rozhraní připojené k tomuto `COleDispatchDriver`.|

## <a name="remarks"></a>Poznámky

`COleDispatchDriver` nemá základní třídu.

Rozhraní odbavení OLE poskytují přístup k metodám a vlastnostem objektu. Členské funkce `COleDispatchDriver` připojení, odpojení, vytvořit a release odeslání připojení typu `IDispatch`. Další členské funkce používají seznamy argumentů proměnných pro zjednodušení volání `IDispatch::Invoke`.

Tato třída je možné přímo, ale obecně se používá pouze pomocí třídy vytvořené pomocí průvodce Přidat třídu. Když vytvoříte nové třídy jazyka C++ pomocí importu knihovny typů, nové třídy jsou odvozeny z `COleDispatchDriver`.

Další informace o používání `COleDispatchDriver`, naleznete v následujících článcích:

- [Klienti automatizace](../../mfc/automation-clients.md)

- [Automatizační servery](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`COleDispatchDriver`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

##  <a name="attachdispatch"></a>  COleDispatchDriver::AttachDispatch

Volání `AttachDispatch` členská funkce se připojit `IDispatch` ukazatel `COleDispatchDriver` objektu. Další informace najdete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Ukazatel na OLE `IDispatch` objektu, který chcete připojit k `COleDispatchDriver` objektu.

*bAutoRelease*<br/>
Určuje, zda od odeslání uvolnit, když tento objekt dostane mimo rozsah.

### <a name="remarks"></a>Poznámky

Tato funkce uvolní všechny `IDispatch` ukazatel, který je již připojen k `COleDispatchDriver` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

##  <a name="coledispatchdriver"></a>  COleDispatchDriver::COleDispatchDriver

Vytvoří `COleDispatchDriver` objektu.

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Ukazatel na OLE `IDispatch` objektu, který chcete připojit k `COleDispatchDriver` objektu.

*bAutoRelease*<br/>
Určuje, zda od odeslání uvolnit, když tento objekt dostane mimo rozsah.

*dispatchSrc*<br/>
Odkaz na existující `COleDispatchDriver` objektu.

### <a name="remarks"></a>Poznámky

Formulář `COleDispatchDriver`( `LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **TRUE**) se připojí [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) rozhraní.

Formulář `COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) zkopíruje existující `COleDispatchDriver` objektu a zvýší počet odkazů.

Formulář `COleDispatchDriver`() vytvoří `COleDispatchDriver` objektu, ale nepřipojí `IDispatch` rozhraní. Před použitím `COleDispatchDriver`() bez argumentů, je vhodné připojit se `IDispatch` buď pomocí [COleDispatchDriver::CreateDispatch](#createdispatch) nebo [COleDispatchDriver::AttachDispatch](#attachdispatch). Další informace najdete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](#createdispatch).

##  <a name="createdispatch"></a>  COleDispatchDriver::CreateDispatch

Vytvoří [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) objektu rozhraní a připojí ho k `COleDispatchDriver` objektu.

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*identifikátor CLSID*<br/>
ID třídy `IDispatch` objekt připojení, který se má vytvořit.

*pError*<br/>
Ukazatel na objekt výjimky OLE, který bude obsahovat stavový kód, který je výsledkem vytvoření.

*lpszProgID*<br/>
Ukazatel na programový identifikátor, jako je například "Excel.Document.5", automatizační objekt, pro který má být vytvořen objekt odeslání.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu; nenulovou hodnotu. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

##  <a name="detachdispatch"></a>  COleDispatchDriver::DetachDispatch

Odpojí aktuální `IDispatch` připojení z tohoto objektu.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dříve připojené OLE `IDispatch` objektu.

### <a name="remarks"></a>Poznámky

`IDispatch` Neuvolní.

Další informace o typu LPDISPATCH najdete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

##  <a name="getproperty"></a>  COleDispatchDriver::GetProperty

Získá objekt vlastnost určenou *dwDispID*.

```
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Určuje vlastnost, která se má načíst.

*vtProp*<br/>
Určuje vlastnost, která se má načíst. Možné hodnoty najdete v části poznámky [COleDispatchDriver::InvokeHelper](#invokehelper).

*pvProp*<br/>
Adresa proměnné, která se zobrazí hodnotu vlastnosti. Musí odpovídat typu určeného *vtProp*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

##  <a name="invokehelper"></a>  COleDispatchDriver::InvokeHelper

Volání metody objektu nebo vlastnost určenou *dwDispID*, v rámci určeného *wFlags*.

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
Určuje metodu nebo vlastnost má být volána.

*wFlags*<br/>
Příznaky popisující kontext volání `IDispatch::Invoke`. . Seznam možných hodnot, najdete v článku *wFlags* parametr [IDispatch::Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) v sadě Windows SDK.

*vtRet*<br/>
Určuje typ vrácené hodnoty. Možné hodnoty najdete v části poznámky.

*pvRet*<br/>
Adresa proměnné, která bude přijímat hodnoty vlastnosti nebo návratovou hodnotu. Musí odpovídat typu určeného *vtRet*.

*pbParamInfo*<br/>
Ukazatel na řetězec zakončený hodnotou null bajtů určující typy parametrů za *pbParamInfo*.

*...*<br/>
Proměnné seznam parametrů typů uvedených v *pbParamInfo*.

### <a name="remarks"></a>Poznámky

*PbParamInfo* parametr určuje typy parametry předané do metody nebo vlastnosti. Proměnné seznam argumentů, které je reprezentována **...**  v syntaxi deklarace.

Možné hodnoty pro *vtRet* argument pocházejí ze výčet VARENUM. Možné hodnoty jsou následující:

|Symbol|Návratový typ|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**DATUM**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**BOOL**|
|VT_VARIANT|**VARIANT**|
|VT_UNKNOWN|LPUNKNOWN|

*PbParamInfo* argument je místo oddělený seznam **VTS_** konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne středníky), určuje seznam parametrů funkce. Možné hodnoty jsou seřazeny [EVENT_CUSTOM](event-maps.md#event_custom) – makro.

Tato funkce převede parametry VARIANTARG hodnoty a potom vyvolá [IDispatch::Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) metody. Pokud volání `Invoke` selže, tato funkce vyvolá výjimku. Pokud SCODE (stavový kód) vrácené `IDispatch::Invoke` DISP_E_EXCEPTION, je tato funkce vyvolá [coleexception –](../../mfc/reference/coleexception-class.md) objektu; v opačném případě vyvolá [coledispatchexception –](../../mfc/reference/coledispatchexception-class.md).

Další informace najdete v tématu [VARIANTARG](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch::Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke), a [struktury z modelu COM chybové kódy](/windows/desktop/com/structure-of-com-error-codes) ve Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](#createdispatch).

##  <a name="m_bautorelease"></a>  COleDispatchDriver::m_bAutoRelease

Při hodnotě TRUE se objekt COM přistupuje [m_lpDispatch](#m_lpdispatch) se automaticky vydá při [ReleaseDispatch](#releasedispatch) se nazývá nebo kdy to `COleDispatchDriver` objekt zničen.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `m_bAutoRelease` nastavena na hodnotu TRUE v konstruktoru.

Další informace o uvolnění objektů modelu COM, naleznete v tématu [implementace počítání odkazů](/windows/desktop/com/implementing-reference-counting) a [IUnknown::Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

##  <a name="m_lpdispatch"></a>  COleDispatchDriver::m_lpDispatch

Ukazatel `IDispatch` rozhraní připojené k tomuto `COleDispatchDriver`.

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Poznámky

`m_lpDispatch` Datový člen je veřejná proměnná typu LPDISPATCH.

Další informace najdete v tématu [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver::AttachDispatch](#attachdispatch).

##  <a name="operator_eq"></a>  COleDispatchDriver::operator =

Zkopíruje zdrojovou hodnotou do `COleDispatchDriver` objektu.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*dispatchSrc*<br/>
Ukazatel na existující `COleDispatchDriver` objektu.

##  <a name="operator_lpdispatch"></a>  COleDispatchDriver::operator LPDISPATCH

Přistupuje k podkladovým `IDispatch` ukazatel `COleDispatchDriver` objektu.

```
operator LPDISPATCH();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

##  <a name="releasedispatch"></a>  COleDispatchDriver::ReleaseDispatch

Verze `IDispatch` připojení. Další informace najdete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```
void ReleaseDispatch();
```

### <a name="remarks"></a>Poznámky

Pokud automatické vydání je nastavená pro toto připojení, tato funkce volá `IDispatch::Release` před uvolněním rozhraní.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleDispatchDriver::AttachDispatch](#attachdispatch).

##  <a name="setproperty"></a>  COleDispatchDriver::SetProperty

Nastaví vlastnost objektu OLE určenou *dwDispID*.

```
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Určuje vlastnost, která má být nastavena.

*vtProp*<br/>
Určuje typ vlastnosti, která má být nastavena. Možné hodnoty najdete v části poznámky [COleDispatchDriver::InvokeHelper](#invokehelper).

*...*<br/>
Jeden parametr typu určeného *vtProp*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC CALCDRIV](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC acdual –](../../visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
