---
title: Rozhraní IAxWinAmbientDispatchEx
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: f4816846801e388619db62998ec979a1100916ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329983"
---
# <a name="iaxwinambientdispatchex-interface"></a>Rozhraní IAxWinAmbientDispatchEx

Toto rozhraní implementuje doplňkové vlastnosti okolí pro hostovaný ovládací prvek.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|Tato metoda je volána k doplnění výchozí rozhraní vlastnosti okolí s uživatelem definované rozhraní.|

## <a name="remarks"></a>Poznámky

Toto rozhraní zahrňte do aplikací knihovny ATL, které jsou staticky propojeny s knihovnou ATL a hostují ovládací prvky ActiveX, zejména ovládací prvky ActiveX, které mají vlastnosti okolí. Nezahrnutí tohoto rozhraní vygeneruje toto tvrzení: "Zapomněli jste předat LIBID ccommodule::Init"

Toto rozhraní je vystaveno ovládacím objektům ActiveX společnosti ATL. Odvozeno z [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), přidá metodu, `IAxWinAmbientDispatchEx` která umožňuje doplnit rozhraní vlastností okolí poskytované ATL s jedním z vašich vlastních.

<xref:System.Windows.Forms.AxHost>se pokusí načíst `IAxWinAmbientDispatch` informace `IAxWinAmbientDispatchEx` o typu a z knihovny typů, která obsahuje kód.

Pokud odkazujete na knihovnu ATL90.dll, **AXHost** načte informace o typu z knihovny typů v knihovně DLL.

Další podrobnosti najdete v [tématu Hostování ovládacích prvků ActiveX pomocí služby ATL AXHost.](../../atl/hosting-activex-controls-using-atl-axhost.md)

## <a name="requirements"></a>Požadavky

Definice tohoto rozhraní je k dispozici v několika formulářích, jak je znázorněno v následující tabulce.

|Typ definice|File|
|---------------------|----------|
|Idl|atliface.idl|
|Knihovna typů|Soubor ATL.dll|
|C++|atliface.h (také součástí ATLBase.h)|

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Tato metoda je volána k doplnění výchozí rozhraní vlastnosti okolí s uživatelem definované rozhraní.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pOdeslání*<br/>
Ukazatel na nové rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Při `SetAmbientDispatch` volání s ukazatelem na nové rozhraní, toto nové rozhraní se použije k vyvolání všechny vlastnosti nebo metody, které jsou požadovány hostované hostovanou ovládacího prvku, pokud tyto vlastnosti již nejsou k dispozici [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>Viz také

[Rozhraní IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)
