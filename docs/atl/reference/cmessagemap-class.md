---
title: Třída CMessageMap
ms.date: 11/04/2016
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
ms.openlocfilehash: a822f36d6b6fd49301d8240324e27f0ad9ce52e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326713"
---
# <a name="cmessagemap-class"></a>Třída CMessageMap

Tato třída umožňuje mapy zpráv objektu přístup k jinému objektu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Přistupuje k `CMessageMap`mapě zpráv v odvozené třídě.|

## <a name="remarks"></a>Poznámky

`CMessageMap`je abstraktní základní třída, která umožňuje přístup k mapám zpráv objektu pomocí jiného objektu. Aby objekt vystavit své mapy zpráv, jeho třída `CMessageMap`musí být odvozena z .

ATL `CMessageMap` používá pro podporu obsažených oken a dynamické mapování zpráv řetězení. Například všechny třídy obsahující [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) objekt `CMessageMap`musí být odvozen z . Následující kód je převzat ze vzorku [SUBEDIT.](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) Prostřednictvím [CComControl](../../atl/reference/ccomcontrol-class.md), `CAtlEdit` třída `CMessageMap`automaticky odvozuje od .

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

Vzhledem k tomu, že obsažené okno , `m_EditCtrl`bude `CAtlEdit` používat mapu `CMessageMap`zpráv v obsahující třídy, pochází z .

Další informace o mapách zpráv naleznete v tématu [Mapy zpráv](../../atl/message-maps-atl.md) v článku "Třídy oken ATL".

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="cmessagemapprocesswindowmessage"></a><a name="processwindowmessage"></a>CMessageMap::ProcessWindowMessage

Přistupuje k mapování zpráv identifikované *dwMsgMapID* v `CMessageMap`odvozené třídě.

```
virtual BOOL ProcessWindowMessage(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[v] Popisovač do okna, které přijímá zprávu.

*uMsg*<br/>
[v] Zpráva odeslaná do okna.

*wParam*<br/>
[v] Další informace specifické pro zprávu.

*Lparam*<br/>
[v] Další informace specifické pro zprávu.

*lVýsledek*<br/>
[out] Výsledek zpracování zprávy.

*dwMsgMapID*<br/>
[v] Identifikátor mapy zprávy, která bude zpracovávat zprávu. Výchozí mapa zpráv deklarovaná [s BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)je označena hodnotou 0. Alternativní mapa zpráv deklarovaná [pomocí ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)je identifikována . `msgMapID`

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je zpráva plně zpracována; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Volána procedurou okna [ccontainedwindow](../../atl/reference/ccontainedwindowt-class.md) objektu nebo objektu, který je dynamicky zřetězení na mapu zprávy.

## <a name="see-also"></a>Viz také

[Třída CDynamicChain](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
