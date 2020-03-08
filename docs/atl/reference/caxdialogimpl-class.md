---
title: CAxDialogImpl – třída
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
ms.openlocfilehash: 548d2aed0644187b4b8dee1e472b581f1f92d6a1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865053"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl – třída

Tato třída implementuje dialogové okno (modální nebo nemodální), které hostuje ovládací prvky ActiveX.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `CAxDialogImpl`.

*TBase*<br/>
Základní třída okna pro `CDialogImplBaseT`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Voláním této metody můžete poradit nebo odradit všechny položky v mapě událostí mapy jímky objektu.|
|[CAxDialogImpl:: Create](#create)|Voláním této metody vytvoříte nemodální dialogové okno.|
|[CAxDialogImpl::D estroyWindow](#destroywindow)|Voláním této metody zničíte nemodální dialogové okno.|
|[CAxDialogImpl::D oModal](#domodal)|Zavolejte tuto metodu pro vytvoření modálního dialogového okna.|
|[CAxDialogImpl:: EndDialog](#enddialog)|Zavolejte tuto metodu pro zničení modálního dialogového okna.|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Voláním této metody získáte ukazatel na funkci zpětného volání `DialogProc`.|
|[CAxDialogImpl::GetIDD](#getidd)|Voláním této metody získáte ID prostředku šablony dialogového okna.|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Voláním této metody určíte, zda je zpráva určena pro toto dialogové okno a v případě, že je, zpracujte zprávu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAxDialogImpl:: m_bModal](#m_bmodal)|Proměnná, která existuje pouze v sestavení ladění a je nastavena na hodnotu true, pokud je dialogové okno modální.|

## <a name="remarks"></a>Poznámky

`CAxDialogImpl` umožňuje vytvořit modální nebo nemodální dialogové okno. `CAxDialogImpl` poskytuje postup dialogového okna, který používá výchozí mapu zpráv k přímému směrování zpráv na příslušné obslužné rutiny.

`CAxDialogImpl` jsou odvozeny z `CDialogImplBaseT`, které se zase odvozují z *TBase* (ve výchozím nastavení `CWindow`) a `CMessageMap`.

Vaše třída musí definovat člen IDD, který určuje ID prostředku šablony dialogového okna. Například přidání objektu dialogového okna ATL pomocí dialogového okna **Přidat třídu** automaticky přidá následující řádek do třídy:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

kde `MyDialog` je **krátký název** zadaný v průvodci dialogem ATL.

Další informace najdete v tématu [Implementace dialogového okna](../../atl/implementing-a-dialog-box.md) .

Všimněte si, že ovládací prvek ActiveX na modálním dialogovém okně vytvořeném pomocí `CAxDialogImpl` nebude podporovat klávesové zkratky. Aby bylo možné podporovat přístupové klávesy v dialogovém okně vytvořeném pomocí `CAxDialogImpl`, vytvořte nemodální dialogové okno a pomocí vlastní smyčky zpráv použijte [CAxDialogImpl:: IsDialogMessage](#isdialogmessage) po získání zprávy z fronty, která bude zpracovávat klávesovou zkratku.

Další informace o `CAxDialogImpl`najdete v tématu [Nejčastější dotazy k omezením ovládacího prvku ATL](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap

Voláním této metody můžete poradit nebo odradit všechny položky v mapě událostí mapy jímky objektu.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
Nastavte na hodnotu true, pokud se mají vyhodnotit všechny záznamy jímky. false, pokud mají být všechny záznamy jímky nedoporučeníné.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="create"></a>CAxDialogImpl:: Create

Voláním této metody vytvoříte nemodální dialogové okno.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
pro Popisovač okna vlastníka.

*dwInitParam*<br/>
pro Určuje hodnotu, která má být předána do dialogového okna v parametru *lParam* zprávy WM_INITDIALOG.

*& RECT*<br/>
Tento parametr není používán. Tento parametr je předán pomocí `CComControl`.

### <a name="return-value"></a>Návratová hodnota

Popisovač nově vytvořeného dialogového okna.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je automaticky připojeno k objektu `CAxDialogImpl`. Chcete-li vytvořit modální dialogové okno, zavolejte [DoModal](#domodal).

Druhé přepsání je k dispozici pouze pro dialogová okna, která lze použít s [CComControl](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>CAxDialogImpl::D estroyWindow

Voláním této metody zničíte nemodální dialogové okno.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je okno úspěšně zničeno; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Nevolejte `DestroyWindow` k zničení modálního dialogového okna. Místo toho zavolejte [EndDialog](#enddialog) .

##  <a name="domodal"></a>CAxDialogImpl::D oModal

Zavolejte tuto metodu pro vytvoření modálního dialogového okna.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
pro Popisovač okna vlastníka. Výchozí hodnota je návratová hodnota funkce [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32.

*dwInitParam*<br/>
pro Určuje hodnotu, která má být předána do dialogového okna v parametru *lParam* zprávy WM_INITDIALOG.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu hodnota parametru *nRetCode* zadaného ve volání [EndDialog](#enddialog); v opačném případě-1.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je automaticky připojeno k objektu `CAxDialogImpl`.

Chcete-li vytvořit nemodální dialogové okno, zavolejte příkaz [Create](#create).

##  <a name="enddialog"></a>CAxDialogImpl:: EndDialog

Zavolejte tuto metodu pro zničení modálního dialogového okna.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
pro Hodnota, která má být vrácena funkcí [DoModal](#domodal).

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je dialogové okno zničeno; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

`EndDialog` musí být volána prostřednictvím postupu dialogového okna. Po zničení dialogového okna používá systém Windows hodnotu *nRetCode* jako návratovou hodnotu pro `DoModal`, která vytvořila dialogové okno.

> [!NOTE]
>  Nevolejte `EndDialog` k zničení nemodálního dialogového okna. Místo toho zavolejte [DestroyWindow](#destroywindow) .

##  <a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc

Voláním této metody získáte ukazatel na funkci zpětného volání `DialogProc`.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na funkci zpětného volání `DialogProc`.

### <a name="remarks"></a>Poznámky

Funkce `DialogProc` je funkce zpětného volání definovaného aplikací.

##  <a name="getidd"></a>CAxDialogImpl::GetIDD

Voláním této metody získáte ID prostředku šablony dialogového okna.

```
int GetIDD();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ID prostředku šablony dialogového okna.

##  <a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage

Voláním této metody určíte, zda je zpráva určena pro toto dialogové okno a v případě, že je, zpracujte zprávu.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Ukazatel [na strukturu zprávy](/windows/win32/api/winuser/ns-winuser-msg) , která obsahuje zprávu, kterou chcete zkontrolovat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byla zpráva zpracována, jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda má být volána v rámci smyčky zpráv.

##  <a name="m_bmodal"></a>CAxDialogImpl:: m_bModal

Proměnná, která existuje pouze v sestavení ladění a je nastavena na hodnotu true, pokud je dialogové okno modální.

```
bool m_bModal;
```

## <a name="see-also"></a>Viz také

[CDialogImpl – třída](../../atl/reference/cdialogimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
