---
title: CComCompositeControl – třída
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
ms.openlocfilehash: b57eaf105bfca1a49d53b5e5e99969b0fa2fc82f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864947"
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl – třída

Tato třída poskytuje metody vyžadované k implementaci složeného ovládacího prvku.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená z [třídy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)a také z dalších rozhraní, která chcete pro složený ovládací prvek podporovat.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Konstruktor|
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Voláním této metody můžete poradit nebo odradit všechny ovládací prvky hostované složeným ovládacím prvkem.|
|[CComCompositeControl::CalcExtent](#calcextent)|Zavolejte tuto metodu pro výpočet velikosti v jednotkách HIMETRIC prostředku dialogového okna, který se používá pro hostování složeného ovládacího prvku.|
|[CComCompositeControl:: Create](#create)|Tato metoda je volána k vytvoření okna ovládacího prvku pro složený ovládací prvek.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Voláním této metody vytvoříte okno ovládacího prvku a upozorníte všechny hostované ovládací prvky.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Voláním této metody nastavíte barvu pozadí složeného ovládacího prvku pomocí barvy pozadí kontejneru.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComCompositeControl:: m_hbrBackground](#m_hbrbackground)|Štětec pozadí.|
|[CComCompositeControl:: m_hWndFocus](#m_hwndfocus)|Popisovač okna, které aktuálně má fokus.|

## <a name="remarks"></a>Poznámky

Třídy odvozené od třídy `CComCompositeControl` dědí funkce složeného ovládacího prvku ActiveX. Ovládací prvky ActiveX odvozené z `CComCompositeControl` jsou hostovány standardním dialogovým oknem. Tyto typy ovládacích prvků se nazývají složené ovládací prvky, protože jsou schopny hostovat jiné ovládací prvky (nativní ovládací prvky systému Windows a ovládací prvky ActiveX).

`CComCompositeControl` identifikuje prostředek dialogového okna, který se má použít při vytváření složeného ovládacího prvku, a to tak, že vyhledá Výčtový datový člen v podřízené třídě. Člen IDD této podřízené třídy je nastaven na ID prostředku pro prostředek dialogu, který bude použit jako okno ovládacího prvku. Následuje příklad datového členu, který třída odvozená z `CComCompositeControl` by měla obsahovat k identifikaci prostředku dialogového okna, který se má použít pro okno ovládacího prvku:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
>  Složené ovládací prvky jsou vždy ovládací prvky okna, i když mohou obsahovat ovládací prvky bez oken.

Ovládací prvek implementovaný třídou odvozenou od `CComCompositeControl`má vestavěné výchozí chování při procházení. Když ovládací prvek dostane fokus se zaměřením na kartu v rámci obsahující aplikace, Poklikáním na klávesu TAB dojde k cyklickému procházení fokusu všemi obsaženými ovládacími prvky složeného ovládacího prvku, a poté mimo složený ovládací prvek a na další položku v pořadí prvků kontejneru. Pořadí karet hostovaných ovládacích prvků je určeno pomocí prostředku dialogového okna a určuje pořadí, ve kterém budou klávesy TAB provedeny.

> [!NOTE]
>  Aby akcelerátory správně fungovaly s `CComCompositeControl`, je nutné načíst tabulku akcelerátorů, když je ovládací prvek vytvořen, předat popisovač a počet akcelerátorů zpět do [IOleControlImpl:: GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)a nakonec zničit tabulku při vydání ovládacího prvku.

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap

Voláním této metody můžete poradit nebo odradit všechny ovládací prvky hostované složeným ovládacím prvkem.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
True, pokud jsou všechny ovládací prvky doporučeno; v opačném případě false.

### <a name="return-value"></a>Návratová hodnota

|||
|-|-|
|S_OK  |Všechny ovládací prvky v mapě jímky událostí byly úspěšně připojeny nebo odpojeny od svého zdroje událostí.|
|E_FAIL  |Ne všechny ovládací prvky v mapě jímky událostí by mohly být připojeny nebo odpojeny od svého zdroje událostí úspěšně.|
|E_POINTER  |Tato chyba obvykle označuje problém s položkou v mapě jímky událostí ovládacího prvku nebo problém s argumentem šablony použitým v `IDispEventImpl` nebo `IDispEventSimpleImpl` základní třídy.|
|CONNECT_E_ADVISELIMIT  |Spojovací bod již dosáhl svého limitu připojení a nemůže přijmout žádné další.|
|CONNECT_E_CANNOTCONNECT  |Jímka nepodporuje rozhraní požadované tímto spojovacím bodem.|
|CONNECT_E_NOCONNECTION  |Hodnota souboru cookie nepředstavuje platné připojení. Tato chyba obvykle označuje problém s položkou v mapě jímky událostí ovládacího prvku nebo problém s argumentem šablony použitým v `IDispEventImpl` nebo `IDispEventSimpleImpl` základní třídy.|

### <a name="remarks"></a>Poznámky

Základní implementace této metody prohledá záznamy v mapě jímky událostí. Poté informuje nebo poradí body připojení k objektům COM, které jsou popsány v záznamech jímky v mapě jímky událostí. Tato členská metoda také spoléhá na skutečnost, že odvozená třída dědí z jedné instance `IDispEventImpl` pro každý ovládací prvek v mapě jímky, který má být doporučeno nebo nedoporučuje.

##  <a name="calcextent"></a>CComCompositeControl::CalcExtent

Zavolejte tuto metodu pro výpočet velikosti v jednotkách HIMETRIC prostředku dialogového okna, který se používá pro hostování složeného ovládacího prvku.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Odkaz na strukturu `SIZE`, kterou chcete vyplnit touto metodou.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je ovládací prvek hostován dialogovým oknem; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Velikost se vrátí v parametru *Size* .

##  <a name="create"></a>CComCompositeControl:: Create

Tato metoda je volána k vytvoření okna ovládacího prvku pro složený ovládací prvek.

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
Rezervovaný.

*dwInitParam*<br/>
Data, která mají být předána ovládacímu prvku během vytváření ovládacího prvku. Data předaná jako *dwInitParam* se zobrazí jako parametr LPARAM zprávy [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) , která se pošle do složeného ovládacího prvku, když se vytvoří.

### <a name="return-value"></a>Návratová hodnota

Popisovač nově vytvořeného dialogového okna složeného ovládacího prvku.

### <a name="remarks"></a>Poznámky

Tato metoda je obvykle volána během místní aktivace ovládacího prvku.

##  <a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl

Konstruktor

```
CComCompositeControl();
```

### <a name="remarks"></a>Poznámky

Inicializuje datové členy [CComCompositeControl:: m_hbrBackground](#m_hbrbackground) a [CComCompositeControl:: m_hWndFocus](#m_hwndfocus) na hodnotu null.

##  <a name="dtor"></a>CComCompositeControl:: ~ CComCompositeControl

Destruktor.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Poznámky

Odstraní objekt na pozadí, pokud existuje.

##  <a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow

Voláním této metody vytvoříte okno ovládacího prvku a upozorníte všechny hostované ovládací prvky.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Popisovač nadřazeného okna ovládacího prvku.

*rcPos*<br/>
Pozice obdélníku složeného ovládacího prvku v souřadnicích klienta vzhledem k *hwndParent*.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač do nově vytvořeného dialogového okna složeného ovládacího prvku.

### <a name="remarks"></a>Poznámky

Tato metoda volá [CComCompositeControl:: Create](#create) a [CComCompositeControl:: AdviseSinkMap](#advisesinkmap).

##  <a name="m_hbrbackground"></a>CComCompositeControl:: m_hbrBackground

Štětec pozadí.

```
HBRUSH m_hbrBackground;
```

##  <a name="m_hwndfocus"></a>CComCompositeControl:: m_hWndFocus

Popisovač okna, které aktuálně má fokus.

```
HWND m_hWndFocus;
```

##  <a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient

Voláním této metody nastavíte barvu pozadí složeného ovládacího prvku pomocí barvy pozadí kontejneru.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="see-also"></a>Viz také

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Složené základní prvky](../../atl/atl-composite-control-fundamentals.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
