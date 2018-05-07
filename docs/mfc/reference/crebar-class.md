---
title: CReBar – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94fc1e0ccad8980e0ed5a1cc0f8c0262502e1398
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="crebar-class"></a>CReBar – třída
Ovládací prvek panel, který poskytuje informace o stavu pro ovládací prvky matrice, rozložení a trvalost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CReBar : public CControlBar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CReBar::AddBar](#addbar)|Přidá pásmo matrice.|  
|[CReBar::Create](#create)|Vytvoří ovládacího prvku matrice a připojí jej k `CReBar` objektu.|  
|[CReBar::GetReBarCtrl](#getrebarctrl)|Umožňuje přímý přístup k podkladové běžného ovládacího prvku.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt matrice může obsahovat celou řadu podřízená okna, obvykle další ovládací prvky, včetně polí úpravy, panely nástrojů a seznamy. Objekt matrice můžete zobrazit jeho podřízené systému windows přes zadané rastrového obrázku. Aplikace můžete automaticky matrice změnit velikost nebo uživatele můžete ručně změnit velikost matrice kliknutím nebo přetažením jeho úchytu pruh.  
  
 ![Příklad RebarMenu](../../mfc/reference/media/vc4sc61.gif "vc4sc61")  
  
## <a name="rebar-control"></a>Matrice – ovládací prvek  
 Objekt matrice se chová podobně jako objekt panelu nástrojů. Matrice používá mechanismus kliknutím a přetažením ke změně velikosti jeho pásma. Ovládacím prvkem matrice může obsahovat jeden nebo více pruhy s každé pásmo s libovolnou kombinaci řádku úchytu, rastrový obrázek, text popisku a podřízeného okna. Pruhy však nemůže obsahovat více než jeden podřízeného okna.  
  
 **CReBar** používá [crebarctrl –](../../mfc/reference/crebarctrl-class.md) třída k zajištění jeho implementace. Přistupujete prostřednictvím ovládacího prvku matrice [GetReBarCtrl](#getrebarctrl) využívat možnosti přizpůsobení ovládacího prvku. Další informace o ovládacích prvcích matrice najdete v tématu `CReBarCtrl`. Další informace o používání ovládací prvky matrice najdete v tématu [crebarctrl pomocí –](../../mfc/using-crebarctrl.md).  
  
> [!CAUTION]
>  Matrice a objekty ovládacího prvku matrice nepodporují MFC ovládací prvek panelu ukotvení. Pokud **CRebar::EnableDocking** je volána, aplikace bude uplatnit.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccontrolbar –](../../mfc/reference/ccontrolbar-class.md)  
  
 `CReBar`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="addbar"></a>  CReBar::AddBar  
 Volání této funkce člena pro přidání do matrice pásmo.  
  
```  
BOOL AddBar(
    CWnd* pBar,  
    LPCTSTR pszText = NULL,  
    CBitmap* pbmp = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

 
BOOL AddBar(
    CWnd* pBar,  
    COLORREF clrFore,  
    COLORREF clrBack,  
    LPCTSTR pszText = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```  
  
### <a name="parameters"></a>Parametry  
 `pBar`  
 Ukazatel na `CWnd` objekt, který je podřízeného okna Vložit do matrice. Odkazovaný objekt musí mít **ws_child –**.  
  
 `lpszText`  
 Ukazatel na řetězec obsahující text, který se zobrazí na matrice. **NULL** ve výchozím nastavení. Text obsažené v `lpszText` není součástí podřízeného okna; se nachází na matrice sám sebe.  
  
 `pbmp`  
 Ukazatel na `CBitmap` objekt, který se má zobrazit na pozadí matrice. **NULL** ve výchozím nastavení.  
  
 `dwStyle`  
 A `DWORD` obsahující stylu použít matrice. Najdete v článku **fStyle** funkce Popis ve struktuře Win32 [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) úplný seznam stylů vzdálené správy.  
  
 *clrFore*  
 A **COLORREF** hodnotu, která představuje barvu popředí matrice.  
  
 *clrBack*  
 A **COLORREF** hodnotu, která představuje barvu pozadí matrice.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]  
  
##  <a name="create"></a>  CReBar::Create  
 Volání této funkce člen k vytvoření matrice.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Ukazatel `CWnd` objektu, jehož okno systému Windows je nadřazená stavový řádek. Za normálních okolností rámce okna.  
  
 `dwCtrlStyle`  
 Styl ovládacího prvku matrice. Ve výchozím nastavení **RBS_BANDBORDERS**, který zobrazí zúžit řádky k oddělení přiléhající pruhy v ovládacím prvku matrice. V tématu [– styly ovládacího prvku matrice](http://msdn.microsoft.com/library/windows/desktop/bb774377) ve Windows SDK pro seznam stylů.  
  
 `dwStyle`  
 Styly oken matrice.  
  
 `nID`  
 ID matrice podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CReBar::AddBar](#addbar).  
  
##  <a name="getrebarctrl"></a>  CReBar::GetReBarCtrl  
 Tato funkce člen umožňuje přímý přístup k podkladové běžného ovládacího prvku.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na [crebarctrl –](../../mfc/reference/crebarctrl-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen chcete využít výhod funkce Windows matrice běžné ovládacího prvku přizpůsobení vaší matrice. Při volání `GetReBarCtrl`, vrátí objekt a odkaz `CReBarCtrl` objekt, můžete použít buď sadu členské funkce.  
  
 Další informace o používání `CReBarCtrl` přizpůsobit vaší matrice, najdete v tématu [crebarctrl pomocí –](../../mfc/using-crebarctrl.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MFCIE](../../visual-cpp-samples.md)   
 [Ccontrolbar – třída](../../mfc/reference/ccontrolbar-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



