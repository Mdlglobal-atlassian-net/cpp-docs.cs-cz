---
title: Canimatectrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b8f9f99b38d2878025546379a185aef53bb663
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213766"
---
# <a name="canimatectrl-class"></a>Canimatectrl – třída
Poskytuje funkce pro Windows běžný ovládací prvek animace.  
  
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
|[CAnimateCtrl::Close](#close)|Zavře klip AVI.|  
|[CAnimateCtrl::Create](#create)|Vytvoří ovládací prvek animace a připojí ho k `CAnimateCtrl` objektu.|  
|[CAnimateCtrl::CreateEx](#createex)|Vytvoří ovládací prvek animace se zadaným rozšířené styly Windows a připojí ho k `CAnimateCtrl` objektu.|  
|[CAnimateCtrl::IsPlaying](#isplaying)|Určuje, zda je přehrávání klipu Audio a Video prokládané (AVI).|  
|[CAnimateCtrl::Open](#open)|Otevře klip AVI ze souboru nebo prostředku a zobrazí prvního rámce.|  
|[CAnimateCtrl::Play](#play)|Přehraje klip AVI bez zvuku.|  
|[CAnimateCtrl::Seek](#seek)|Zobrazí vybraný jediný snímek klip AVI.|  
|[CAnimateCtrl::Stop](#stop)|Přehrávat klip AVI se zastaví.|  
  
## <a name="remarks"></a>Poznámky  
 Tento ovládací prvek (a tedy `CAnimateCtrl` třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95, Windows 98 a Windows NT verze 3.51 a vyšší.  
  
 Je ovládacího prvku animace obdélníkové okno zobrazující klip AVI (zvuk videa prokládané) formát – standardní video nebo Zvuk formátu Windows. Klip AVI je řada rastrového obrázku rámce, jako jsou videa.  
  
 Ovládací prvky animace můžete přehrát pouze jednoduché AVI klipy. Konkrétně klipy přehrávat pomocí ovládacího prvku animace musí splňovat následující požadavky:  
  
-   Musí být přesně jeden datový proud videa a musí mít aspoň jeden snímek.  
  
-   Může existovat nejvýše dva datové proudy v souboru (obvykle jiný datový proud, pokud jsou k dispozici, je zvukový datový proud, i když se ovládací prvek animace ignoruje zvuku informace).  
  
-   Klip musí být buď nekomprimovaný nebo komprimována pomocí RLE8 komprese.  
  
-   Ve streamu videa nejsou povoleny žádné změny palety.  
  
 Klip AVI můžete přidat do vaší aplikace jako prostředek AVI nebo ji může doprovázet jako samostatný soubor AVI vaší aplikace.  
  
 Vzhledem k tomu, že vaše vlákno pokračuje v provádění, když klip AVI se zobrazí, je jedno společné použití ovládacího prvku animace indikovat aktivitu systému během operace s delším průběhem. Například dialogové okno Najít Průzkumníka souborů zobrazí přesunutí Lupa jako systém vyhledá soubor.  
  
 Pokud jste vytvořili `CAnimateCtrl` objekt v rámci dialogového okna, pole nebo z prostředku dialogového okna pomocí editoru dialogového okna, je automaticky zničí při zavření dialogových oken.  
  
 Pokud jste vytvořili `CAnimateCtrl` objekt v rámci časového období, možná budete muset zničit ho. Pokud jste vytvořili `CAnimateCtrl` objekt v zásobníku, je automaticky zničen. Pokud jste vytvořili `CAnimateCtrl` objektů na haldě pomocí **nové** funkce, je nutné volat **odstranit** na objekt, který chcete odstranit ji. Pokud odvodit novou třídu z `CAnimateCtrl` a přidělení paměti v dané třídě, přepsat `CAnimateCtrl` destruktor k uvolnění přidělení.  
  
 Další informace o používání `CAnimateCtrl`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md) a [používání atributu CAnimateCtrl](../../mfc/using-canimatectrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="canimatectrl"></a>  CAnimateCtrl::CAnimateCtrl  
 Vytvoří `CAnimateCtrl` objektu.  
  
```  
CAnimateCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
 Je třeba zavolat [vytvořit](#create) členskou funkci před provedením jakékoli další operace na objektu, který vytvoříte.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]  
  
##  <a name="close"></a>  CAnimateCtrl::Close  
 Zavře klip AVI, který byl dříve otevřen v ovládacím prvku animace (pokud existuje) a odstraní ji z paměti.  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak nula.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="create"></a>  CAnimateCtrl::Create  
 Vytvoří ovládací prvek animace a připojí ho k `CAnimateCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Určuje styl ovládacího prvku animace. Použít libovolnou kombinaci systému windows, styly, které jsou popsány v následující části poznámky a – styly ovládacích prvků animace popsané v [– styly ovládacích prvků animace](/windows/desktop/Controls/animation-control-styles) v sadě Windows SDK.  
  
 *Rect*  
 Určuje pozici a velikost ovládacího prvku animace. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](../../mfc/reference/rect-structure1.md) struktury.  
  
 *pParentWnd*  
 Určuje nadřazené okno ovládacího prvku animace, obvykle `CDialog`. Nesmí být NULL.  
  
 *nID*  
 Určuje ID ovládacího prvku animace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak nula.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CAnimateCtrl` ve dvou krocích. Nejprve volat konstruktor a poté zavolejte `Create`, což vytvoří ovládací prvek animace a připojí ho k `CAnimateCtrl` objektu.  
  
 Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do ovládacího prvku animace.  
  
- WS_CHILD vždy  
  
- WS_VISIBLE obvykle  
  
- WS_DISABLED jen zřídka  
  
 Pokud chcete použít rozšířené windows styly ovládacího prvku animace, zavolejte [CreateEx](#createex) místo `Create`.  
  
 Kromě styly oken uvedené výše můžete použít jeden nebo více – styly ovládacích prvků animace ovládacího prvku animace. Sada Windows SDK pro další informace naleznete na [– styly ovládacích prvků animace](/windows/desktop/Controls/animation-control-styles).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="createex"></a>  CAnimateCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízené okno) a přidruží ji k `CAnimateCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwExStyle*  
 Určuje rozšířený styl ovládacího prvku vytváří. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](https://msdn.microsoft.com/library/windows/desktop/ms632680) v sadě Windows SDK.  
  
 *dwStyle*  
 Určuje styl ovládacího prvku animace. Použít libovolnou kombinaci okna a podle – styly ovládacích prvků animace [– styly ovládacích prvků animace](/windows/desktop/Controls/animation-control-styles) v sadě Windows SDK.  
  
 *Rect*  
 Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující, velikost a umístění okna, které nelze v souřadnice klienta *pParentWnd*.  
  
 *pParentWnd*  
 Ukazatel na okno, který je nadřazeného ovládacího prvku.  
  
 *nID*  
 ID ovládacího prvku podřízené okno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určené předponu rozšířeného stylu Windows **WS_EX_**.  
  
##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying  
 Určuje, zda je přehrávání klipu Audio a Video prokládané (AVI).  
  
```  
BOOL IsPlaying() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je přehrávání klip AVI; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [ACM_ISPLAYING](/windows/desktop/Controls/acm-isplaying) zprávu, která je popsána v sadě Windows SDK.  
  
##  <a name="open"></a>  CAnimateCtrl::Open  
 Voláním této funkce Otevřít klip AVI a zobrazit jeho prvního rámce.  
  
```  
BOOL Open(LPCTSTR lpszFileName);  
BOOL Open(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszFileName*  
 A `CString` objekt nebo ukazatel na řetězec zakončený hodnotou null, který obsahuje buď název souboru AVI nebo název AVI prostředku. Pokud tento parametr hodnotu NULL, systém zavře klip AVI, který byl dříve otevřen pro ovládací prvek animace, pokud existuje.  
  
 *nID*  
 Identifikátor URI AVI. Pokud tento parametr hodnotu NULL, systém zavře klip AVI, který byl dříve otevřen pro ovládací prvek animace, pokud existuje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak nula.  
  
### <a name="remarks"></a>Poznámky  
 AVI prostředků je načten z modulu, který vytvoří ovládací prvek animace.  
  
 `Open` nepodporuje zvuk klip AVI; můžete otevřít jenom tiché AVI klipy.  
  
 Pokud je ovládací prvek animace `ACS_AUTOPLAY` styl, ovládacího prvku animace automaticky začne přehrávat klip ihned po jeho otevření. Přehrajte klip na pozadí, zatímco vaše vlákno pokračuje v provádění bude pokračovat. Když se provádí klip přehrávání, se bude automaticky opakována.  
  
 Pokud je ovládací prvek animace `ACS_CENTER` styl, klip AVI bude zarovnaný na střed v ovládacím prvku a nedojde ke změně velikosti ovládacího prvku. Pokud ovládací prvek animace nemá `ACS_CENTER` styl, bude se velikost ovládacího prvku, když je klip AVI otevřen velikost bitové kopie, ve kterém se klip AVI. Pozice levého horního rohu ovládacího prvku se nezmění, velikost ovládacího prvku.  
  
 Pokud je ovládací prvek animace `ACS_TRANSPARENT` styl, první snímek bude vykreslen pomocí průhledné pozadí spíše než barva pozadí podle klip animace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="play"></a>  CAnimateCtrl::Play  
 Voláním této funkce přehrávání klip AVI v ovládacím prvku animace.  
  
```  
BOOL Play(
    UINT nFrom,  
    UINT nTo,  
    UINT nRep);
```  
  
### <a name="parameters"></a>Parametry  
 *Nze*  
 Index založený na nule rámce, ve kterém začne přehrávat. Hodnota musí být menší než 65536. Hodnota 0 znamená, že začínat prvního rámce, ve kterém se klip AVI.  
  
 *nChcete-li*  
 Index založený na nule rámce, ve kterém přehrávání skončí. Hodnota musí být menší než 65536. Hodnota - 1 znamená končit posledního rámce, ve kterém se klip AVI.  
  
 *nRep*  
 Počet pokusů přehrajte klip AVI. Hodnota - 1 znamená přehrání souboru po neomezenou dobu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak nula.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek animace bude přehrajte klip na pozadí, zatímco vaše vlákno pokračuje v provádění. Pokud je ovládací prvek animace `ACS_TRANSPARENT` styl, klip AVI bude možné přehrát, pomocí průhledné pozadí spíše než barva pozadí podle klip animace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="seek"></a>  CAnimateCtrl::Seek  
 Voláním této funkce pro staticky zobrazení jedním snímkem klip AVI.  
  
```  
BOOL Seek(UINT nTo);
```  
  
### <a name="parameters"></a>Parametry  
 *nChcete-li*  
 Rámeček pro zobrazení index založený na nule. Hodnota musí být menší než 65536. Hodnota 0 znamená, že zobrazení v klip AVI prvního rámce. Hodnota -1 znamená, že zobrazení v klip AVI posledního rámce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak nula.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je ovládací prvek animace `ACS_TRANSPARENT` styl, klip AVI bude vykreslen pomocí průhledné pozadí spíše než barva pozadí podle klip animace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="stop"></a>  CAnimateCtrl::Stop  
 Voláním této funkce zastavit přehrávání klip AVI ovládacího prvku animace.  
  
```  
BOOL Stop();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak nula.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](#create)   
 [ON_CONTROL](message-map-macros-mfc.md#on_control)

