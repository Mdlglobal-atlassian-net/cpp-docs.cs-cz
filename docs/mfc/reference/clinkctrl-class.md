---
title: Clinkctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
dev_langs:
- C++
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f81b1e675f6b0c12330d84d17b2e6b1635503dfc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704935"
---
# <a name="clinkctrl-class"></a>Clinkctrl – třída
Poskytuje funkce pro Windows běžný ovládací prvek SysLink.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CLinkCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Vytvoří `CLinkCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CLinkCtrl::Create](#create)|Vytvoří ovládací prvek odkazu a připojí ho k `CLinkCtrl` objektu.|  
|[CLinkCtrl::CreateEx](#createex)|Vytvoří ovládací prvek odkazu s rozšířené styly a připojí ho k `CLinkCtrl` objektu.|  
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Načte ideální výšku ovládacího prvku odkaz.|  
|[CLinkCtrl::GetIdealSize](#getidealsize)|Vypočítá Upřednostňovaná výška text odkazu pro aktuální ovládací prvek odkazu, v závislosti na nastavená šířka odkazu.|  
|[CLinkCtrl::GetItem](#getitem)|Načte stav a atributy položky ovládacího prvku odkaz.|  
|[CLinkCtrl::GetItemID](#getitemid)|Načte Identifikátor položky ovládacího prvku odkaz.|  
|[CLinkCtrl::GetItemState](#getitemstate)|Načte stav položky ovládacího prvku odkaz.|  
|[CLinkCtrl::GetItemUrl](#getitemurl)|Načte adresu URL reprezentována položku ovládacího prvku odkaz.|  
|[CLinkCtrl::HitTest](#hittest)|Určuje, zda uživatel kliknul zadaném propojení.|  
|[CLinkCtrl::SetItem](#setitem)|Nastaví stav a atributy položky ovládacího prvku odkaz.|  
|[CLinkCtrl::SetItemID](#setitemid)|Nastaví ID položky ovládacího prvku odkaz.|  
|[CLinkCtrl::SetItemState](#setitemstate)|Nastaví stav položky ovládacího prvku odkaz.|  
|[CLinkCtrl::SetItemUrl](#setitemurl)|Nastaví adresu URL reprezentována položku ovládacího prvku odkaz.|  
  
## <a name="remarks"></a>Poznámky  
 "Propojení ovládacího prvku" poskytuje pohodlný způsob, jak vložit hypertextové odkazy v okně. Skutečný ovládací prvek je okno, které generuje text značkami a příslušné aplikace spustí, když uživatel klikne na odkaz vložený. Více odkazů jsou podporovány v rámci jednoho ovládacího prvku a je přístupný z nuly vycházející index.  
  
 Tento ovládací prvek (a tedy `CLinkCtrl` třídy) je dostupná jenom pro programy spuštěné pod Windows XP nebo novější.  
  
 Další informace najdete v tématu [ovládací prvek SysLink](/windows/desktop/Controls/syslink-overview) v sadě Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CLinkCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="clinkctrl"></a>  CLinkCtrl::CLinkCtrl  
 Vytvoří `CLinkCtrl` objektu.  
  
```  
CLinkCtrl();
```  
  
##  <a name="create"></a>  CLinkCtrl::Create  
 Vytvoří ovládací prvek odkazu a připojí ho k `CLinkCtrl` objektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,   
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);

 
virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLinkMarkup*  
 Ukazatel na řetězec ukončit nulou, který obsahuje označené text k zobrazení. Další informace najdete v části "Značek a odkaz přístup" v tématu [prvky SysLink přehled](/windows/desktop/Controls/syslink-overview).  
  
 *dwStyle*  
 Určuje styl ovládacího prvku odkaz. Použijte libovolnou kombinaci – styly ovládacího prvku. V tématu [– styly běžných ovládacích prvků](/windows/desktop/Controls/common-control-styles) v `Windows SDK` Další informace.  
  
 *Rect*  
 Určuje velikost a umístění ovládacího prvku odkaz. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](../../mfc/reference/rect-structure1.md) struktury.  
  
 *pParentWnd*  
 Určuje nadřazené okno ovládacího prvku odkaz. Nesmí být NULL.  
  
 *nID*  
 Určuje ID ovládacího prvku odkaz.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě, že inicializace byla úspěšná. v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CLinkCtrl` objektu ve dvou krocích. Nejprve volat konstruktor a následně zavolat `Create`, což vytvoří ovládací prvek odkazu a připojí ho k `CLinkCtrl` objektu. Pokud chcete použít rozšířené windows styly ovládacího prvku, zavolejte [CLinkCtrl::CreateEx](#createex) místo `Create`.  
  
 Tedy o druhou podobu `Create` metoda je zastaralá. Použít první formulář, který určuje, *lpszLinkMarkup* parametru.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje dvě proměnné pojmenované `m_Link1` a `m_Link2`, které se používají pro přístup k dvou ovládacích prvků propojení.  
  
 [!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří jeden ovládací prvek odkazu na základě umístění jiného ovládacího prvku odkaz. Zavaděč prostředků vytvoří první ovládací prvek odkazu při spuštění aplikace. Když vaše aplikace přejde do metody OnInitDialog, můžete vytvořit druhý ovládací prvek odkazu relativní k pozici první ovládací prvek odkazu. Potom změňte velikost druhý ovládací prvek link přizpůsobit text, který se zobrazí.  
  
 [!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CLinkCtrl::CreateEx  
 Vytvoří ovládací prvek odkazu s rozšířené styly a připojí ho k `CLinkCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,   
    DWORD dwExStyle,  
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);

 
virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLinkMarkup*  
 Ukazatel na řetězec ukončit nulou, který obsahuje označené text k zobrazení. Další informace najdete v části "Značek a odkaz přístup" v tématu [prvky SysLink přehled](/windows/desktop/Controls/syslink-overview).  
  
 *dwExStyle*  
 Určuje rozšířený styl ovládacího prvku odkaz. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) v sadě Windows SDK.  
  
 *dwStyle*  
 Určuje styl ovládacího prvku odkaz. Použijte libovolnou kombinaci – styly ovládacího prvku. Další informace najdete v tématu [– styly běžných ovládacích prvků](/windows/desktop/Controls/common-control-styles) v sadě Windows SDK.  
  
 *Rect*  
 Určuje velikost a umístění ovládacího prvku odkaz. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](../../mfc/reference/rect-structure1.md) struktury.  
  
 *pParentWnd*  
 Určuje nadřazené okno ovládacího prvku odkaz. Nesmí být NULL.  
  
 *nID*  
 Určuje ID ovládacího prvku odkaz.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě, že inicializace byla úspěšná. v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířený styl konstanty Windows.  
  
 Tedy o druhou podobu `CreateEx` metoda je zastaralá. Použít první formulář, který určuje, *lpszLinkMarkup* parametru.  
  
##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight  
 Načte ideální výšku ovládacího prvku odkaz.  
  
```  
int GetIdealHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ideální výška ovládacího prvku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [LM_GETIDEALHEIGHT](/windows/desktop/Controls/lm-getidealheight), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize  
 Vypočítá Upřednostňovaná výška text odkazu pro aktuální ovládací prvek odkazu, v závislosti na nastavená šířka odkazu.  
  
```  
int GetIdealSize(
    int cxMaxWidth,   
    SIZE* pSize) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*cxMaxWidth*|[in] Maximální šířka propojení v pixelech.|  
|[out] \* *pSize*|Ukazatel Windows [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury. Po návratu tato metoda *cy* člena `SIZE` struktura obsahuje text výška ideální odkaz pro šířku textu odkazu, která je zadána *cxMaxWidth*. *Cx* členu struktury obsahuje šířku text odkazu, který je skutečně potřeba.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Upřednostňovaná výška textu odkazu, v pixelech. Vrácená hodnota je stejná jako hodnota *cy* člena `SIZE` struktury.  
  
### <a name="remarks"></a>Poznámky  
 Příklad `GetIdealSize` metodou, podívejte se na příklad v [CLinkCtrl::Create](#create).  
  
 Tato metoda odesílá [LM_GETIDEALSIZE](/windows/desktop/Controls/lm-getidealsize) zprávu, která je popsána v sadě Windows SDK.  
  
##  <a name="getitem"></a>  CLinkCtrl::GetItem  
 Načte stav a atributy položky ovládacího prvku odkaz.  
  
```  
BOOL GetItem(PLITEM pItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pItem*  
 Ukazatel [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) struktura přijímat informace o položce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getitemid"></a>  CLinkCtrl::GetItemID  
 Načte Identifikátor položky ovládacího prvku odkaz.  
  
```  
BOOL GetItemID(
    int iLink,  
    CString& strID) const;  
  
BOOL GetItemID(
    int iLink,  
    LPWSTR szID,  
    UINT cchID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *společnosti iLink*  
 Index položky ovládacího prvku odkaz.  
  
 *hodnoty %{strid/*  
 A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje ID zadané položky.  
  
 *szID*  
 Řetězec zakončený hodnotou null obsahující ID zadané položky.  
  
 *cchID*  
 Velikost ve znacích *szID* vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
> [!NOTE]
>  Tato funkce také vrátí hodnotu FALSE, pokud vyrovnávací paměť o *szID nebo hodnoty %{strid/* je menší než MAX_LINKID_TEXT.  
  
### <a name="remarks"></a>Poznámky  
 Načte Identifikátor položky ovládacího prvku odkaz. Další informace najdete v tématu zpráva Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem) v sadě Windows SDK.  
  
##  <a name="getitemstate"></a>  CLinkCtrl::GetItemState  
 Načte stav položky ovládacího prvku odkaz.  
  
```  
BOOL GetItemState(
    int iLink,  
    UINT* pnState,  
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *společnosti iLink*  
 Index položky ovládacího prvku odkaz.  
  
 *pnState*  
 Hodnota zadaného stavu položky.  
  
 *stateMask*  
 Kombinace příznaků popisující, které stav položky zobrazíte. Seznam hodnot, viz popis `state` člen [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) struktury. Povolené položky jsou stejné jako ty v povolené `state`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Načte hodnotu zadaného stavu položky položky ovládacího prvku odkaz. Další informace najdete v tématu zpráva Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem) v sadě Windows SDK.  
  
##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl  
 Načte adresu URL reprezentována položku ovládacího prvku odkaz.  
  
```  
BOOL GetItemUrl(
    int iLink,  
    CString& strUrl) const;  
  
BOOL GetItemUrl(
    int iLink,  
    LPWSTR szUrl,  
    UINT cchUrl) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *společnosti iLink*  
 Index položky ovládacího prvku odkaz.  
  
 *%{strurl/*  
 A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje adresu URL reprezentována určenou položku  
  
 *szUrl*  
 Řetězec zakončený hodnotou null obsahující adresu URL reprezentována určenou položku  
  
 *cchUrl*  
 Velikost ve znacích *szURL* vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
> [!NOTE]
>  Tato funkce také vrátí hodnotu FALSE, pokud vyrovnávací paměť o *szUrl nebo %{strurl/* je menší než MAX_LINKID_TEXT.  
  
### <a name="remarks"></a>Poznámky  
 Načte adresu URL reprezentována zadaný odkaz položku ovládacího prvku. Další informace najdete v tématu zpráva Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem) v sadě Windows SDK.  
  
##  <a name="hittest"></a>  CLinkCtrl::HitTest  
 Určuje, pokud uživatel klikl na zadaném propojení.  
  
```  
BOOL HitTest(PLHITTESTINFO phti) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *phti*  
 Ukazatel `LHITTESTINFO` struktura obsahující informace o propojení uživatel klikl na.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [LM_HITTEST](/windows/desktop/Controls/lm-hittest), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setitem"></a>  CLinkCtrl::SetItem  
 Nastaví stav a atributy položky ovládacího prvku odkaz.  
  
```  
BOOL SetItem(PLITEM pItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pItem*  
 Ukazatel [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) struktura obsahující informace o nastavení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setitemid"></a>  CLinkCtrl::SetItemID  
 Načte Identifikátor položky ovládacího prvku odkaz.  
  
```  
BOOL SetItemID(
    int iLink,  
    LPCWSTR szID);
```  
  
### <a name="parameters"></a>Parametry  
 *společnosti iLink*  
 Index položky ovládacího prvku odkaz.  
  
 *szID*  
 Řetězec zakončený hodnotou null obsahující ID zadané položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví ID položky ovládacího prvku odkaz. Další informace najdete v tématu zpráva Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem) v sadě Windows SDK.  
  
##  <a name="setitemstate"></a>  CLinkCtrl::SetItemState  
 Načte stav položky ovládacího prvku odkaz.  
  
```  
BOOL SetItemState(
    int iLink,  
    UINT state,  
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```  
  
### <a name="parameters"></a>Parametry  
 *společnosti iLink*  
 Index položky ovládacího prvku odkaz.  
  
 *pnState*  
 Hodnota položky zadaného stavu nastavena.  
  
 *stateMask*  
 Kombinace příznaků popisující stav položky nastavena. Seznam hodnot, viz popis `state` člen [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) struktury. Povolené položky jsou stejné jako ty v povolené `state`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví hodnotu zadaného stavu položky položky ovládacího prvku odkaz. Další informace najdete v tématu zpráva Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem) v sadě Windows SDK.  
  
##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl  
 Nastaví adresu URL reprezentována položku ovládacího prvku odkaz.  
  
```  
BOOL SetItemUrl(
    int iLink,  
    LPCWSTR szUrl);
```  
  
### <a name="parameters"></a>Parametry  
 *společnosti iLink*  
 Index položky ovládacího prvku odkaz.  
  
 *szUrl*  
 Řetězec zakončený hodnotou null obsahující adresu URL reprezentována určenou položku  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví adresu URL reprezentována zadaný odkaz položku ovládacího prvku. Další informace najdete v tématu zpráva Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CWnd – třída](../../mfc/reference/cwnd-class.md)
