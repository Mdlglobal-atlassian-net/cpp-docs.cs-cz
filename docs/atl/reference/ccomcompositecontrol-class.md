---
title: Ccomcompositecontrol – třída
ms.date: 11/04/2016
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
ms.openlocfilehash: f1a9a2d0628b3683f047ce9858d809040438db03
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301997"
---
# <a name="ccomcompositecontrol-class"></a>Ccomcompositecontrol – třída

Tato třída poskytuje metody potřebnou k implementaci složeného ovládacího prvku.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře jako z jiných rozhraní, které chcete podporovat složeného ovládacího prvku.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Konstruktor|
|[CComCompositeControl::~CComCompositeControl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Volání této metody vytvoříte nebo zrušíte avízo o všech ovládacích prvků, které jsou hostitelem složeného ovládacího prvku.|
|[CComCompositeControl::CalcExtent](#calcextent)|Voláním této metody lze vypočítat velikost v jednotkách HIMETRIC používají k hostování složeného ovládacího prvku prostředku dialogového okna.|
|[CComCompositeControl::Create](#create)|Tato metoda je volána k vytvoření složeného ovládacího prvku v okně ovládacího prvku.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Volejte tuto metodu za účelem vytvoření okna ovládacího prvku a dokáží všechny hostované ovládací prvky.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Voláním této metody lze nastavit barvu pozadí složeného ovládacího prvku pomocí kontejneru barvu pozadí.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|Štětec pozadí.|
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|Popisovač okna, který má aktuálně fokus.|

## <a name="remarks"></a>Poznámky

Třídy odvozené z třídy `CComCompositeControl` funkci složeného ovládacího prvku ActiveX dědí. Ovládací prvky ActiveX, které jsou odvozeny z `CComCompositeControl` hostovaných standardní dialogové okno. Tyto typy ovládacích prvků se nazývají složených ovládacích prvků, protože budou mít možnost si hostují jiné ovládací prvky (nativní ovládací prvky Windows a ovládací prvky ActiveX).

`CComCompositeControl` identifikuje prostředku dialogového okna pro použití k vytvoření složeného ovládacího prvku tím, že hledají výčtový datový člen v podřízené třídy. Člen IDD této podřízené třídy je nastavený na ID prostředku, který se použije jako okno ovládacího prvku prostředku dialogového okna. Následuje příklad, který třída odvozena z datového člena `CComCompositeControl` by měl obsahovat k identifikaci prostředku dialogového okna pro okno ovládacího prvku:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
>  Složené ovládací prvky jsou vždy oddílové ovládací prvky, i když mohou obsahovat ovládací prvky bez oken.

Ovládací prvek implementované `CComCompositeControl`-odvozená třída nemá výchozí hodnotu tabulátor chování, které jsou součástí. Když ovládací prvek získá fokus, tak se v kartách v obsahující aplikace, postupně stisknutím klávesy TAB způsobí, že se na cykluje přes všechny složeného ovládacího prvku obsažené ovládací prvky, pak mimo složeného ovládacího prvku a k další položce v pořadí prvků kontejneru. Pořadí prvků hostované ovládací prvky se určuje podle prostředku dialogového okna a určuje pořadí, ve které tabulátor dojde.

> [!NOTE]
>  Aby akcelerátory pracovat správně `CComCompositeControl`, je nutné načíst tabulky akcelerátorů jako ovládací prvek je vytvořen, předejte popisovač a počet akcelerátory zpět do [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), a Nakonec zničí v tabulce při uvolnění ovládacího prvku.

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="advisesinkmap"></a>  CComCompositeControl::AdviseSinkMap

Volání této metody vytvoříte nebo zrušíte avízo o všech ovládacích prvků, které jsou hostitelem složeného ovládacího prvku.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
Hodnota TRUE, pokud všechny ovládací prvky mají být doporučujeme; naopak hodnota false.

### <a name="return-value"></a>Návratová hodnota

|||
|-|-|
|S_OK  |Všechny ovládací prvky v případě jímky mapy byly připojené nebo úspěšně připojený k jejich zdroji událostí.|
|E_FAIL  |Ne všechny ovládací prvky v případě jímky mapa může být připojení nebo odpojení z jejich zdroje událostí úspěšně.|
|E_POINTER  |Tato chyba obvykle znamená problém s položkou v mapě jímky událostí ovládacího prvku nebo problém s argumentem šablony používané `IDispEventImpl` nebo `IDispEventSimpleImpl` základní třídy.|
|CONNECT_E_ADVISELIMIT  |Spojovací bod už dosáhla svého limitu připojení a nemůže přijímat nic dalšího.|
|CONNECT_E_CANNOTCONNECT  |Jímka nepodporuje rozhraní vyžaduje tento bod připojení.|
|CONNECT_E_NOCONNECTION  |Hodnota souboru cookie nepředstavuje platné připojení. Tato chyba obvykle znamená problém s položkou v mapě jímky událostí ovládacího prvku nebo problém s argumentem šablony používané `IDispEventImpl` nebo `IDispEventSimpleImpl` základní třídy.|

### <a name="remarks"></a>Poznámky

Základní implementace této metody prohledává položky událostí jímky mapy. Pak vás informuje o tom nebo unadvises spojovací body s objekty COM je popsáno v mapě událostí jímky jímky položkách. Tato metoda člen také závisí na skutečnost, že odvozená třída dědí z jedné instance `IDispEventImpl` pro každý ovládací prvek v mapě jímky, který má být unadvised nebo doporučené.

##  <a name="calcextent"></a>  CComCompositeControl::CalcExtent

Voláním této metody lze vypočítat velikost v jednotkách HIMETRIC používají k hostování složeného ovládacího prvku prostředku dialogového okna.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Odkaz na `SIZE` strukturu pro vyplnění touto metodou.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud ovládací prvek je hostován dialogovému oknu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Velikost se vrátí v *velikost* parametru.

##  <a name="create"></a>  CComCompositeControl::Create

Tato metoda je volána k vytvoření složeného ovládacího prvku v okně ovládacího prvku.

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač pro nadřazené okno ovládacího prvku.

*rcPos*<br/>
Vyhrazená.

*dwInitParam*<br/>
Data mají být předána do ovládacího prvku během vytvoření ovládacího prvku. Data předána jako *dwInitParam* se zobrazí jako parametr LPARAM [nezavěsíte](/windows/desktop/dlgbox/wm-initdialog) zprávu, která budou odeslána do složeného ovládacího prvku, když se vytvoří.

### <a name="return-value"></a>Návratová hodnota

Popisovač do nově vytvořeného složených ovládacích prvků dialogových oken.

### <a name="remarks"></a>Poznámky

Tato metoda je obvykle volána při místní aktivaci ovládacího prvku.

##  <a name="ccomcompositecontrol"></a>  CComCompositeControl::CComCompositeControl

Konstruktor

```
CComCompositeControl();
```

### <a name="remarks"></a>Poznámky

Inicializuje [CComCompositeControl::m_hbrBackground](#m_hbrbackground) a [CComCompositeControl::m_hWndFocus](#m_hwndfocus) datové členy na hodnotu NULL.

##  <a name="dtor"></a>  CComCompositeControl::~CComCompositeControl

Destruktor.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Poznámky

Odstraní objekt na pozadí, pokud existuje.

##  <a name="createcontrolwindow"></a>  CComCompositeControl::CreateControlWindow

Volejte tuto metodu za účelem vytvoření okna ovládacího prvku a dokáží všechny hostované ovládací prvky.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač pro nadřazené okno ovládacího prvku.

*rcPos*<br/>
Pozici obdélníku složeného ovládacího prvku v klientovi koordinuje vzhledem k *hWndParent*.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač do nově vytvořeného složených ovládacích prvků dialogových oken.

### <a name="remarks"></a>Poznámky

Tato metoda volá [CComCompositeControl::Create](#create) a [CComCompositeControl::AdviseSinkMap](#advisesinkmap).

##  <a name="m_hbrbackground"></a>  CComCompositeControl::m_hbrBackground

Štětec pozadí.

```
HBRUSH m_hbrBackground;
```

##  <a name="m_hwndfocus"></a>  CComCompositeControl::m_hWndFocus

Popisovač okna, který má aktuálně fokus.

```
HWND m_hWndFocus;
```

##  <a name="setbackgroundcolorfromambient"></a>  CComCompositeControl::SetBackgroundColorFromAmbient

Voláním této metody lze nastavit barvu pozadí složeného ovládacího prvku pomocí kontejneru barvu pozadí.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Principy vytváření složených prvků](../../atl/atl-composite-control-fundamentals.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
