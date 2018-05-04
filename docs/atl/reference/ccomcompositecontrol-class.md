---
title: Třída CComCompositeControl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 592eb6c897f47bede5aa0a09149aaf791e8cfbce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl – třída
Tato třída poskytuje metody potřebnou k implementaci složeného ovládacího prvku.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře od dalších rozhraní, které chcete podporovat pro vaše složeného ovládacího prvku.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Konstruktor|  
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Volejte tuto metodu za účelem poradit nebo unadvise všechny ovládací prvky hostované složeného ovládacího prvku.|  
|[CComCompositeControl::CalcExtent](#calcextent)|Volat tuto metodu pro výpočet velikosti v **HIMETRIC** jednotky prostředku dialogového okna, které jsou použity k hostování složeného ovládacího prvku.|  
|[CComCompositeControl::Create](#create)|Tato metoda je volána vytvořit okno pro řízení složeného ovládacího prvku.|  
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Volejte tuto metodu za účelem vytvoření okna pro ovládací prvek a poradit libovolný hostované ovládací prvek.|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Volejte tuto metodu a nastavit barvu pozadí složeného ovládacího prvku pomocí barvu pozadí kontejneru.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|Štětec pozadí plochy.|  
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|Popisovač okna, který má právě fokus.|  
  
## <a name="remarks"></a>Poznámky  
 Třídy odvozené od třídy `CComCompositeControl` dědění funkce složeného ovládacího prvku ActiveX. Ovládací prvky ActiveX, které jsou odvozené z `CComCompositeControl` jsou hostované pomocí standardního dialogového okna. Tyto typy ovládacích prvků se nazývají složené ovládací prvky, protože jsou možné hostovat další ovládací prvky (nativní ovládací prvky systému Windows a ovládací prvky ActiveX).  
  
 `CComCompositeControl` dialogovém okně prostředek se má použít při vytváření složených prvků tak, že vyhledá člena dat výčet ve třídě podřízené identifikuje. Člen IDD této podřízené třídy je nastavena na ID prostředku prostředku dialogového okna, který se použije jako okno ovládacího prvku. Tady je příklad dat člena, který třídy odvozené od `CComCompositeControl` by měl obsahovat k identifikaci prostředku dialogového okna, který se má použít pro okno ovládacího prvku:  
  
 [!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  Složené ovládací prvky jsou vždy oddílové ovládacích prvků, i když mohou obsahovat ovládací prvky bez oken.  
  
 Ovládací prvek implementované `CComCompositeControl`-odvozené třídy má výchozí chování, které jsou součástí použití tabulátoru. Pokud ovládací prvek vybrán, podle probíhá v kartách v obsahující aplikaci, postupně stisknutím klávesy TAB způsobí, že zaměření se cyklicky všechny obsažené prvků složeného ovládacího prvku, potom mimo složeného ovládacího prvku a na další položku v pořadí karet kontejneru. Pořadí karet hostované ovládacích prvků je dáno prostředku dialogového okna a určuje pořadí, ve které použití tabulátoru dojde.  
  
> [!NOTE]
>  Aby akcelerátorů pracovat správně s `CComCompositeControl`, je potřeba načíst tabulky akcelerátorů jako ovládací prvek je vytvořen, předat popisovač a počet akcelerátorů zpět do [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), a nakonec zrušte v tabulce, až bude vydaná ovládacího prvku.  
  
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
 Volejte tuto metodu za účelem poradit nebo unadvise všechny ovládací prvky hostované složeného ovládacího prvku.  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>Parametry  
 `bAdvise`  
 Hodnota TRUE, pokud mají být doporučila; všechny ovládací prvky jinak hodnota false.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`  
 Všechny ovládací prvky v případě mapy jímek byly připojení nebo odpojení od zdroje událostí úspěšně.  
  
 **E_FAIL**  
 Ne všechny ovládací prvky v případě mapy jímek může připojení nebo odpojení od zdroje událostí úspěšně.  
  
 `E_POINTER`  
 Tato chyba obvykle označuje potíže s položkou do mapy jímek událostí ovládacího prvku nebo problém s argumentem šablony použité v `IDispEventImpl` nebo `IDispEventSimpleImpl` základní třídy.  
  
 **CONNECT_E_ADVISELIMIT**  
 Spojovací bod již dosáhl svého limitu připojení a nemůže přijímat žádné další.  
  
 **CONNECT_E_CANNOTCONNECT**  
 Jímka nepodporuje rozhraní požadované pomocí tohoto bodu připojení.  
  
 **CONNECT_E_NOCONNECTION**  
 Hodnota souboru cookie nepředstavuje platné připojení. Tato chyba obvykle označuje potíže s položkou do mapy jímek událostí ovládacího prvku nebo problém s argumentem šablony použité v `IDispEventImpl` nebo `IDispEventSimpleImpl` základní třídy.  
  
### <a name="remarks"></a>Poznámky  
 Základní implementace této metody vyhledá prostřednictvím položky události podřízený mapy. Potom informuje o tom, nebo unadvises body připojení k objektům modelu COM popsaného mapy jímek událostí podřízený položky. Tato metoda člen také závisí na skutečnost, že odvozené třídy dědí z jednu instanci `IDispEventImpl` pro každý ovládací prvek v mapě podřízený, které se má doporučené nebo unadvised.  
  
##  <a name="calcextent"></a>  CComCompositeControl::CalcExtent  
 Volat tuto metodu pro výpočet velikosti v **HIMETRIC** jednotky prostředku dialogového okna, které jsou použity k hostování složeného ovládacího prvku.  
  
```
BOOL CalcExtent(SIZE& size);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Odkaz na **velikost** struktura, aby byla vyplněna touto metodou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud hostitelem dialogové okno; je ovládací prvek jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Velikost je vrácený v `size` parametr.  
  
##  <a name="create"></a>  CComCompositeControl::Create  
 Tato metoda je volána vytvořit okno pro řízení složeného ovládacího prvku.  
  
```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 Obslužná rutina do nadřazeného okna ovládacího prvku.  
  
 `rcPos`  
 Vyhrazena.  
  
 `dwInitParam`  
 Data mají být předána do ovládacího prvku během vytvoření ovládacího prvku. Data předaná jako `dwInitParam` se zobrazí jako **LPARAM** parametr [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) zpráva, která budou odeslána složeného ovládacího prvku, když se vytvoří.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro dialogové okno nově vytvořený složeného ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána obvykle během aktivace na místě ovládacího prvku.  
  
##  <a name="ccomcompositecontrol"></a>  CComCompositeControl::CComCompositeControl  
 Konstruktor  
  
```
CComCompositeControl();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje [CComCompositeControl::m_hbrBackground](#m_hbrbackground) a [CComCompositeControl::m_hWndFocus](#m_hwndfocus) datové členy na hodnotu NULL.  
  
##  <a name="dtor"></a>  CComCompositeControl:: ~ CComCompositeControl  
 Destruktor.  
  
```
~CComCompositeControl();
```  
  
### <a name="remarks"></a>Poznámky  
 Odstraní objekt pozadí, pokud existuje.  
  
##  <a name="createcontrolwindow"></a>  CComCompositeControl::CreateControlWindow  
 Volejte tuto metodu za účelem vytvoření okna pro ovládací prvek a poradit všechny hostované ovládací prvky.  
  
```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 Obslužná rutina do nadřazeného okna ovládacího prvku.  
  
 `rcPos`  
 Pozice rámečku složeného ovládacího prvku v klientovi koordinuje vzhledem k `hWndParent`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač do dialogového okna nově vytvořený složeného ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [CComCompositeControl::Create](#create) a [CComCompositeControl::AdviseSinkMap](#advisesinkmap).  
  
##  <a name="m_hbrbackground"></a>  CComCompositeControl::m_hbrBackground  
 Štětec pozadí plochy.  
  
```
HBRUSH m_hbrBackground;
```  
  
##  <a name="m_hwndfocus"></a>  CComCompositeControl::m_hWndFocus  
 Popisovač okna, který má právě fokus.  
  
```
HWND m_hWndFocus;
```  
  
##  <a name="setbackgroundcolorfromambient"></a>  CComCompositeControl::SetBackgroundColorFromAmbient  
 Volejte tuto metodu a nastavit barvu pozadí složeného ovládacího prvku pomocí barvu pozadí kontejneru.  
  
```
HRESULT SetBackgroundColorFromAmbient();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
## <a name="see-also"></a>Viz také  
 [CComControl – třída](../../atl/reference/ccomcontrol-class.md)   
 [Principy vytváření složených prvků](../../atl/atl-composite-control-fundamentals.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
