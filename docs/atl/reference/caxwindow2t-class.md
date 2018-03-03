---
title: "Třída CAxWindow2T | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12b7c8c66a092a92ef7fce25ce283f5145d9f910
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="caxwindow2t-class"></a>CAxWindow2T – třída
Tato třída poskytuje metody pro práci s okno, které hostuje ovládacího prvku ActiveX a má také podpora pro hostování licencované ovládací prvky ActiveX.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```  
  
#### <a name="parameters"></a>Parametry  
 *TBase*  
 Třídu, ze které `CAxWindowT` odvozena.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Vytvoří `CAxWindow2T` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAxWindow2T::Create](#create)|Vytvoří okno hostitele.|  
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.|  
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Vytvoří licencované ovládací prvek ActiveX, inicializuje ji, hostitelem v zadané okno a načte ukazatele rozhraní (nebo ukazatele) z ovládacího prvku.|  
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Statickou metodu, která načte název třídy oken.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAxWindow2T::operator =](#operator_eq)|Přiřadí `HWND` na stávající `CAxWindow2T` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CAxWindow2T`poskytuje metody pro manipulaci s časového období, který je hostitelem ovládacího prvku ActiveX. `CAxWindow2T`má také podpora pro hostování licencované ovládací prvky ActiveX. Který je hostitelem zajišťuje " **AtlAxWinLic80**", který je zabalen `CAxWindow2T`.  
  
 Třída `CAxWindow2` je implementovaný jako specializace z `CAxWindow2T` třídy. Tato specializace je deklarován jako:  
  
 `typedef CAxWindow2T <CWindow> CAxWindow2;`  
  
> [!NOTE]
> `CAxWindowT`členy jsou popsané v části [CAxWindow](../../atl/reference/caxwindow-class.md).  
  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá členy této třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `TBase`  
  
 `CAxWindowT`  
  
 `CAxWindow2T`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T  
 Vytvoří `CAxWindow2T` objektu.  
  
```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 Obslužná rutina existujícího okna.  
  
##  <a name="create"></a>CAxWindow2T::Create  
 Vytvoří okno hostitele.  
  
```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="remarks"></a>Poznámky  
 `CAxWindow2T::Create`volání [CWindow::Create](../../atl/reference/cwindow-class.md#create) s `LPCTSTR lpstrWndClass` parametr nastaven na okno třídu, která poskytuje – hostování ovládacího prvku ( **AtlAxWinLic80**).  
  
 V tématu `CWindow::Create` popis parametry a návratové hodnoty.  
  
 **Poznámka:** Pokud 0 se používá jako hodnota `MenuOrID` parametr, musí být zadán jako 0U (výchozí hodnota) aby se zabránilo chybě kompilátoru.  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá `CAxWindow2T::Create`.  
  
##  <a name="createcontrollic"></a>CAxWindow2T::CreateControlLic  
 Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.  
  
```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrLicKey`  
 Licenční klíč pro ovládací prvek; Hodnota NULL, pokud vytvoření ovládacího prvku nonlicensed.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) popis zbývající parametry a návratové hodnoty.  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá `CAxWindow2T::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx  
 Vytvoří licencované ovládací prvek ActiveX, inicializuje ji, hostitelem v zadané okno a načte ukazatele rozhraní (nebo ukazatele) z ovládacího prvku.  
  
```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrLicKey`  
 Licenční klíč pro ovládací prvek; Hodnota NULL, pokud vytvoření ovládacího prvku nonlicensed.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) popis zbývající parametry a návratové hodnoty.  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá `CAxWindow2T::CreateControlLicEx`.  
  
##  <a name="getwndclassname"></a>CAxWindow2T::GetWndClassName  
 Načte název třídy oken.  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec obsahující název třídy oken ( **AtlAxWinLic80**), může být hostitelem licencovanou a nonlicensed ovládací prvky ActiveX.  
  
##  <a name="operator_eq"></a>CAxWindow2T::operator =  
 Přiřadí `HWND` na stávající `CAxWindow2T` objektu.  
  
```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 Obslužná rutina existujícího okna.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Uzavření ovládacího prvku – nejčastější dotazy](../../atl/atl-control-containment-faq.md)
