---
title: "Třída CComControl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
dev_langs: C++
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0ddbd18ac39721dd80eb547e53c7708891b94aa9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomcontrol-class"></a>CComControl – třída
Tato třída poskytuje metody pro vytváření a správu ATL ovládací prvky.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class WinBase = CWindowImpl<T>>  
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída implementace ovládacího prvku.  
  
 *WinBase*  
 Základní třída, která implementuje oddílová funkce. Použije se výchozí hodnota [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComControl::CComControl](#ccomcontrol)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Načte ukazatel na požadované rozhraní.|  
|[CComControl::CreateControlWindow](#createcontrolwindow)|Vytvoří okna pro ovládací prvek.|  
|[CComControl::FireOnChanged](#fireonchanged)|Upozorní kontejneru podřízený, které se změnily vlastnosti ovládacího prvku.|  
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Kontejneru podřízený upozorní, že vlastnost ovládacího prvku se má změnit a že objekt je s dotazem, jímky postup pokračovat.|  
|[CComControl::MessageBox](#messagebox)|Voláním této metody lze vytvořit, zobrazit a pracovat se zprávou.|  
  
## <a name="remarks"></a>Poznámky  
 `CComControl`je sada užitečné řízení pomocných funkcí a základní data členů pro ovládací prvky knihovny ATL. Když vytvoříte standardního ovládacího prvku nebo ovládací prvek DHTML pomocí Průvodce ovládacím prvkem ATL, průvodce automaticky odvodí třídě z `CComControl`. `CComControl`Odvozená většinu její metody z [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).  
  
 Další informace o vytvoření ovládacího prvku, najdete v článku [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md). Další informace o Průvodci projektu knihovny ATL, najdete v článku [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Pro předvedení `CComControl` metody a členy data, najdete v článku [str](../../visual-cpp-samples.md) ukázka.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 `CComControl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="ccomcontrol"></a>CComControl::CComControl  
 Konstruktor  
  
```
CComControl();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) konstruktoru, předávání `m_hWnd` – datový člen zděděná prostřednictvím [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
##  <a name="controlqueryinterface"></a>CComControl::ControlQueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor GUID se požadované rozhraní.  
  
 `ppv`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný `iid`, nebo **NULL** Pokud rozhraní nebyl nalezen.  
  
### <a name="remarks"></a>Poznámky  
 Zpracovává jenom rozhraní v tabulce COM mapy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]  
  
##  <a name="createcontrolwindow"></a>CComControl::CreateControlWindow  
 Ve výchozím nastavení, vytvoří okna pro ovládací prvek voláním `CWindowImpl::Create`.  
  
```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [v] Zpracování do okna nadřazené nebo vlastníka. Je nutné zadat platný okno popisovač. Okno pro řízení je omezen na oblasti jeho nadřazeného okna.  
  
 `rcPos`  
 [v] Počáteční velikost a umístění okna, který se má vytvořit.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, pokud chcete, aby dělala něco jiné než vytvořit v jednom okně, například pokud chcete vytvořit dvě windows, z nichž jeden se změní na panelu nástrojů pro ovládací prvek.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]  
  
##  <a name="fireonchanged"></a>CComControl::FireOnChanged  
 Upozorní kontejneru podřízený, které se změnily vlastnosti ovládacího prvku.  
  
```
HRESULT FireOnChanged(DISPID dispID);
```  
  
### <a name="parameters"></a>Parametry  
 *dispID*  
 [v] Identifikátor vlastnosti, která se změnila.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše řízení třída odvozena z [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), tato metoda volá [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) upozornit všechny připojené `IPropertyNotifySink` rozhraní, která daný ovládací prvek změnila se vlastnost. Pokud vaše třída ovládacích prvků není odvozena od `IPropertyNotifySink`, vrátí tato metoda `S_OK`. 
  
 Tato metoda je bezpečné volat i v případě vlastního ovládacího prvku nepodporuje spojovací body.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]  
  
##  <a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit  
 Kontejneru podřízený upozorní, že vlastnost ovládacího prvku se má změnit a že objekt je s dotazem, jímky postup pokračovat.  
  
```
HRESULT FireOnRequestEdit(DISPID dispID);
```  
  
### <a name="parameters"></a>Parametry  
 *dispID*  
 [v] Identifikátor vlastnosti Chystáte se změnit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše řízení třída odvozena z [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), tato metoda volá [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) upozornit všechny připojené `IPropertyNotifySink` rozhraní, která zadaný ovládací prvek vlastnost je změnit. Pokud vaše třída ovládacích prvků není odvozena od `IPropertyNotifySink`, vrátí tato metoda `S_OK`.  

  
 Tato metoda je bezpečné volat i v případě vlastního ovládacího prvku nepodporuje spojovací body.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]  
  
##  <a name="messagebox"></a>CComControl::MessageBox  
 Voláním této metody lze vytvořit, zobrazit a pracovat se zprávou.  
  
```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Text, který se zobrazí v okně zprávy.  
  
 `lpszCaption`  
 Názvu dialogového okna. Pokud hodnotu NULL (výchozí), název se používá "Chyba".  
  
 `nType`  
 Určuje obsahu a chování dialogového okna. Najdete v článku [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) položku v dokumentaci k Windows SDK pro seznam polí jiná zpráva k dispozici. Výchozí hodnota poskytuje jednoduchou **OK** tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací celočíselnou hodnotu zadáním jednoho z položky nabídky hodnoty uvedené v [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) v dokumentaci k Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 `MessageBox`je užitečné při vývoji a jako snadný způsob, jak zobrazit chyba nebo upozornění uživateli.  
  
## <a name="see-also"></a>Viz také  
 [CWindowImpl – třída](../../atl/reference/cwindowimpl-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CComControlBase – třída](../../atl/reference/ccomcontrolbase-class.md)   
 [CComCompositeControl – třída](../../atl/reference/ccomcompositecontrol-class.md)
