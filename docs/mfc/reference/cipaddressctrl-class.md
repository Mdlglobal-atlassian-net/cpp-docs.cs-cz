---
title: "Třída CIPAddressCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
dev_langs:
- C++
helpviewer_keywords:
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 67c775f314cc70da1b662ca9b9c5f0a2e68eb2bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl – třída
Poskytuje funkci ovládacím prvku Windows běžné adres IP.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CIPAddressCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Vytvoří `CIPAddressCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Vymaže obsah ovládací prvek adresy IP.|  
|[CIPAddressCtrl::Create](#create)|Vytvoří ovládací prvek adresy IP a připojí jej k `CIPAddressCtrl` objektu.|  
|[CIPAddressCtrl::CreateEx](#createex)|Vytvoří ovládací prvek IP adresu s zadaný Windows rozšířené styly a připojí jej k `CIPAddressCtrl` objektu.|  
|[CIPAddressCtrl::GetAddress](#getaddress)|Načte hodnoty adres pro všechny čtyři pole v ovládací prvek adresy IP.|  
|[CIPAddressCtrl::IsBlank](#isblank)|Určuje, zda všechna pole v ovládacím prvku IP adres prázdný.|  
|[CIPAddressCtrl::SetAddress](#setaddress)|Nastaví hodnoty adres pro všechny čtyři pole v ovládací prvek adresy IP.|  
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Nastaví fokus klávesnice v zadaném poli ovládací prvek adresy IP.|  
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Nastaví rozsah v zadaném poli ovládací prvek adresy IP.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvek IP adresu, podobně jako ovládací prvek upravit ovládacího prvku umožňuje zadat a upravit číselnou adresu ve formátu Internet Protocol (IP).  
  
 Tento ovládací prvek (a proto `CIPAddressCtrl` třída) je k dispozici pouze pro aplikace běžící v rámci aplikace Microsoft Internet Explorer 4.0 a novější. Také bude k dispozici v budoucích verzích systému Windows a Windows NT.  
  
 Další obecné informace o ovládací prvek adresy IP, najdete v části [ovládací prvky IP adresu](http://msdn.microsoft.com/library/windows/desktop/bb761372) ve Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CIPAddressCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl  
 Vytvoří `CIPAddressCtrl` objektu.  
  
```  
CIPAddressCtrl();
```  
  
##  <a name="clearaddress"></a>CIPAddressCtrl::ClearAddress  
 Vymaže obsah ovládací prvek adresy IP.  
  
```  
void ClearAddress();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [IPM_CLEARADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761377), jak je popsáno v sadě Windows SDK.  
  
##  <a name="create"></a>CIPAddressCtrl::Create  
 Vytvoří ovládací prvek adresy IP a připojí jej k `CIPAddressCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Styl ovládací prvek adresy IP. Použijte kombinaci styly oken. Musí zahrnovat **ws_child –** styl, protože ovládací prvek musí být podřízeného okna. V tématu [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) ve Windows SDK pro seznam styly systému windows.  
  
 `rect`  
 Odkaz na velikost a umístění ovládací prvek adresy IP. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura.  
  
 `pParentWnd`  
 Ukazatel do nadřazeného okna Ovládací prvek adresy IP. Nesmí být **hodnotu NULL.**  
  
 `nID`  
 ID ovládací prvek adresy IP.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se inicializace byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CIPAddressCtrl` objektu ve dvou krocích.  
  
1.  Volání konstruktoru, který vytvoří `CIPAddressCtrl` objektu.  
  
2.  Volání **vytvořit**, která vytvoří ovládací prvek adresy IP.  
  
 Pokud chcete použít rozšířené windows styly s ovládacím prvkem, zavolejte [CreateEx](#createex) místo **vytvořit**.  
  
##  <a name="createex"></a>CIPAddressCtrl::CreateEx  
 Volání této funkce vytvoření ovládacího prvku (podřízeného okna) a její přidružení `CIPAddressCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Určuje styl rozšířené vytváří ovládacího prvku. Seznam rozšířené styly Windows najdete v tématu `dwExStyle` parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 `dwStyle`  
 Styl ovládací prvek adresy IP. Použijte kombinaci styly oken. Musí zahrnovat **ws_child –** styl, protože ovládací prvek musí být podřízeného okna. V tématu [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) ve Windows SDK pro seznam styly systému windows.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující velikost a umístění okna byly vytvořeny v souřadnice klienta `pParentWnd`.  
  
 `pParentWnd`  
 Ukazatel na okně, které je nadřazeného ovládacího prvku.  
  
 `nID`  
 ID ovládacího prvku podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určeného předponu rozšířené styl Windows **WS_EX_**.  
  
##  <a name="getaddress"></a>CIPAddressCtrl::GetAddress  
 Načte hodnoty adres pro všechny čtyři pole v ovládací prvek adresy IP.  
  
```  
int GetAddress(
    BYTE& nField0,  
    BYTE& nField1,  
    BYTE& nField2,  
    BYTE& nField3);  
  
int GetAddress(DWORD& dwAddress);
```  
  
### <a name="parameters"></a>Parametry  
 `nField0`  
 Odkaz na hodnotě pole 0 z sbalené IP adresy.  
  
 `nField1`  
 Odkaz na hodnotě pole 1 z sbalené IP adresy.  
  
 `nField2`  
 Odkaz na hodnotě pole 2 z sbalené IP adresy.  
  
 `nField3`  
 Odkaz na hodnotě pole 3 z sbalené IP adresy.  
  
 `dwAddress`  
 Odkaz na adresu `DWORD` hodnotu, která přijímá IP adresu. V tématu **poznámky** pro tabulku, která ukazuje, jak `dwAddress` je vyplněna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet neprázdných polí v ovládací prvek adresy IP.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378), jak je popsáno v sadě Windows SDK. V první prototypu výše čísla v polích 0 až 3 ovládacího prvku, čtení zleva doprava v uvedeném pořadí, naplnit čtyři parametry. V druhé prototypu výše `dwAddress` je naplněn takto.  
  
|Pole|Služba BITS obsahující hodnota pole|  
|-----------|-------------------------------------|  
|0|24 do 31|  
|1|16 až 23|  
|2|8 až 15|  
|3|0 až 7|  
  
##  <a name="isblank"></a>CIPAddressCtrl::IsBlank  
 Určuje, zda všechna pole v ovládacím prvku IP adres prázdný.  
  
```  
BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud všechna pole ovládací prvek adresy IP jsou prázdná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [IPM_ISBLANK](http://msdn.microsoft.com/library/windows/desktop/bb761379), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setaddress"></a>CIPAddressCtrl::SetAddress  
 Nastaví hodnoty adres pro všechny čtyři pole v ovládací prvek adresy IP.  
  
```  
void SetAddress(
    BYTE nField0,  
    BYTE nField1,  
    BYTE nField2,  
    BYTE nField3);  
  
void SetAddress(DWORD dwAddress);
```  
  
### <a name="parameters"></a>Parametry  
 `nField0`  
 Hodnota pole 0 z sbalené IP adresy.  
  
 `nField1`  
 Hodnota pole 1 z sbalené IP adresy.  
  
 `nField2`  
 Hodnota pole 2 z sbalené IP adresy.  
  
 `nField3`  
 Hodnota pole 3 z sbalené IP adresy.  
  
 `dwAddress`  
 A `DWORD` hodnotu, která obsahuje novou IP adresu. V tématu **poznámky** pro tabulku, která ukazuje, jak `DWORD` hodnota je vyplněna.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380), jak je popsáno v sadě Windows SDK. V první prototypu výše čísla v polích 0 až 3 ovládacího prvku, čtení zleva doprava v uvedeném pořadí, naplnit čtyři parametry. V druhé prototypu výše `dwAddress` je naplněn takto.  
  
|Pole|Služba BITS obsahující hodnota pole|  
|-----------|-------------------------------------|  
|0|24 do 31|  
|1|16 až 23|  
|2|8 až 15|  
|3|0 až 7|  
  
##  <a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus  
 Nastaví fokus klávesnice v zadaném poli ovládací prvek adresy IP.  
  
```  
void SetFieldFocus(WORD nField);
```  
  
### <a name="parameters"></a>Parametry  
 `nField`  
 Index počítaný od nuly pole, do které by měla být nastavena fokus. Pokud tato hodnota je vyšší než počet polí, fokus nastavená na první prázdné pole. Pokud jsou všechna pole prázdná, fokus nastavená na první pole.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [IPM_SETFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb761381), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange  
 Nastaví rozsah v zadaném poli ovládací prvek adresy IP.  
  
```  
void SetFieldRange(
    int nField,  
    BYTE nLower,  
    BYTE nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 `nField`  
 Index počítaný od nuly pole, do které se použijí v rozsahu.  
  
 `nLower`  
 Odkaz na typ integer příjem dolní limit dané pole ve tento ovládací prvek adresy IP.  
  
 `nUpper`  
 Odkaz na typ integer příjem horní limit počtu dané pole ve tento ovládací prvek adresy IP.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [IPM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761382), jak je popsáno v sadě Windows SDK. Použít dva parametry `nLower` a `nUpper`, k označení horní a dolní mez v poli místo *wRange* parametr použít se zprávou Win32.  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



