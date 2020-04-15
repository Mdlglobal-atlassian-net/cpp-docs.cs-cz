---
title: Třída CComCompositeControl
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
ms.openlocfilehash: 700a8047ab1fa9df85c8e6530eb3eed5f29bd3d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320809"
---
# <a name="ccomcompositecontrol-class"></a>Třída CComCompositeControl

Tato třída poskytuje metody potřebné k implementaci složeného ovládacího prvku.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), stejně jako z jiných rozhraní, které chcete podporovat pro složený ovládací prvek.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Konstruktor|
|[CComCompositeControl::~CComCompositeControl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CcomCompositeControl::AdviseSinkMap](#advisesinkmap)|Volání této metody poradit nebo unadvise všechny ovládací prvky hostované složený ovládací prvek.|
|[CComCompositeControl::CalcExtent](#calcextent)|Volání této metody k výpočtu velikosti v jednotkách HIMETRIC dialogového okna prostředku používaného k hostování složeného ovládacího prvku.|
|[CComCompositeControl::Vytvořit](#create)|Tato metoda je volána k vytvoření ovládacího okna pro složený ovládací prvek.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Volání této metody k vytvoření okna ovládacího prvku a poradit všechny hostované ovládací prvek.|
|[CcomCompositeControl::SetBackgroundColorFromambient](#setbackgroundcolorfromambient)|Volánítéto metody nastavit barvu pozadí složené ovládacího prvku pomocí barvy pozadí kontejneru.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|Štětec na pozadí.|
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|Popisovač okna, které má aktuálně fokus.|

## <a name="remarks"></a>Poznámky

Třídy odvozené `CComCompositeControl` z třídy dědí funkce složeného ovládacího prvku ActiveX. Ovládací prvky ActiveX odvozené z `CComCompositeControl` nich jsou hostovány standardním dialogovým oknem. Tyto typy ovládacích prvků se nazývají složené ovládací prvky, protože jsou schopny hostovat další ovládací prvky (nativní ovládací prvky systému Windows a ovládací prvky ActiveX).

`CComCompositeControl`identifikuje prostředek dialogu, který se má použít při vytváření složeného ovládacího prvku, hledáním člena s výčtem dat v podřízené třídě. IDD člena této podřízené třídy je nastaveno na ID prostředku dialogového okna, který bude použit jako okno ovládacího prvku. Následuje příklad datového člena, který by měl `CComCompositeControl` třídy odvozené z by měla obsahovat k identifikaci dialogového prostředku, který má být použit pro okno ovládacího prvku:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
> Složené ovládací prvky jsou vždy v okně ovládací prvky, i když mohou obsahovat ovládací prvky bez oken.

Ovládací prvek implementovaný odvozenou `CComCompositeControl`třídou má vestavěné výchozí chování tabulátoru. Když ovládací prvek obdrží fokus tím, že jsou tabulátory v obsahující aplikaci, postupně stisknutím klávesy TAB způsobí, že fokus cykluje přes všechny ovládací prvky obsažené složený ovládací prvek, pak z kompozitního ovládacího prvku a na další položku v pořadí polí kontejneru. Pořadí polí hostovaných ovládacích prvků je určeno zdrojem dialogu a určuje pořadí, ve kterém dojde k tabulátoru.

> [!NOTE]
> Aby akcelerátory pracovat správně `CComCompositeControl`s , je nutné načíst tabulku akcelerátoru jako ovládací prvek je vytvořen, předat popisovač a počet akcelerátorů zpět do [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), a nakonec zničit tabulku při uvolnění ovládacího prvku.

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[Ovládací prvek CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="ccomcompositecontroladvisesinkmap"></a><a name="advisesinkmap"></a>CcomCompositeControl::AdviseSinkMap

Volání této metody poradit nebo unadvise všechny ovládací prvky hostované složený ovládací prvek.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bPoradit*<br/>
Platí, pokud všechny ovládací prvky mají být doporučeny; jinak nepravdivé.

### <a name="return-value"></a>Návratová hodnota

|||
|-|-|
|S_OK  |Všechny ovládací prvky v mapě jímky událostí byly úspěšně připojeny nebo odpojeny od zdroje událostí.|
|E_fail  |Ne všechny ovládací prvky v mapě jímky událostí může být připojennebo odpojen od jejich zdroje událostí úspěšně.|
|E_POINTER  |Tato chyba obvykle označuje problém s položkou v mapování jímky událostí ovládacího `IDispEventImpl` prvku `IDispEventSimpleImpl` nebo problém s argumentem šablony používanév nebo základní třídy.|
|CONNECT_E_ADVISELIMIT  |Bod připojení již dosáhl svého limitu připojení a nemůže přijmout žádné další.|
|CONNECT_E_CANNOTCONNECT  |Jímka nepodporuje rozhraní vyžadované tímto bodem připojení.|
|CONNECT_E_NOCONNECTION  |Hodnota souboru cookie nepředstavuje platné připojení. Tato chyba obvykle označuje problém s položkou v mapování jímky událostí ovládacího `IDispEventImpl` prvku `IDispEventSimpleImpl` nebo problém s argumentem šablony používanév nebo základní třídy.|

### <a name="remarks"></a>Poznámky

Základní implementace této metody prohledává položky v mapě jímky událostí. Potom poskytuje nebo unadvises spojovací body na com objekty popsané položky jímky jímky události. Tato metoda člena také závisí na skutečnosti, že odvozené `IDispEventImpl` třídy dědí z jedné instance pro každý ovládací prvek v mapě jímky, který je třeba doporučit nebo nedoporučeno.

## <a name="ccomcompositecontrolcalcextent"></a><a name="calcextent"></a>CComCompositeControl::CalcExtent

Volání této metody k výpočtu velikosti v jednotkách HIMETRIC dialogového okna prostředku používaného k hostování složeného ovládacího prvku.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Odkaz na `SIZE` strukturu, která má být vyplněna touto metodou.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je ovládací prvek hostován dialogovým oknem; jinak FALSE.

### <a name="remarks"></a>Poznámky

Velikost je vrácena v parametru *size.*

## <a name="ccomcompositecontrolcreate"></a><a name="create"></a>CComCompositeControl::Vytvořit

Tato metoda je volána k vytvoření ovládacího okna pro složený ovládací prvek.

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač nadřazeného okna ovládacího prvku.

*rcPos*<br/>
Vyhrazeno.

*dwInitParam*<br/>
Data, která mají být předána ovládacímu prvku během vytváření ovládacího prvku. Data předávaná jako *dwInitParam* se zobrazí jako parametr LPARAM [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) zprávy, která bude odeslána do složeného ovládacího prvku při jeho vytvoření.

### <a name="return-value"></a>Návratová hodnota

Úchyt k nově vytvořenému složenému ovládacímu dialogovému oknu.

### <a name="remarks"></a>Poznámky

Tato metoda se obvykle nazývá během aktivace ovládacího prvku na místě.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl

Konstruktor

```
CComCompositeControl();
```

### <a name="remarks"></a>Poznámky

Inicializuje [ccomcompositecontrol::m_hbrBackground](#m_hbrbackground) a [CComCompositeControl:::m_hWndFocus](#m_hwndfocus) datových členů na HODNOTU NULL.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="dtor"></a>CComCompositeControl::~CComCompositeControl

Destruktor.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Poznámky

Odstraní objekt pozadí, pokud existuje.

## <a name="ccomcompositecontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow

Volání této metody k vytvoření okna ovládacího prvku a poradit všechny hostované ovládací prvky.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač nadřazeného okna ovládacího prvku.

*rcPos*<br/>
Obdélník pozice složeného ovládacího prvku v souřadnicích klienta vzhledem k *hWndParent*.

### <a name="return-value"></a>Návratová hodnota

Vrátí úchyt do nově vytvořeného dialogového okna složeného ovládacího prvku.

### <a name="remarks"></a>Poznámky

Tato metoda volá [CComCompositeControl::Create](#create) a [CComCompositeControl::AdviseSinkMap](#advisesinkmap).

## <a name="ccomcompositecontrolm_hbrbackground"></a><a name="m_hbrbackground"></a>CComCompositeControl::m_hbrBackground

Štětec na pozadí.

```
HBRUSH m_hbrBackground;
```

## <a name="ccomcompositecontrolm_hwndfocus"></a><a name="m_hwndfocus"></a>CComCompositeControl::m_hWndFocus

Popisovač okna, které má aktuálně fokus.

```
HWND m_hWndFocus;
```

## <a name="ccomcompositecontrolsetbackgroundcolorfromambient"></a><a name="setbackgroundcolorfromambient"></a>CcomCompositeControl::SetBackgroundColorFromambient

Volánítéto metody nastavit barvu pozadí složené ovládacího prvku pomocí barvy pozadí kontejneru.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="see-also"></a>Viz také

[Třída CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Základy kompozitního řízení](../../atl/atl-composite-control-fundamentals.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
