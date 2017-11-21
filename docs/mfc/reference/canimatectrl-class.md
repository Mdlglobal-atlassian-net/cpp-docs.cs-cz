---
title: "CAnimateCtrl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
dev_langs: C++
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 30e36ec884b1f073eb3d061923687a4318c0138f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="canimatectrl-class"></a>CAnimateCtrl – třída
Poskytuje funkce Windows běžné ovládacího prvku animace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimateCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Vytvoří `CAnimateCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimateCtrl::Close](#close)|Zavře klip souborů AVI.|  
|[CAnimateCtrl::Create](#create)|Vytvoří ovládacího prvku animace a připojí jej k `CAnimateCtrl` objektu.|  
|[CAnimateCtrl::CreateEx](#createex)|Vytvoří se zadaný Windows rozšířené styly ovládacího prvku animace a připojí jej k `CAnimateCtrl` objektu.|  
|[CAnimateCtrl::IsPlaying](#isplaying)|Určuje, zda je přehrávání klip Audio a Video prokládaný (AVI).|  
|[CAnimateCtrl::Open](#open)|AVI klip ze souboru či prostředku se zobrazí první snímek.|  
|[CAnimateCtrl::Play](#play)|Hraje klip souborů AVI bez zvuku.|  
|[CAnimateCtrl::Seek](#seek)|Zobrazí vybraný jeden snímek systému souborů AVI klip.|  
|[CAnimateCtrl::Stop](#stop)|Ukončí přehrávání souborů AVI klip.|  
  
## <a name="remarks"></a>Poznámky  
 Tento ovládací prvek (a proto `CAnimateCtrl` třída) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95, Windows 98 a systému Windows NT 3.51 a novějším.  
  
 Ovládacího prvku animace je obdélníková okno, které zobrazí klip ve formátu AVI (Audio Video prokládaný) – ve standardním formátu video nebo zvuk systému Windows. Klip souborů AVI je řady rastrový obrázek snímků, jako jsou videa.  
  
 Ovládací prvky animace můžete přehrát pouze jednoduché souborů AVI klipů. Konkrétně klipů má být přehráván pomocí ovládacího prvku animace musí splňovat následující požadavky:  
  
-   Musí být přesně jeden datový proud videa a musí mít alespoň jeden rámce.  
  
-   Může být maximálně dvě datové proudy v souboru (obvykle další datový proud, pokud existuje, je zvukový stream, i když ovládacího prvku animace ignoruje zvuk informace).  
  
-   Klip musí být buď nekomprimovaným nebo komprimované s kompresí RLE8.  
  
-   Nejsou povoleny žádné změny palety v datový proud videa.  
  
 Klip souborů AVI můžete přidat do vaší aplikace jako prostředek souborů AVI nebo ho může být aplikace jako samostatný soubor AVI.  
  
 Vzhledem k tomu, že vaše vlákno pokračuje v provádění při souborů AVI klip se zobrazí, je jeden běžně používá pro ovládacího prvku animace indikovat aktivitu systému během časově náročná operace. Například dialogové okno Hledat v Průzkumníku souborů zobrazí přesunutí Lupa jako soubor výsledky hledání.  
  
 Pokud vytvoříte `CAnimateCtrl` objektů v rámci dialogové okno pole nebo z zdroj dialogového okna pomocí editoru dialogových oken, ji budou automaticky zničena při zavření dialogu.  
  
 Pokud vytvoříte `CAnimateCtrl` objektů v rámci časového období, budete muset zničte jej. Pokud vytvoříte `CAnimateCtrl` objektu v zásobníku, byla automaticky. Pokud vytvoříte `CAnimateCtrl` objektu v haldě pomocí **nové** funkce, musí volat **odstranit** na objekt, který má zničte jej. Pokud odvozujete novou třídu z `CAnimateCtrl` a přidělit paměť v dané třídě, přepsat `CAnimateCtrl` destruktor k odstranění přidělení.  
  
 Další informace o používání `CAnimateCtrl`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md) a [pomocí CAnimateCtrl](../../mfc/using-canimatectrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="canimatectrl"></a>CAnimateCtrl::CAnimateCtrl  
 Vytvoří `CAnimateCtrl` objektu.  
  
```  
CAnimateCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
 Je třeba zavolat [vytvořit](#create) – členská funkce před provedením další operace na objektu, který vytvoříte.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]  
  
##  <a name="close"></a>CAnimateCtrl::Close  
 Zavře klip souborů AVI, který byl dříve otevřen v ovládacím prvku animace (pokud existuje) a odebere ji z paměti.  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="create"></a>CAnimateCtrl::Create  
 Vytvoří ovládacího prvku animace a připojí jej k `CAnimateCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl ovládacího prvku animace. Použít libovolnou kombinaci windows podrobněji popsané v části poznámky níže a styly ovládacího prvku animace styly [styly ovládacího prvku animace](http://msdn.microsoft.com/library/windows/desktop/bb761886) ve Windows SDK.  
  
 `rect`  
 Určuje umístění a velikost ovládacího prvku animace. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](../../mfc/reference/rect-structure1.md) struktura.  
  
 `pParentWnd`  
 Určuje ovládacího prvku animace nadřazené okno, obvykle `CDialog`. Nesmí být **hodnotu NULL.**  
  
 `nID`  
 Určuje ID ovládacího prvku animace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CAnimateCtrl` ve dvou krocích. Nejprve volat konstruktor a pak zavolají **vytvořit**, který vytvoří ovládacího prvku animace a připojí jej k `CAnimateCtrl` objektu.  
  
 Použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do ovládacího prvku animace.  
  
- **Ws_child –** vždy  
  
- **Ws_visible –** obvykle  
  
- **Ws_disabled –** zřídka  
  
 Pokud chcete styly rozšířené windows pomocí vlastního ovládacího prvku animace, zavolejte [CreateEx](#createex) místo **vytvořit**.  
  
 Kromě styly oken, uvedených výše můžete použít jeden nebo více stylů ovládacího prvku animace do ovládacího prvku animace. Sada Windows SDK pro další informace najdete na [styly ovládacího prvku animace](http://msdn.microsoft.com/library/windows/desktop/bb761886).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="createex"></a>CAnimateCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízeného okna) a přidruží ji s `CAnimateCtrl` objektu.  
  
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
 Určuje styl ovládacího prvku animace. Použít libovolnou kombinaci okna a styly ovládacího prvku animace popsaných v [styly ovládacího prvku animace](http://msdn.microsoft.com/library/windows/desktop/bb761886) ve Windows SDK.  
  
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
  
##  <a name="isplaying"></a>CAnimateCtrl::IsPlaying  
 Určuje, zda je přehrávání klip Audio a Video prokládaný (AVI).  
  
```  
BOOL IsPlaying() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je AVI klip přehrávání; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [ACM_ISPLAYING](http://msdn.microsoft.com/library/windows/desktop/bb761895) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="open"></a>CAnimateCtrl::Open  
 Volání této funkce otevřete klip souborů AVI a zobrazíte jeho první snímek.  
  
```  
BOOL Open(LPCTSTR lpszFileName);  
BOOL Open(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 A `CString` objekt nebo ukazatel na řetězec ukončené hodnotou null, který obsahuje buď název souboru AVI nebo název prostředek souborů AVI. Pokud tento parametr je **NULL**, systém zavře klip souborů AVI, který byl dříve otevřen pro ovládacího prvku animace, pokud existuje.  
  
 `nID`  
 Identifikátor prostředku souborů AVI. Pokud tento parametr je **NULL**, systém zavře klip souborů AVI, který byl dříve otevřen pro ovládacího prvku animace, pokud existuje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Prostředek souborů AVI je načten z modulu, který vytvořili ovládacího prvku animace.  
  
 **Otevřete** AVI klip; nepodporuje zvuk můžete otevřít jenom tichou souborů AVI klipů.  
  
 Pokud má ovládacího prvku animace `ACS_AUTOPLAY` styl ovládacího prvku animace bude automaticky spustit přehrávání klip ihned po jeho otevření. Přehrávání klip na pozadí, zatímco vaše vlákno pokračuje v provádění bude pokračovat. Po dokončení klip přehrávání, ji budou automaticky opakovat.  
  
 Pokud má ovládacího prvku animace `ACS_CENTER` styl, klip souborů AVI bude umístěn na střed v ovládacím prvku a nedojde ke změně velikosti ovládacího prvku. Pokud nemá ovládacího prvku animace `ACS_CENTER` styl ovládacího prvku bude nastavena velikost po otevření souborů AVI klip velikost bitové kopie v klip souborů AVI. Pozice levého horního rohu ovládacího prvku nedojde ke změně, velikost ovládacího prvku.  
  
 Pokud má ovládacího prvku animace `ACS_TRANSPARENT` styl, první snímek budou vykreslovat pomocí průhledné pozadí místo barvu pozadí zadaný v klip animace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="play"></a>CAnimateCtrl::Play  
 Volání této funkce přehrávání AVI klip v ovládacím prvku animace.  
  
```  
BOOL Play(
    UINT nFrom,  
    UINT nTo,  
    UINT nRep);
```  
  
### <a name="parameters"></a>Parametry  
 `nFrom`  
 Index rámečku, kde začíná přehrávání nule. Hodnota musí být menší než 65536. Hodnota 0 znamená začínat první snímek klip souborů AVI.  
  
 `nTo`  
 Index rámečku nule kde přehrávání elementy end. Hodnota musí být menší než 65536. Hodnota - 1 znamená končit klip souborů AVI s poslední snímek.  
  
 *nRep*  
 Počet pokusů o přehrání souborů AVI klip. Hodnota - 1 znamená přehráním soubor po neomezenou dobu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Ovládacího prvku animace se přehraje klip na pozadí, zatímco vaše vlákno pokračuje v provádění. Pokud má ovládacího prvku animace `ACS_TRANSPARENT` styl, klip souborů AVI přehrávané pomocí průhledné pozadí spíše než barvu pozadí zadaný v klip animace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="seek"></a>CAnimateCtrl::Seek  
 Volání této funkce na statické zobrazení jeden snímek klip souborů AVI.  
  
```  
BOOL Seek(UINT nTo);
```  
  
### <a name="parameters"></a>Parametry  
 `nTo`  
 Rámeček pro zobrazení index počítáno od nuly. Hodnota musí být menší než 65536. Hodnota 0 znamená zobrazení v klip souborů AVI první snímek. Hodnota -1 znamená zobrazení v klip souborů AVI poslední snímek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Pokud má ovládacího prvku animace `ACS_TRANSPARENT` styl, klip souborů AVI budou vykreslovat pomocí průhledné pozadí místo barvu pozadí zadaný v klip animace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="stop"></a>CAnimateCtrl::Stop  
 Volání této funkce přehrávání AVI klip v ovládacím prvku animace.  
  
```  
BOOL Stop();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](#create)   
 [ON_CONTROL –](message-map-macros-mfc.md#on_control)

