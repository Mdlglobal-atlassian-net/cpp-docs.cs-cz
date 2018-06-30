---
title: Třída CSplitButton | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
dev_langs:
- C++
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fbced65aa76206d040ff1c13267fe9b7d3c69eca
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122784"
---
# <a name="csplitbutton-class"></a>CSplitButton – třída
`CSplitButton` Třída reprezentuje ovládací prvek tlačítko rozdělení. Ovládací prvek tlačítko rozdělení provede výchozí chování, když uživatel klikne na hlavní část tlačítko a zobrazí rozevírací nabídky, když uživatel klikne na šipku rozevíracího seznamu tlačítka.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSplitButton : public CButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSplitButton::CSplitButton](#csplitbutton)|Vytvoří `CSplitButton` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSplitButton::Create](#create)|Vytvoří ovládací prvek tlačítko rozdělení se zadanou styly a připojí k aktuální `CSplitButton` objektu.|  
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Nastaví rozevírací nabídce, která se zobrazí, když uživatel klikne na šipku rozevíracího seznamu aktuální ovládacího prvku tlačítko rozdělení.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSplitButton::OnDropDown](#ondropdown)|Zpracovává BCN_DROPDOWN oznámení, že systém pošle, když uživatel klikne na šipku rozevíracího seznamu aktuální ovládacího prvku tlačítko rozdělení.|  
  
## <a name="remarks"></a>Poznámky  
 `CSplitButton` Je třída odvozená z [CButton](../../mfc/reference/cbutton-class.md) třídy. Ovládací prvek tlačítko rozdělení je tlačítko, jehož styl je BS_SPLITBUTTON. Když uživatel klikne na šipku rozevíracího seznamu zobrazuje vlastní nabídku. Další informace najdete v tématu styly BS_SPLITBUTTON a BS_DEFSPLITBUTTON v [styly tlačítek](http://msdn.microsoft.com/library/windows/desktop/bb775951).  
  
 Následující obrázek znázorňuje dialogu, který obsahuje ovládacího prvku pager a ovládací prvek tlačítko rozdělení (1). Již bylo kliknuto na šipku rozevíracího seznamu (2) a (3) podnabídky se zobrazí.  
  
 ![Dialogové okno s ovládacím prvkem a stránkovacím. ] (../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CSplitButton`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
 Tato třída je podporována v [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] a novější.  
  
 Další požadavky pro tuto třídu, jsou popsané v [sestavení požadavky pro Windows Vista běžné ovládací prvky](../../mfc/build-requirements-for-windows-vista-common-controls.md).  
  
##  <a name="create"></a>  CSplitButton::Create  
 Vytvoří ovládací prvek tlačítko rozdělení se zadanou styly a připojí k aktuální `CSplitButton` objektu.  
  
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
|[v] *dwStyle*|Bitová kombinace (nebo) stylů má být použita pro ovládací prvek. Další informace najdete v tématu [styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).|  
|[v] *Rect –*|Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která obsahuje umístění a velikost ovládacího prvku.|  
|[v] *pParentWnd*|Ukazatel na jinou hodnotu než null [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku.|  
|[v] *nID*|ID ovládacího prvku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tato metoda je úspěšná. jinak hodnota FALSE.  
  
##  <a name="csplitbutton"></a>  CSplitButton::CSplitButton  
 Vytvoří `CSplitButton` objektu. V konstruktoru parametry zadejte podnabídky, které se zobrazí, když uživatel klikne na šipku rozevíracího seznamu ovládacího prvku tlačítko rozdělení.  
  
```  
CSplitButton();

 
CSplitButton(
    UINT nMenuId,   
    UINT nSubMenuId)  
CSplitButton(CMenu* pMenu)  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] *nMenuId*|ID prostředku řádku nabídek.|  
|[v] *nSubMenuId*|ID prostředku podnabídky.|  
|[v] *pMenu*|Ukazatel [cmenu –](../../mfc/reference/cmenu-class.md) objekt, který určuje podnabídky. `CSplitButton` Objektu odstranění `CMenu` objekt a jeho přidružené HMENU při `CSplitButton` opuštění rozsahu.|  
  
### <a name="remarks"></a>Poznámky  
 Použití [CSplitButton::Create](#create) metodu pro vytvoření ovládacího prvku tlačítko rozdělení a připojte ji k `CSplitButton` objektu.  
  
##  <a name="ondropdown"></a>  CSplitButton::OnDropDown  
 Zpracovává BCN_DROPDOWN oznámení, že systém pošle, když uživatel klikne na šipku rozevíracího seznamu aktuální ovládacího prvku tlačítko rozdělení.  
  
```  
afx_msg void OnDropDown(
    NMHDR* pNMHDR,   
    LRESULT* pResult);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] *pNMHDR*|Ukazatel na [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) struktura, která obsahuje informace o [BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983) oznámení.|  
|[out] *pResult*|(Nepoužívá, je vrácena žádná hodnota.) Návratová hodnota [BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983) oznámení.|  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel klikne na šipku rozevíracího seznamu v ovládacím prvku tlačítko rozdělení, systém odešle oznámení BCN_DROPDOWN zprávy, které `OnDropDown` metoda zpracovává. Ale `CSplitButton` objekt nepředává BCN_DROPDOWN oznámení pro ovládací prvek, který obsahuje ovládací prvek tlačítko rozdělení. Nadřazeného ovládacího prvku v důsledku toho nemůže podporovat vlastní akce v reakci na oznámení.  
  
 Chcete-li implementovat vlastní akci, která podporuje nadřazeného ovládacího prvku, použijte [CButton](../../mfc/reference/cbutton-class.md) objekt s styl BS_SPLITBUTTON místo `CSplitButton` objektu. Potom implementovat obslužnou rutinu pro oznámení BCN_DROPDOWN v `CButton` objektu. Další informace najdete v tématu [styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
 Chcete-li implementovat vlastní akce, aby tlačítko rozdělení podporuje ovládací prvek sám sebe, použijte [zprávy reflexe](../../mfc/tn062-message-reflection-for-windows-controls.md). Odvodit vlastní třídu z `CSplitButton` třídy a pojmenujte ji třeba CMySplitButton. Pak přidejte následující mapa zpráv do vaší aplikace pro zpracování BCN_DROPDOWN oznámení:  
  
```  
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)  
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)  
END_MESSAGE_MAP()  
```  
  
##  <a name="setdropdownmenu"></a>  CSplitButton::SetDropDownMenu  
 Nastaví rozevírací nabídce, která se zobrazí, když uživatel klikne na šipku rozevíracího seznamu aktuální ovládacího prvku tlačítko rozdělení.  
  
```  
void SetDropDownMenu(
    UINT nMenuId,   
    UINT nSubMenuId);  
  
void SetDropDownMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] *nMenuId*|ID prostředku řádku nabídek.|  
|[v] *nSubMenuId*|ID prostředku podnabídky.|  
|[v] *pMenu*|Ukazatel na [cmenu –](../../mfc/reference/cmenu-class.md) objekt, který určuje podnabídky. `CSplitButton` Objektu odstranění `CMenu` objekt a jeho přidružené HMENU při `CSplitButton` opuštění rozsahu.|  
  
### <a name="remarks"></a>Poznámky  
 *NMenuId* parametr identifikuje řádku nabídek, což je vodorovné seznam položek nabídky panelu. *NSubMenuId* parametr je počítaný od nuly číslo indexu, který identifikuje podnabídky, což je rozevírací seznam položky nabídky, které jsou spojené s každou položku nabídky panelu. Typická aplikace má například nabídky, která obsahuje položky nabídky panelu, "Soubor" "Upravit" a "Nápověda". Položka nabídky panelu "Soubor" má dílčí, který obsahuje položky nabídky "Otevřít," "Zavřete" a "Ukončit." Při kliknutí na šipku rozevíracího seznamu ovládacího prvku tlačítko rozdělení ovládací prvek zobrazí zadané dílčí není panelu nabídek.  
  
 Následující obrázek znázorňuje dialogu, který obsahuje ovládacího prvku pager a ovládací prvek tlačítko rozdělení (1). Již bylo kliknuto na šipku rozevíracího seznamu (2) a (3) podnabídky se zobrazí.  
  
 ![Dialogové okno s ovládacím prvkem a stránkovacím. ] (../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
### <a name="example"></a>Příklad  
 První příkaz v následujícím příkladu kódu ukazuje [CSplitButton::SetDropDownMenu](#setdropdownmenu) metoda. Jsme vytvořili v nabídce sady Visual Studio prostředek editor, který automaticky s názvem IDR_MENU1 Identifikátor řádku nabídky. *NSubMenuId* parametr, který je nulová, odkazuje na podnabídky pouze v řádku nabídek.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CSplitButton – třída](../../mfc/reference/csplitbutton-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CButton – třída](../../mfc/reference/cbutton-class.md)
