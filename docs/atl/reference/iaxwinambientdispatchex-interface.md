---
title: Iaxwinambientdispatchex – rozhraní
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: 638152d8c49bd20742a586bc665efcdb662b6f3a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413885"
---
# <a name="iaxwinambientdispatchex-interface"></a>Iaxwinambientdispatchex – rozhraní

Toto rozhraní implementuje dodatečné vlastnosti prostředí pro hostované ovládací prvek.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|Tato metoda je volána k doplnění rozhraní vedlejší vlastnost výchozí uživatelské rozhraní.|

## <a name="remarks"></a>Poznámky

Toto rozhraní zahrňte knihovny ATL aplikace, které jsou staticky propojené knihovny ATL a hostitele – ovládací prvky ActiveX, zejména – ovládací prvky ActiveX, které mají vlastnosti prostředí. Toto rozhraní není včetně vygeneruje tento kontrolní výraz: "Zapomněli jste LIBID předat v: CComModule::Init"

Toto rozhraní je zveřejněný prostřednictvím ovládací prvek ActiveX knihovny ATL pro hostování objektů. Odvozené od [iaxwinambientdispatch –](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` přidá metodu, která umožňuje doplnit rozhraní vedlejší vlastnost poskytované ATL s vlastním.

<xref:System.Windows.Forms.AxHost> pokusí se načíst informace o typu o `IAxWinAmbientDispatch` a `IAxWinAmbientDispatchEx` z knihovny typů, která obsahuje kód.

Pokud se připojujete k ATL90.dll, **AXHost** načte informace o typu z knihovny typů v knihovně DLL.

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) další podrobnosti.

## <a name="requirements"></a>Požadavky

Definice toto rozhraní není k dispozici v různých formách, jak je znázorněno v následující tabulce.

|Typ definice|Soubor|
|---------------------|----------|
|IDL|atliface.IDL|
|Knihovny typů|ATL.dll|
|C++|atliface.h (také součástí ATLBase.h)|

##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch

Tato metoda je volána k doplnění rozhraní vedlejší vlastnost výchozí uživatelské rozhraní.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatch*<br/>
Ukazatel na nové rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Když `SetAmbientDispatch` se volá s ukazatelem na nové rozhraní, bude toto nové rozhraní použít k vyvolání žádné vlastnosti nebo metody požádán o hostovaného ovládacího prvku, pokud tyto vlastnosti nejsou ještě součástí [iaxwinambientdispatch –](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>Viz také:

[IAxWinAmbientDispatch – rozhraní](../../atl/reference/iaxwinambientdispatch-interface.md)
