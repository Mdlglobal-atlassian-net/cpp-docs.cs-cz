---
title: Cnetaddressctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
dev_langs:
- C++
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b035f496a8daf34334d6e3a6690046c862795dc9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714555"
---
# <a name="cnetaddressctrl-class"></a>CNetAddressCtrl – třída
`CNetAddressCtrl` Třída reprezentuje ovládacího prvku síťové adresy, které můžete použít k zadání a ověření formátu protokolu IPv4, IPv6 a pojmenovaných adres DNS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CNetAddressCtrl : public CEdit  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|Vytvoří `CNetAddressCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CNetAddressCtrl::Create](#create)|Vytvoří ovládací prvek adresy sítě se zadaným styly a připojí ho k aktuální `CNetAddressCtrl` objektu.|  
|[CNetAddressCtrl::CreateEx](#createex)|Vytvoří ovládací prvek adresy sítě se zadaným rozšířené styly a připojí ho k aktuální `CNetAddressCtrl` objektu.|  
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Zobrazení tipu v bublině chyba zobrazí, když uživatel zadá adresu nepodporovanou síť v aktuální ovládací prvek síťové adresy.|  
|[CNetAddressCtrl::GetAddress](#getaddress)|Získá ověřených a Analyzovaná reprezentace síťové adresy přidružené k aktuálnímu ovládacímu prvku síťové adresy.|  
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Načte typ síťové adresy, který podporuje ovládací prvek adresy aktuální sítě.|  
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Nastaví typ síťové adresy, který podporuje ovládací prvek adresy aktuální sítě.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládacího prvku síťové adresy ověří, zda je správný formát, který uživatel zadá adresu. Ovládací prvek nepřipojí ve skutečnosti k síťovou adresu. [CNetAddressCtrl::SetAllowType](#setallowtype) metody Určuje jeden nebo více typů adresy, která [CNetAddressCtrl::GetAddress](#getaddress) metoda můžete analyzovat a ověřit. Adresa může být ve formě IPv4, IPv6 nebo pojmenované adresy serveru, sítě, hostitele nebo cíl zprávy všesměrového vysílání. Pokud nemá správný formát adresy, můžete použít [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodu pro zobrazení okno se zprávou informační tip, který graficky bodů do textového pole ovládacího prvku síťové adresy a zobrazí i předdefinovanou chybová zpráva.  
  
 `CNetAddressCtrl` Je třída odvozena z [CEdit](../../mfc/reference/cedit-class.md) třídy. V důsledku toho ovládacího prvku síťové adresy poskytuje přístup k všechny zprávy upravit ovládací prvek Windows.  
  
 Následující obrázek znázorňuje dialogového okna, která obsahuje ovládací prvek sítě. Textového pole (1) pro ovládacího prvku síťové adresy obsahuje neplatný síťovou adresu. Pokud síťová adresa není platná, zobrazí se zpráva informační Tip (2).  
  
 ![Dialogové okno s ovládacím prvkem síťové adresy a informační tip. ](../../mfc/reference/media/cnetaddctrl.png "cnetaddctrl")  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je část dialogového okna, která ověřuje síťovou adresu. Obslužné rutiny událostí pro tři přepínačů určete síťová adresa může být jeden ze tří typů adresu. Uživatel zadá do textového pole ovládacího prvku síťové adresy a stiskne tlačítko Ověřit adresu. Pokud se jedná o platnou adresu, zobrazí se zpráva o úspěchu; v opačném případě se zobrazí chybová zpráva předdefinované informační tip.  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ze souboru záhlaví dialogového okna definuje [NC_ADDRESS](/windows/desktop/api/shellapi/ns-shellapi-tagnc_address) a [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) proměnné, které jsou vyžadované [CNetAddressCtrl::GetAddress](#getaddress)metody.  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cedit –](../../mfc/reference/cedit-class.md)  
  
 `CNetAddressCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
 Tato třída je podporován v systému Windows Vista nebo novější.  
  
 Další požadavky pro tuto třídu jsou popsány v [vytvářet požadavky pro Windows Vista běžné ovládací prvky](../../mfc/build-requirements-for-windows-vista-common-controls.md).  
  
##  <a name="cnetaddressctrl"></a>  CNetAddressCtrl::CNetAddressCtrl  
 Vytvoří `CNetAddressCtrl` objektu.  
  
```  
CNetAddressCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
 Použití [CNetAddressCtrl::Create](#create) nebo [CNetAddressCtrl::CreateEx](#createex) metodu pro vytvoření ovládacího prvku sítě a připojte ji k `CNetAddressCtrl` objektu.  
  
##  <a name="create"></a>  CNetAddressCtrl::Create  
 Vytvoří ovládací prvek adresy sítě se zadaným styly a připojí ho k aktuální `CNetAddressCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*dwStyle*|[in] Bitová kombinace hodnot styly použité na ovládací prvek. Další informace najdete v tématu [upravit styly](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|  
|*Rect*|[in] Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturu, která obsahuje umístění a velikost ovládacího prvku.|  
|*pParentWnd*|[in] Nenulový ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku.|  
|*nID*|[in] ID ovládacího prvku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.  
  
##  <a name="createex"></a>  CNetAddressCtrl::CreateEx  
 Vytvoří ovládací prvek adresy sítě se zadaným rozšířené styly a připojí ho k aktuální `CNetAddressCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,   
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*dwExStyle*|[in] Bitová kombinace (nebo) rozšířené stylů pro ovládací prvek. Další informace najdete v tématu *dwExStyle* parametr [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) funkce.|  
|*dwStyle*|[in] Bitová kombinace (nebo) stylů pro ovládací prvek. Další informace najdete v tématu [upravit styly](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|  
|*Rect*|[in] Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturu, která obsahuje umístění a velikost ovládacího prvku.|  
|*pParentWnd*|[in] Nenulový ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku.|  
|*nID*|[in] ID ovládacího prvku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.  
  
##  <a name="displayerrortip"></a>  CNetAddressCtrl::DisplayErrorTip  
 V bublině tipu, který je přidružený aktuální ovládací prvek síťové adresy zobrazí chybovou zprávu.  
  
```  
HRESULT DisplayErrorTip();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota `S_OK` Pokud tato metoda je úspěšná, jinak kód chyby.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CNetAddressCtrl::SetAllowType](#setallowtype) metodu pro určení typů adresy, které může podporovat ovládacího prvku aktuální síťové adresy. Použití [CNetAddressCtrl::GetAddress](#getaddress) metodu k ověření a analyzovat síťovou adresu, která uživatel zadá. Použití [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metoda se zobrazí chybová zpráva tip, pokud [CNetAddressCtrl::GetAddress](#getaddress) metoda neproběhne úspěšně.  
  
 Vyvolá tuto zprávu [NetAddr_DisplayErrorTip](/windows/desktop/api/shellapi/nf-shellapi-netaddr_displayerrortip) makra, která je popsána v sadě Windows SDK. Toto makro odešle `NCM_DISPLAYERRORTIP` zprávy.  
  
##  <a name="getaddress"></a>  CNetAddressCtrl::GetAddress  
 Získá ověřených a Analyzovaná reprezentace síťové adresy, který je přidružený aktuální ovládací prvek síťové adresy.  
  
```  
HRESULT GetAddress(PNC_ADDRESS pAddress) const;  
```  
  
### <a name="parameters"></a>Parametry  

*pAddress*<br/>
[out v] Ukazatel [NC_ADDRESS](/windows/desktop/api/shellapi/ns-shellapi-tagnc_address) struktury.  Nastavte *pAddrInfo* člena této struktury na adresu [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) strukturu před voláním metody GetAddress.
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota S_OK, pokud tato metoda je úspěšná. jinak kód chyby modelu COM. Další informace o kódech chyb najdete v části vrátit hodnotu z [NetAddr_GetAddress](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getaddress) – makro.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato metoda je úspěšná, [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) struktura obsahuje další informace o síťové adrese.  
  
 Použití [CNetAddressCtrl::SetAllowType](#setallowtype) metodu pro určení typů ovládacího prvku aktuální síťové adresy může podporovat adresy. Použití [CNetAddressCtrl::GetAddress](#getaddress) metodu k ověření a analyzovat síťovou adresu, která uživatel zadá. Použití [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metoda se zobrazí chybová zpráva tip, pokud [CNetAddressCtrl::GetAddress](#getaddress) metoda neproběhne úspěšně.  
  
 Tato metoda vyvolá [NetAddr_GetAddress](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getaddress) makra, která je popsána v sadě Windows SDK. Toto makro odešle zprávu NCM_GETADDRESS.  
  
##  <a name="getallowtype"></a>  CNetAddressCtrl::GetAllowType  
 Načte typ síťové adresy, který podporuje ovládací prvek adresy aktuální sítě.  
  
```  
DWORD GetAllowType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitová kombinace (nebo) příznaky určující typy adres může podporovat ovládacího prvku síťové adresy. Další informace najdete v tématu [NET_STRING](https://msdn.microsoft.com/library/windows/desktop/bb762586).  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá tuto zprávu [NetAddr_GetAllowType](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getallowtype) makra, která je popsána v sadě Windows SDK. Toto makro odešle zprávu NCM_GETALLOWTYPE.  
  
##  <a name="setallowtype"></a>  CNetAddressCtrl::SetAllowType  
 Nastaví typ síťové adresy, který podporuje ovládací prvek adresy aktuální sítě.  
  
```  
HRESULT SetAllowType(DWORD dwAddrMask);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*dwAddrMask*|[in] Bitová kombinace (nebo) příznaky určující typy adres může podporovat ovládacího prvku síťové adresy. Další informace najdete v tématu [NET_STRING](https://msdn.microsoft.com/library/windows/desktop/bb762586).|  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud tato metoda je úspěšná. jinak kód chyby modelu COM.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CNetAddressCtrl::SetAllowType](#setallowtype) metodu pro určení typů adresy, které může podporovat ovládacího prvku aktuální síťové adresy. Použití [CNetAddressCtrl::GetAddress](#getaddress) metodu k ověření a analyzovat síťovou adresu, která uživatel zadá. Použití [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metoda se zobrazí chybová zpráva tip, pokud [CNetAddressCtrl::GetAddress](#getaddress) metoda neproběhne úspěšně.  
  
 Vyvolá tuto zprávu [NetAddr_SetAllowType](/windows/desktop/api/shellapi/nf-shellapi-netaddr_setallowtype) makra, která je popsána v sadě Windows SDK. Toto makro odešle zprávu NCM_SETALLOWTYPE.  
  
## <a name="see-also"></a>Viz také  
 [Cnetaddressctrl – třída](../../mfc/reference/cnetaddressctrl-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)
