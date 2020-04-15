---
title: Třída CAxDialogImpl
ms.date: 11/04/2016
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
ms.openlocfilehash: d8e60a817d197f67c14318a7d50ddf796e570142
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318731"
---
# <a name="caxdialogimpl-class"></a>Třída CAxDialogImpl

Tato třída implementuje dialogové okno (modální nebo nemodální), které je hostitelem ovládacích prvků ActiveX.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `CAxDialogImpl`.

*TBase*<br/>
Třída základního `CDialogImplBaseT`okna pro .

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Volání této metody poradit nebo unadvise všechny položky v mapě mapy jímky objektu.|
|[CAxDialogImpl::Vytvořit](#create)|Volání této metody k vytvoření nemodální dialogové okno.|
|[CAxDialogImpl::DestroyOkno](#destroywindow)|Volání této metody zničit nemodální dialogové okno.|
|[CAxDialogImpl::DoModální](#domodal)|Volání této metody k vytvoření modální dialogové okno.|
|[CAxDialogImpl::EndDialog](#enddialog)|Volání této metody zničit modální dialogové okno.|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Volání této metody získat ukazatel `DialogProc` na funkci zpětného volání.|
|[CAxDialogImpl::GetIDD](#getidd)|Volání této metody k získání ID prostředku šablony dialogu|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Volání této metody k určení, zda je zpráva určena pro toto dialogové okno a pokud je, zpracování zprávy.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CAxDialogImpl::m_bModal](#m_bmodal)|Proměnná, která existuje pouze v sestaveních ladění a je nastavena na hodnotu true, pokud je dialogové okno modální.|

## <a name="remarks"></a>Poznámky

`CAxDialogImpl`umožňuje vytvořit modální nebo nemodální dialogové okno. `CAxDialogImpl`Poskytuje proceduru dialogového okna, která používá výchozí mapování zpráv k přesměrování zpráv na příslušné obslužné rutiny.

`CAxDialogImpl`pochází z `CDialogImplBaseT`, který zase pochází z *TBase* (ve výchozím nastavení, `CWindow`) a `CMessageMap`.

Vaše třída musí definovat člen IDD, který určuje ID prostředku šablony dialogu. Například přidání objektu dialogového okna KNIHOVNY ATL pomocí dialogového okna **Přidat třídu** automaticky přidá do vaší třídy následující řádek:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

kde `MyDialog` je **krátký název** zadaný v Průvodci dialogem ATL.

Další informace naleznete [v tématu Implementace dialogového okna.](../../atl/implementing-a-dialog-box.md)

Všimněte si, že ovládací prvek ActiveX v modálním dialogovém okně vytvořeném pomocí `CAxDialogImpl` nepodporuje klávesy akcelerátoru. Chcete-li podporovat klávesy akcelerátoru v dialogovém okně vytvořeném pomocí `CAxDialogImpl`aplikace , vytvořte nemodální dialogové okno a pomocí vlastní smyčky zpráv použijte [caxDialogImpl::IsDialogMessage](#isdialogmessage) poté, co se z fronty zobrazí zpráva ke zpracování klíče akcelerátoru.

Další informace `CAxDialogImpl`naleznete v [nejčastějších dotazech](../../atl/atl-control-containment-faq.md)k omezení řízení řízení atl .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="caxdialogimpladvisesinkmap"></a><a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap

Volání této metody poradit nebo unadvise všechny položky v mapě mapy jímky objektu.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bPoradit*<br/>
Nastavte na hodnotu true, pokud mají být doporučeny všechny položky jímky; false, pokud všechny položky jímky mají být nedoporučeno.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="caxdialogimplcreate"></a><a name="create"></a>CAxDialogImpl::Vytvořit

Volání této metody k vytvoření nemodální dialogové okno.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
[v] Popisovač do okna vlastníka.

*dwInitParam*<br/>
[v] Určuje hodnotu, která má být předávána dialogovému oknu v parametru *lParam* WM_INITDIALOG zprávy.

*RECT&*<br/>
Tento parametr není používán. Tento parametr je `CComControl`předán .

### <a name="return-value"></a>Návratová hodnota

Úchyt k nově vytvořenému dialogovému oknu.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je `CAxDialogImpl` automaticky připojeno k objektu. Chcete-li vytvořit modální dialogové okno, volejte [DoModal](#domodal).

Druhé přepsání je k dispozici pouze proto, aby dialogová okna mohla být použita s [CComControl](../../atl/reference/ccomcontrol-class.md).

## <a name="caxdialogimpldestroywindow"></a><a name="destroywindow"></a>CAxDialogImpl::DestroyOkno

Volání této metody zničit nemodální dialogové okno.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je okno úspěšně zničeno; jinak FALSE.

### <a name="remarks"></a>Poznámky

Nevolejte `DestroyWindow` zničit modální dialogové okno. Místo toho volání [EndDialog.](#enddialog)

## <a name="caxdialogimpldomodal"></a><a name="domodal"></a>CAxDialogImpl::DoModální

Volání této metody k vytvoření modální dialogové okno.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
[v] Popisovač do okna vlastníka. Výchozí hodnota je vrácená hodnota funkce [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32.

*dwInitParam*<br/>
[v] Určuje hodnotu, která má být předávána dialogovému oknu v parametru *lParam* WM_INITDIALOG zprávy.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu hodnota parametru *nRetCode* zadaná ve volání [EndDialog](#enddialog); jinak -1.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je `CAxDialogImpl` automaticky připojeno k objektu.

Chcete-li vytvořit nemodální dialogové okno, volejte [vytvořit](#create).

## <a name="caxdialogimplenddialog"></a><a name="enddialog"></a>CAxDialogImpl::EndDialog

Volání této metody zničit modální dialogové okno.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
[v] Hodnota, která má být vrácena [DoModal](#domodal).

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je dialogové okno zničeno; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

`EndDialog`musí být volána procedurou dialogového okna. Po zničení dialogového okna použije systém Windows hodnotu *nRetCode* jako vrácenou hodnotu pro `DoModal`aplikaci , která dialogové okno vytvořila.

> [!NOTE]
> Nevolejte, `EndDialog` abyste zničili nemodální dialogové okno. Volání [DestroyWindow](#destroywindow) místo.

## <a name="caxdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc

Volání této metody získat ukazatel `DialogProc` na funkci zpětného volání.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `DialogProc` funkci zpětného volání.

### <a name="remarks"></a>Poznámky

Funkce `DialogProc` je funkce zpětného volání definovaná aplikací.

## <a name="caxdialogimplgetidd"></a><a name="getidd"></a>CAxDialogImpl::GetIDD

Volání této metody získat ID prostředku šablony dialogu.

```
int GetIDD();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ID prostředku šablony dialogu.

## <a name="caxdialogimplisdialogmessage"></a><a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage

Volání této metody k určení, zda je zpráva určena pro toto dialogové okno a pokud je, zpracování zprávy.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Ukazatel na strukturu [MSG,](/windows/win32/api/winuser/ns-winuser-msg) která obsahuje zprávu, která má být kontrolována.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byla zpráva zpracována, jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda je určena pro volání z smyčky zpráv.

## <a name="caxdialogimplm_bmodal"></a><a name="m_bmodal"></a>CAxDialogImpl::m_bModal

Proměnná, která existuje pouze v sestaveních ladění a je nastavena na hodnotu true, pokud je dialogové okno modální.

```
bool m_bModal;
```

## <a name="see-also"></a>Viz také

[CDialogImpl – třída](../../atl/reference/cdialogimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
