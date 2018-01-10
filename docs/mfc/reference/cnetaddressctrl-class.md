---
title: "Třída CNetAddressCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9a433d723e15d910674c129b1e62ca82c1de4bb0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cnetaddressctrl-class"></a>CNetAddressCtrl – třída
`CNetAddressCtrl` Třída reprezentuje ovládací prvek adresy sítě, který můžete použít k vstup a ověření formát IPv4 a IPv6, adresy s názvem DNS.  
  
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
|[CNetAddressCtrl::Create](#create)|Vytvoří adresu ovládacího prvku sítě s zadaný styly a připojí k aktuální `CNetAddressCtrl` objektu.|  
|[CNetAddressCtrl::CreateEx](#createex)|Vytvoří adresu ovládacího prvku sítě s zadaný rozšířené styly a připojí k aktuální `CNetAddressCtrl` objektu.|  
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|K chybě v tipu zobrazí, když uživatel zadá adresu nepodporované sítě v aktuální ovládací prvek síťové adresy.|  
|[CNetAddressCtrl::GetAddress](#getaddress)|Načte ověřená a Analyzovaná reprezentace síťové adresy přidružené k aktuální ovládací prvek síťové adresy.|  
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Načte typ síťové adresy, který může podporovat aktuální ovládací prvek síťové adresy.|  
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Nastaví typ síťové adresy, který může podporovat aktuální ovládací prvek síťové adresy.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvek adresy sítě ověřuje, zda je formát adresy, které uživatel zadá správný. Ovládací prvek nepřipojuje ke síťová adresa ve skutečnosti. [CNetAddressCtrl::SetAllowType](#setallowtype) metoda určuje jeden nebo více typů adresy, [CNetAddressCtrl::GetAddress](#getaddress) metoda můžete analyzovat a ověření. Adresa může být ve tvaru IPv4, IPv6, nebo s názvem adresu serveru, síti, hostitele nebo cíl zprávy všesměrového vysílání. Pokud není ve správném formátu adresy, můžete použít [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodu pro zobrazení okno zprávy informační tip, který graficky bodů do textového pole ovládacího prvku adresa sítě a zobrazí i předdefinovanou chybová zpráva.  
  
 `CNetAddressCtrl` Je třída odvozená z [CEdit](../../mfc/reference/cedit-class.md) třídy. V důsledku toho ovládací prvek adresy sítě poskytuje přístup k všechny zprávy ovládací prvek upravit systému Windows.  
  
 Následující obrázek znázorňuje dialog, který obsahuje ovládací prvek síťové adresy. Textové pole (1) pro ovládací prvek adresy sítě obsahuje neplatná síťová adresa. Pokud síťová adresa je neplatná, zobrazí se zpráva informační Tip (2).  
  
 ![Dialogové okno s ovládacím prvkem síťové adresy a informační tip. ] (../../mfc/reference/media/cnetaddctrl.png "cnetaddctrl")  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je část dialogového okna, která ověřuje adresu sítě. Obslužné rutiny události pro tři přepínací tlačítka zadejte síťová adresa může být jeden ze tří typů adresu. Uživatel zadá adresu do textového pole ovládacího prvku sítě a potom stiskne tlačítko Ověřit adresu. Pokud je adresa platnou, se zobrazí zpráva o úspěšném provedení; jinak se zobrazí chybová zpráva předdefinované informační tip.  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu z hlavičky souboru dialogové okno definuje [NC_ADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb773345) a [NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) proměnné, které jsou vyžadované [CNetAddressCtrl::GetAddress](#getaddress)metoda.  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CNetAddressCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
 Tato třída je podporována v [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] a novější.  
  
 Další požadavky pro tuto třídu, jsou popsané v [sestavení požadavky pro Windows Vista běžné ovládací prvky](../../mfc/build-requirements-for-windows-vista-common-controls.md).  
  
##  <a name="cnetaddressctrl"></a>CNetAddressCtrl::CNetAddressCtrl  
 Vytvoří `CNetAddressCtrl` objektu.  
  
```  
CNetAddressCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
 Použití [CNetAddressCtrl::Create](#create) nebo [CNetAddressCtrl::CreateEx](#createex) metodu pro vytvoření ovládacího prvku sítě a připojte ji k `CNetAddressCtrl` objektu.  
  
##  <a name="create"></a>CNetAddressCtrl::Create  
 Vytvoří adresu ovládacího prvku sítě s zadaný styly a připojí k aktuální `CNetAddressCtrl` objektu.  
  
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
|[v]`dwStyle`|Bitová kombinace styly použité pro ovládací prvek. Další informace najdete v tématu [upravit styly](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|  
|[v]`rect`|Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která obsahuje umístění a velikost ovládacího prvku.|  
|[v]`pParentWnd`|Ukazatel na jinou hodnotu než null [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku.|  
|[v]`nID`|ID ovládacího prvku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
##  <a name="createex"></a>CNetAddressCtrl::CreateEx  
 Vytvoří adresu ovládacího prvku sítě s zadaný rozšířené styly a připojí k aktuální `CNetAddressCtrl` objektu.  
  
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
|[v]`dwExStyle`|Bitová kombinace (nebo) rozšířené stylů má být použita pro ovládací prvek. Další informace najdete v tématu `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkce.|  
|[v]`dwStyle`|Bitová kombinace (nebo) stylů má být použita pro ovládací prvek. Další informace najdete v tématu [upravit styly](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|  
|[v]`rect`|Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která obsahuje umístění a velikost ovládacího prvku.|  
|[v]`pParentWnd`|Ukazatel na jinou hodnotu než null [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku.|  
|[v]`nID`|ID ovládacího prvku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
##  <a name="displayerrortip"></a>CNetAddressCtrl::DisplayErrorTip  
 Zobrazí chybová zpráva v bublině tip, který je přidružen aktuální ovládací prvek adresy sítě.  
  
```  
HRESULT DisplayErrorTip();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota `S_OK` Pokud tato metoda je úspěšné, jinak hodnota chybový kód.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CNetAddressCtrl::SetAllowType](#setallowtype) metoda určit typy adres, které může podporovat aktuální ovládací prvek síťové adresy. Použití [CNetAddressCtrl::GetAddress](#getaddress) metodu pro ověření a analyzovat síťovou adresu, která uživatel zadá. Použití [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodu pro zobrazení tip chybová zpráva, pokud [CNetAddressCtrl::GetAddress](#getaddress) metoda neúspěšná.  
  
 Vyvolá se tato zpráva [NetAddr_DisplayErrorTip](http://msdn.microsoft.com/library/windows/desktop/bb774314) makro, který je popsán v sadě Windows SDK. Odešle tento makro `NCM_DISPLAYERRORTIP` zprávy.  
  
##  <a name="getaddress"></a>CNetAddressCtrl::GetAddress  
 Načte ověřená a Analyzovaná reprezentace síťové adresy, která souvisí s aktuální ovládací prvek síťové adresy.  
  
```  
HRESULT GetAddress(PNC_ADDRESS pAddress) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[ve out]`pAddress`|Ukazatel na [NC_ADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb773345) struktury.  Nastavte `pAddrInfo` členem tato struktura na adresu [NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) struktury před voláním getaddress – metoda.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota `S_OK` Pokud tato metoda je úspěšné, jinak hodnota COM kód chyby. Další informace o možných chybové kódy, najdete v části vrátit hodnotu [NetAddr_GetAddress](http://msdn.microsoft.com/library/windows/desktop/bb774316) makro.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato metoda je úspěšné, [NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) struktura obsahuje další informace o síťové adrese.  
  
 Použití [CNetAddressCtrl::SetAllowType](#setallowtype) metoda určit typy adres může podporovat aktuální ovládací prvek síťové adresy. Použití [CNetAddressCtrl::GetAddress](#getaddress) metodu pro ověření a analyzovat síťovou adresu, která uživatel zadá. Použití [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodu pro zobrazení tip chybová zpráva, pokud [CNetAddressCtrl::GetAddress](#getaddress) metoda neúspěšná.  
  
 Tato metoda vyvolá [NetAddr_GetAddress](http://msdn.microsoft.com/library/windows/desktop/bb774316) makro, který je popsán v sadě Windows SDK. Odešle tento makro `NCM_GETADDRESS` zprávy.  
  
##  <a name="getallowtype"></a>CNetAddressCtrl::GetAllowType  
 Načte typ síťové adresy, který může podporovat aktuální ovládací prvek síťové adresy.  
  
```  
DWORD GetAllowType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitová kombinace (nebo) příznaky určující typy adresy ovládací prvek adresy sítě může podporovat. Další informace najdete v tématu [NET_STRING](http://msdn.microsoft.com/library/windows/desktop/bb762586).  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá se tato zpráva [NetAddr_GetAllowType](http://msdn.microsoft.com/library/windows/desktop/bb774318) makro, který je popsán v sadě Windows SDK. Odešle tento makro `NCM_GETALLOWTYPE` zprávy.  
  
##  <a name="setallowtype"></a>CNetAddressCtrl::SetAllowType  
 Nastaví typ síťové adresy, který může podporovat aktuální ovládací prvek síťové adresy.  
  
```  
HRESULT SetAllowType(DWORD dwAddrMask);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`dwAddrMask`|Bitová kombinace (nebo) příznaky určující typy adresy ovládací prvek adresy sítě může podporovat. Další informace najdete v tématu [NET_STRING](http://msdn.microsoft.com/library/windows/desktop/bb762586).|  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud tato metoda je úspěšná. jinak kód chyby COM.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CNetAddressCtrl::SetAllowType](#setallowtype) metoda určit typy adres, které může podporovat aktuální ovládací prvek síťové adresy. Použití [CNetAddressCtrl::GetAddress](#getaddress) metodu pro ověření a analyzovat síťovou adresu, která uživatel zadá. Použití [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodu pro zobrazení tip chybová zpráva, pokud [CNetAddressCtrl::GetAddress](#getaddress) metoda neúspěšná.  
  
 Vyvolá se tato zpráva [NetAddr_SetAllowType](http://msdn.microsoft.com/library/windows/desktop/bb774320) makro, který je popsán v sadě Windows SDK. Odešle tento makro `NCM_SETALLOWTYPE` zprávy.  
  
## <a name="see-also"></a>Viz také  
 [CNetAddressCtrl – třída](../../mfc/reference/cnetaddressctrl-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)
