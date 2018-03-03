---
title: "CSpinButtonCtrl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
dev_langs:
- C++
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b00fc554c6ca677756cf6a9a9c7fa83cd9d255f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl – třída
Poskytuje funkci ovládacím prvku tlačítko typu číselník běžné Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Vytvoří `CSpinButtonCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSpinButtonCtrl::Create](#create)|Ovládací prvek číselníku vytvoří a připojí jej k `CSpinButtonCtrl` objektu.|  
|[CSpinButtonCtrl::CreateEx](#createex)|Vytvoří ovládací prvek typu číselník tlačítko s zadaný Windows rozšířené styly a připojí jej k `CSpinButtonCtrl` objektu.|  
|[CSpinButtonCtrl::GetAccel](#getaccel)|Načte informace akcelerace pro ovládací prvek typu číselník tlačítko.|  
|[CSpinButtonCtrl::GetBase](#getbase)|Načte aktuální základ pro ovládací prvek typu číselník tlačítko.|  
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Načte ukazatel na aktuální kamarád okno.|  
|[CSpinButtonCtrl::GetPos](#getpos)|Načte aktuální pozici ovládací prvek typu číselník tlačítko.|  
|[CSpinButtonCtrl::GetRange](#getrange)|Načte horní a dolní meze (oblast) pro ovládací prvek typu číselník tlačítko.|  
|[CSpinButtonCtrl::SetAccel](#setaccel)|Nastaví akcelerace pro ovládací prvek typu číselník tlačítko.|  
|[CSpinButtonCtrl::SetBase](#setbase)|Nastaví základ pro ovládací prvek typu číselník tlačítko.|  
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Nastaví kamarád okna pro ovládací prvek typu číselník tlačítko.|  
|[CSpinButtonCtrl::SetPos](#setpos)|Nastaví aktuální pozici pro ovládací prvek.|  
|[CSpinButtonCtrl::SetRange](#setrange)|Nastaví horní a dolní meze (oblast) pro ovládací prvek typu číselník tlačítko.|  
  
## <a name="remarks"></a>Poznámky  
 "Typu číselník prvek tlačítko" (také označované jako ovládacího prvku číselník) je pár tlačítek který uživatel může kliknout a zvýší nebo sníží hodnotu, jako je například pozici posunutí nebo číslo zobrazené v ovládacím prvku doprovodné. Hodnota přidružená ovládací prvek typu číselník nazývá své aktuální pozici. Ovládací prvek číselníku se nejčastěji používá s ovládacím prvkem doprovodné názvem "kamarád okna."  
  
 Tento ovládací prvek (a proto `CSpinButtonCtrl` třída) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Pro uživatele ovládací prvek typu číselník a jeho kamarád okna často vypadat jako jeden ovládací prvek. Můžete zadat, ovládací prvek typu číselník umožňuje automatické umísťování samotné vedle jeho kamarád okna a jeho automaticky nastaví titulek okna kamarád na aktuální pozici. Ovládací prvek typu číselník tlačítko s ovládacím prvkem upravit slouží k požádat uživatele o číselný vstup.  
  
 Kliknutím na šipku nahoru Přesune aktuální pozice směrem k maximální a kliknutím na šipku dolů přesune aktuální pozice směrem k minimální. Ve výchozím nastavení minimální hodnota je 100 a maximální hodnota je 0. Když je větší než maximální nastavení (například pokud se používá výchozí nastavení), kliknutím na tlačítko nahoru snížení šipku nastavení minimální hodnota pozice a kliknutím na šipku dolů zvyšuje.  
  
 Ovládací prvek číselníku bez okno kamarád funguje jako řazení zjednodušené posuvníku. Například ovládacího prvku karta někdy zobrazí ovládací prvek typu číselník tlačítko pro povolení uživatelům přejděte do zobrazení další karty.  
  
 Další informace o používání `CSpinButtonCtrl`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md) a [pomocí CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="create"></a>CSpinButtonCtrl::Create  
 Ovládací prvek číselníku vytvoří a připojí jej k `CSpinButtonCtrl` objektu...  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl ovládacího prvku tlačítko otočení. Použít libovolnou kombinaci styly pro ovládací prvek typu číselník tlačítek do ovládacího prvku. Tyto styly jsou popsané v [styly ovládacího prvku číselník](http://msdn.microsoft.com/library/windows/desktop/bb759885) ve Windows SDK.  
  
 `rect`  
 Určuje velikost a umístění ovládacího prvku tlačítko otočení. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura  
  
 `pParentWnd`  
 Ukazatel na ovládací prvek tlačítko typu číselník nadřazené okno, obvykle `CDialog`. Nesmí být **hodnotu NULL.**  
  
 `nID`  
 Určuje ID ovládacího prvku tlačítko otočení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se inicializace byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CSpinButtonCtrl` objekt ve dvou krocích, volat konstruktor a pak zavolají **vytvořit**, které ovládací prvek typu číselník vytvoří a připojí jej k `CSpinButtonCtrl` objektu.  
  
 Chcete-li vytvořit ovládací prvek typu číselník tlačítko s rozšířené styly oken, volejte [CSpinButtonCtrl::CreateEx](#createex) místo **vytvořit**.  
  
##  <a name="createex"></a>CSpinButtonCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízeného okna) a přidruží ji s `CSpinButtonCtrl` objektu.  
  
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
 Určuje styl rozšířené vytváří ovládacího prvku. Seznam styly rozšířené windows najdete v tématu `dwExStyle` parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 `dwStyle`  
 Určuje styl ovládacího prvku tlačítko otočení. Použít libovolnou kombinaci styly pro ovládací prvek typu číselník tlačítek do ovládacího prvku. Tyto styly jsou popsané v [styly ovládacího prvku číselník](http://msdn.microsoft.com/library/windows/desktop/bb759885) ve Windows SDK.  
  
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
  
##  <a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl  
 Vytvoří `CSpinButtonCtrl` objektu.  
  
```  
CSpinButtonCtrl();
```  
  
##  <a name="getaccel"></a>CSpinButtonCtrl::GetAccel  
 Načte informace akcelerace pro ovládací prvek typu číselník tlačítko.  
  
```  
UINT GetAccel(
    int nAccel,  
    UDACCEL* pAccel) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nAccel`  
 Počet prvků v poli určeného `pAccel`.  
  
 `pAccel`  
 Ukazatele na pole [UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897) struktury, které obdrží akcelerace informace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet akcelerátoru struktury načíst.  
  
##  <a name="getbase"></a>CSpinButtonCtrl::GetBase  
 Načte aktuální základ pro ovládací prvek typu číselník tlačítko.  
  
```  
UINT GetBase() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnotu.  
  
##  <a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy  
 Načte ukazatel na aktuální kamarád okno.  
  
```  
CWnd* GetBuddy() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuální kamarád okno.  
  
##  <a name="getpos"></a>CSpinButtonCtrl::GetPos  
 Načte aktuální pozici ovládací prvek typu číselník tlačítko.  
  
```  
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpbError*  
 Ukazatel na logickou hodnotu, která je nastavena na nulu pokud hodnota je úspěšně načtena, nebo nenulové Pokud dojde k chybě. Pokud tento parametr je nastaven na **NULL**, nejsou hlášeny chyby.  
  
### <a name="return-value"></a>Návratová hodnota  
 První verze Vrátí 16bitové aktuální pozici v aplikaci word nejnižší. Horní slovo je nenulové hodnoty, pokud došlo k chybě.  
  
 Druhá verze vrátí pozici 32-bit.  
  
### <a name="remarks"></a>Poznámky  
 Při zpracování hodnota vrácená, aktualizuje ovládacího prvku založené na záhlaví okna kamarád aktuální pozici. Ovládací prvek vrátí chybu, pokud není okno kamarád nebo pokud titulek určuje neplatná nebo out-of-range.  
  
##  <a name="getrange"></a>CSpinButtonCtrl::GetRange  
 Načte horní a dolní meze (oblast) pro ovládací prvek typu číselník tlačítko.  
  
```  
DWORD GetRange() const;  
  
void GetRange(
    int& lower,  
    int& upper) const;  
  
void GetRange32(
    int& lower,  
    int &upper) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nižší*  
 Odkaz na celé číslo, které obdrží nižší limit pro ovládací prvek.  
  
 *horní*  
 Odkaz na celé číslo, které obdrží horní limit pro ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 První verze vrací hodnotu 32-bit obsahující horní a dolní meze. Word nejnižší je horní limit pro ovládací prvek a word horní dolní limit.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce `GetRange32` načte rozsah ovládacího prvku tlačítko typu číselník jako 32bitové celé číslo.  
  
##  <a name="setaccel"></a>CSpinButtonCtrl::SetAccel  
 Nastaví akcelerace pro ovládací prvek typu číselník tlačítko.  
  
```  
BOOL SetAccel(
    int nAccel,  
    UDACCEL* pAccel);
```  
  
### <a name="parameters"></a>Parametry  
 `nAccel`  
 Počet [UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897) struktury určeného `pAccel`.  
  
 `pAccel`  
 Ukazatele na pole `UDACCEL` struktury, které obsahují informace akcelerace. Elementy musí být seřazeny ve vzestupném pořadí podle **nSec** člen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
##  <a name="setbase"></a>CSpinButtonCtrl::SetBase  
 Nastaví základ pro ovládací prvek typu číselník tlačítko.  
  
```  
int SetBase(int nBase);
```  
  
### <a name="parameters"></a>Parametry  
 `nBase`  
 Nová hodnota základní pro ovládací prvek. Může být 10 pro desetinná čísla nebo 16 pro šestnáctkové číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí základní hodnotu, pokud bylo úspěšné, nebo nula, pokud je zadána neplatná základní.  
  
### <a name="remarks"></a>Poznámky  
 Základní hodnota určuje, zda okno kamarád zobrazí čísla v desítkový nebo hexadecimální číslice. Hexadecimální číslice jsou vždy bez znaménka; desetinná čísla přihlášení.  
  
##  <a name="setbuddy"></a>CSpinButtonCtrl::SetBuddy  
 Nastaví kamarád okna pro ovládací prvek typu číselník tlačítko.  
  
```  
CWnd* SetBuddy(CWnd* pWndBuddy);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndBuddy`  
 Ukazatel na nové okno kamarád.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel do předchozího okna kamarád.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek typu číselník je téměř vždy přidružené další okno, jako je například textové pole, která zobrazuje obsah. Toto další okno se nazývá "kamarád" ovládací prvek typu číselník.  
  
##  <a name="setpos"></a>CSpinButtonCtrl::SetPos  
 Nastaví aktuální pozici pro ovládací prvek typu číselník tlačítko.  
  
```  
int SetPos(int nPos);  
int SetPos32(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Nové umístění pro ovládací prvek. Tato hodnota musí být v rozsahu určeném horní a dolní limity pro ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí pozici (16bitové přesnost pro `SetPos`32bitový přesností pro `SetPos32`).  
  
### <a name="remarks"></a>Poznámky  
 `SetPos32`Nastavuje pozici 32-bit.  
  
##  <a name="setrange"></a>CSpinButtonCtrl::SetRange  
 Nastaví horní a dolní meze (oblast) pro ovládací prvek typu číselník tlačítko.  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 `nLower`a`nUpper`  
 Horní a dolní limity pro ovládací prvek. Pro `SetRange`, ani omezení může být větší než **UD_MAXVAL** nebo menší než **UD_MINVAL**; kromě toho nesmí překročit rozdíl mezi dvěma limity **UD_MAXVAL**. `SetRange32`Nenastaví žádná omezení na omezení; použijte všechny celých čísel.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce `SetRange32` Nastaví rozsah 32bitové pro ovládací prvek typu číselník tlačítko.  
  
> [!NOTE]
>  Výchozí rozsah číselníku má nastaven na hodnotu nula (0) maximální a minimální nastavena na hodnotu 100. Vzhledem k tomu, že maximální hodnota je menší než minimální hodnota, kliknutím na šipku nahoru se sníží pozice a kliknutím na šipku dolů zvýší ho. Použití `CSpinButtonCtrl::SetRange` upravit tyto hodnoty.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL2 MFC](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CSliderCtrl – třída](../../mfc/reference/csliderctrl-class.md)
