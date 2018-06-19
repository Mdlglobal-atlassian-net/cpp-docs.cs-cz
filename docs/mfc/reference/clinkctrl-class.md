---
title: Třída CLinkCtrl | Microsoft Docs
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
ms.openlocfilehash: a2312861a1b13ecb432c7893a27d72c61ecd78ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371696"
---
# <a name="clinkctrl-class"></a>CLinkCtrl – třída
Poskytuje funkci běžné SysLink ovládacího prvku Windows.  
  
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
|[CLinkCtrl::Create](#create)|Ovládací prvek odkazu vytvoří a připojí jej k `CLinkCtrl` objektu.|  
|[CLinkCtrl::CreateEx](#createex)|Vytvoří řízení propojení s rozšířené styly a připojí jej k `CLinkCtrl` objektu.|  
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Načte ideální výšku ovládací prvek odkazu.|  
|[CLinkCtrl::GetIdealSize](#getidealsize)|Vypočítá upřednostňované výšku text odkazu pro aktuální řízení propojení, v závislosti na nastavená šířka propojení.|  
|[CLinkCtrl::GetItem](#getitem)|Načte stavy a atributy ovládacího prvku položky odkaz.|  
|[CLinkCtrl::GetItemID](#getitemid)|Načte Identifikátor položky ovládacího prvku odkazu.|  
|[CLinkCtrl::GetItemState](#getitemstate)|Načte stav položky ovládacího prvku odkazu.|  
|[CLinkCtrl::GetItemUrl](#getitemurl)|Načte adresu URL reprezentována položky ovládacího prvku odkazu.|  
|[CLinkCtrl::HitTest](#hittest)|Určuje, zda uživatel klikli na zadaný odkaz.|  
|[CLinkCtrl::SetItem](#setitem)|Nastaví stavy a atributy ovládacího prvku položky odkaz.|  
|[CLinkCtrl::SetItemID](#setitemid)|Nastaví ID položky ovládacího prvku odkazu.|  
|[CLinkCtrl::SetItemState](#setitemstate)|Nastaví stav položky ovládacího prvku odkazu.|  
|[CLinkCtrl::SetItemUrl](#setitemurl)|Nastaví adresu URL reprezentována položky ovládacího prvku odkazu.|  
  
## <a name="remarks"></a>Poznámky  
 "Link řízení" představuje pohodlný způsob pro vložení hypertextové odkazy v okně. Skutečné řízení je okno, které vykreslí text značkami a spouští příslušné aplikace, když uživatel klikne odkaz embedded. Více odkazy jsou podporovány v rámci jeden ovládací prvek a je přístupný pomocí index počítaný od nuly.  
  
 Tento ovládací prvek (a proto `CLinkCtrl` třída) je k dispozici pouze pro aplikace spuštěné v systému Windows XP nebo novější.  
  
 Další informace najdete v tématu [SysLink řízení](http://msdn.microsoft.com/library/windows/desktop/bb760706) ve Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
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
 Ovládací prvek odkazu vytvoří a připojí jej k `CLinkCtrl` objektu.  
  
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
 `lpszLinkMarkup`  
 Ukazatel na nule ukončena řetězec, který označen jako obsahuje zobrazený text. Další informace najdete v části "Značek a odkaz Access" v tématu [prvky SysLink přehled](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 `dwStyle`  
 Určuje styl řízení propojení. Použijte libovolnou kombinaci styly ovládacího prvku. V tématu [běžné styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775498) v `Windows SDK` Další informace.  
  
 `rect`  
 Určuje velikost a umístění řízení propojení. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](../../mfc/reference/rect-structure1.md) struktura.  
  
 `pParentWnd`  
 Určuje řízení propojení nadřazeného okna. Nesmí být `NULL`.  
  
 `nID`  
 Určuje ID ovládacího prvku odkazu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se inicializace byla úspěšná. v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CLinkCtrl` objektu ve dvou krocích. Nejprve volat konstruktor a pak zavolají `Create`, který vytvoří řízení propojení a připojí jej k `CLinkCtrl` objektu. Pokud chcete použít rozšířené windows styly s ovládacím prvkem, zavolejte [CLinkCtrl::CreateEx](#createex) místo `Create`.  
  
 O druhou podobu `Create` metoda je zastaralá. První formulář, který určuje použijte `lpszLinkMarkup` parametr.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje dvě proměnné, s názvem `m_Link1` a `m_Link2`, které se používají pro přístup k dvou ovládacích prvků propojení.  
  
 [!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří jeden ovládací prvek odkazu na základě umístění ovládací prvek odkazu na jiný. Zavaděč prostředku vytvoří první řízení propojení při spuštění aplikace. Když aplikace zadá OnInitDialog – metoda, můžete vytvořit druhý řízení propojení vzhledem ke pozici prvního ovládacího prvku odkazu. Potom můžete velikost druhý odkaz ovládacího prvku podle text, který se zobrazí.  
  
 [!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CLinkCtrl::CreateEx  
 Vytvoří řízení propojení s rozšířené styly a připojí jej k `CLinkCtrl` objektu.  
  
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
 `lpszLinkMarkup`  
 Ukazatel na nule ukončena řetězec, který označen jako obsahuje zobrazený text. Další informace najdete v části "Značek a odkaz Access" v tématu [prvky SysLink přehled](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 `dwExStyle`  
 Určuje styl rozšířené ovládací prvek odkazu. Seznam rozšířené styly Windows najdete v tématu `dwExStyle` parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 `dwStyle`  
 Určuje styl řízení propojení. Použijte libovolnou kombinaci styly ovládacího prvku. Další informace najdete v tématu [běžné styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775498) ve Windows SDK.  
  
 `rect`  
 Určuje velikost a umístění řízení propojení. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](../../mfc/reference/rect-structure1.md) struktura.  
  
 `pParentWnd`  
 Určuje řízení propojení nadřazeného okna. Nesmí být `NULL`.  
  
 `nID`  
 Určuje ID ovládacího prvku odkazu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se inicializace byla úspěšná. v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířené konstanty styl systému Windows.  
  
 O druhou podobu `CreateEx` metoda je zastaralá. První formulář, který určuje použijte `lpszLinkMarkup` parametr.  
  
##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight  
 Načte ideální výšku ovládací prvek odkazu.  
  
```  
int GetIdealHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ideální výška ovládacího prvku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [LM_GETIDEALHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb760716), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize  
 Vypočítá upřednostňované výšku text odkazu pro aktuální řízení propojení, v závislosti na nastavená šířka propojení.  
  
```  
int GetIdealSize(
    int cxMaxWidth,   
    SIZE* pSize) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `cxMaxWidth`|Maximální šířka odkazu, který je v pixelech.|  
|[out] * `pSize`|Ukazatel na Windows [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura. Po návratu tato metoda `cy` členem `SIZE` struktura obsahuje výšku textu ideální odkaz k šířce text odkazu, která je zadána `cxMaxWidth`. `cx` Členů struktury obsahuje šířku text odkazu, která je skutečně potřeba.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Upřednostňované výška text odkazu, v pixelech. Vrácená hodnota je stejná jako hodnota `cy` členem `SIZE` struktura.  
  
### <a name="remarks"></a>Poznámky  
 Příklad `GetIdealSize` metodu, najdete v příkladu v [CLinkCtrl::Create](#create).  
  
 Tato metoda odesílá [LM_GETIDEALSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760718) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getitem"></a>  CLinkCtrl::GetItem  
 Načte stavy a atributy ovládacího prvku položky odkaz.  
  
```  
BOOL GetItem(PLITEM pItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Ukazatel [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) struktura přijímat informace o položce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getitemid"></a>  CLinkCtrl::GetItemID  
 Načte Identifikátor položky ovládacího prvku odkazu.  
  
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
 `iLink`  
 Index položky ovládacího prvku odkazu.  
  
 *hodnoty %{strid/*  
 A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující Identifikátor zadané položky.  
  
 *szID*  
 Ukončené hodnotou null řetězec obsahující ID zadané položky.  
  
 *cchID*  
 Velikost v znaků *szID* vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
> [!NOTE]
>  Tato funkce také vrátí hodnotu **FALSE** Pokud vyrovnávací paměti s *szID nebo hodnoty %{strid/* je menší než **MAX_LINKID_TEXT**.  
  
### <a name="remarks"></a>Poznámky  
 Načte Identifikátor položky ovládacího prvku konkrétním propojení. Další informace najdete v tématu zpráva Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720) ve Windows SDK.  
  
##  <a name="getitemstate"></a>  CLinkCtrl::GetItemState  
 Načte stav položky ovládacího prvku odkazu.  
  
```  
BOOL GetItemState(
    int iLink,  
    UINT* pnState,  
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `iLink`  
 Index položky ovládacího prvku odkazu.  
  
 `pnState`  
 Hodnota položky zadaného stavu.  
  
 `stateMask`  
 Kombinace příznaků popisující, které položky stavu se získat. Seznam hodnot, najdete v části Popis **stavu** člena v [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) struktury. Povolené položky jsou stejné jako, které jsou povoleny v **stavu**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Načte hodnotu zadaného stavu položky položky ovládacího prvku konkrétním propojení. Další informace najdete v tématu zpráva Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720) ve Windows SDK.  
  
##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl  
 Načte adresu URL reprezentována položky ovládacího prvku odkazu.  
  
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
 `iLink`  
 Index položky ovládacího prvku odkazu.  
  
 `strUrl`  
 A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje adresu URL reprezentována zadanou položku  
  
 `szUrl`  
 Obsahující adresu URL zadanou položku reprezentována řetězce ukončené hodnotou null  
  
 *cchUrl*  
 Velikost v znaků *szURL* vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
> [!NOTE]
>  Tato funkce také vrátí hodnotu **FALSE** Pokud vyrovnávací paměti s *szUrl nebo strUrl* je menší než **MAX_LINKID_TEXT**.  
  
### <a name="remarks"></a>Poznámky  
 Načte adresu URL reprezentována položky ovládacího prvku zadaný odkaz. Další informace najdete v tématu zpráva Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720) ve Windows SDK.  
  
##  <a name="hittest"></a>  CLinkCtrl::HitTest  
 Určuje, pokud by uživatel klepl na zadaném propojení.  
  
```  
BOOL HitTest(PLHITTESTINFO phti) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *phti*  
 Ukazatel na **LHITTESTINFO** struktura obsahující žádné informace o propojení, kliknutí na uživatele.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [LM_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb760722), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setitem"></a>  CLinkCtrl::SetItem  
 Nastaví stavy a atributy ovládacího prvku položky odkaz.  
  
```  
BOOL SetItem(PLITEM pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Ukazatel [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) struktura obsahující informace o nastavení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setitemid"></a>  CLinkCtrl::SetItemID  
 Načte Identifikátor položky ovládacího prvku odkazu.  
  
```  
BOOL SetItemID(
    int iLink,  
    LPCWSTR szID);
```  
  
### <a name="parameters"></a>Parametry  
 `iLink`  
 Index položky ovládacího prvku odkazu.  
  
 *szID*  
 Ukončené hodnotou null řetězec obsahující ID zadané položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví ID položky ovládacího prvku konkrétním propojení. Další informace najdete v tématu zpráva Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724) ve Windows SDK.  
  
##  <a name="setitemstate"></a>  CLinkCtrl::SetItemState  
 Načte stav položky ovládacího prvku odkazu.  
  
```  
BOOL SetItemState(
    int iLink,  
    UINT state,  
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```  
  
### <a name="parameters"></a>Parametry  
 `iLink`  
 Index položky ovládacího prvku odkazu.  
  
 `pnState`  
 Hodnota položky zadaného stavu Probíhá nastavení.  
  
 `stateMask`  
 Kombinace příznaků popisující položku stavu Probíhá nastavení. Seznam hodnot, najdete v části Popis **stavu** člena v [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) struktury. Povolené položky jsou stejné jako, které jsou povoleny v **stavu**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví hodnotu zadaného stavu položky položky ovládacího prvku konkrétním propojení. Další informace najdete v tématu zpráva Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724) ve Windows SDK.  
  
##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl  
 Nastaví adresu URL reprezentována položky ovládacího prvku odkazu.  
  
```  
BOOL SetItemUrl(
    int iLink,  
    LPCWSTR szUrl);
```  
  
### <a name="parameters"></a>Parametry  
 `iLink`  
 Index položky ovládacího prvku odkazu.  
  
 `szUrl`  
 Obsahující adresu URL zadanou položku reprezentována řetězce ukončené hodnotou null  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví adresu URL reprezentována položky ovládacího prvku zadaný odkaz. Další informace najdete v tématu zpráva Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CWnd – třída](../../mfc/reference/cwnd-class.md)
