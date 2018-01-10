---
title: "Třída CMFCEditBrowseCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
dev_langs: C++
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de1e30e6ca9f404199c6db43837f35d612a02b69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl – třída
`CMFCEditBrowseCtrl` Třída podporuje řízení procházet úpravy, které je upravitelné textové pole, které volitelně obsahuje tlačítko Procházet. Když uživatel klikne na tlačítko Procházet, ovládacího prvku provede vlastní akci nebo zobrazí standardní dialogové okno, které obsahuje prohlížeče souboru nebo složky prohlížeče.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Výchozí konstruktor.|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Povolí nebo zakáže (skryje) na tlačítko Procházet.|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Umožňuje na tlačítko Procházet a vloží ovládací prvek upravit Procházet *procházení souborů* režimu.|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Umožňuje na tlačítko Procházet a vloží ovládací prvek upravit Procházet *procházet složky* režimu.|  
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Vrátí aktuální procházecí režim.|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Voláno rámcem po aktualizaci prvku procházet upravit s výsledkem procházet akce.|  
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Voláno rámcem po kliknutí na tlačítko Procházet.|  
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Překreslí aktuální procházet ovládací prvek upravit.|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Voláno rámcem kreslení na tlačítko Procházet.|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Voláno rámcem při zadávání názvu objektu neplatný soubor v textovém poli.|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Přeloží zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. Syntaxe a další informace najdete v tématu [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Nastaví vlastní obrázek pro tlačítko procházení.|  
  
## <a name="remarks"></a>Poznámky  
 Použití ovládacího prvku úprav Procházet a vyberte název souboru nebo složky. Volitelně můžete pomocí ovládacího prvku provést vlastní akci, jako a zobrazit dialogové okno. Můžete zobrazit nebo nejsou zobrazeny na tlačítko Procházet a na tlačítko můžete použít vlastní popisek nebo bitové kopie.  
  
 *Režimu procházení* z procházet upravit řízení Určuje, zda se zobrazí tlačítko Procházet a jaké akci dojde po kliknutí na tlačítko. Další informace najdete v tématu [GetMode](#getmode) metoda.  
  
 `CMFCEditBrowseCtrl` Třída podporuje následující režimy.  
  
 `custom mode`  
 Vlastní akce se provádí, když uživatel klikne na tlačítko Procházet. Můžete například zobrazit dialogové okno s konkrétní aplikace.  
  
 `file mode`  
 Dialogové okno Výběr standardní souboru se zobrazí, když uživatel klikne na tlačítko Procházet.  
  
 `folder mode`  
 Dialogové okno Výběr standardní složku se zobrazí, když uživatel klikne na tlačítko Procházet.  
  
## <a name="how-to-specify-an-edit-browse-control"></a>Postupy: Zadejte procházet ovládacího prvku úprav  
 Proveďte následující kroky umožňují začlenění ovládací prvek upravit procházet ve vaší aplikaci:  
  
1.  Pokud chcete implementovat vlastní procházecí režim, odvodit vlastní třídu z `CMFCEditBrowseCtrl` třídy a pak přepsat [CMFCEditBrowseCtrl::OnBrowse](#onbrowse) metoda. V metodě přepsaného provést akci vlastní Procházet a aktualizujte ovládacího prvku úprav procházet pomocí výsledek.  
  
2.  Vložení buď `CMFCEditBrowseCtrl` objekt nebo objekt odvozené upravit procházet ovládacího prvku do nadřazeného okna objektu.  
  
3.  Pokud použijete **Průvodce třídou** vytvořit dialogové okno, přidejte ovládací prvek úprav ( `CEdit`) dialogové okno pole formuláře. Také přidáte proměnnou pro přístup k prvku v záhlaví souboru. V záhlaví souboru změnit typ proměnné z `CEdit` k `CMFCEditBrowseCtrl`. Ovládací prvek upravit procházet vytvoří automaticky. Pokud použijete **Průvodce třídou**, přidat `CMFCEditBrowseCtrl` proměnnou hlavičkový soubor a pak volání jeho `Create` metoda.  
  
4.  Pokud přidáte do dialogového okna procházení ovládací prvek upravit, použijte **ClassWizard** nástroj nastavit dat systému exchange.  
  
5.  Volání [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton), nebo [enablebrowsebutton –](#enablebrowsebutton) metoda k nastavení režimu procházení a zobrazení na tlačítko Procházet. Volání [GetMode](#getmode) metoda získat aktuální procházecí režim.  
  
6.  Zajistit vlastní obrázek pro tlačítko procházení volání [SetBrowseButtonImage](#setbrowsebuttonimage) metoda nebo přepsání [OnDrawBrowseButton](#ondrawbrowsebutton) metoda.  
  
7.  Chcete-li na tlačítko Procházet odebrat z ovládacího prvku úprav procházet, volejte [enablebrowsebutton –](#enablebrowsebutton) metoda s `bEnable` parametr nastaven na `FALSE`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat dvě metody v `CMFCEditBrowseCtrl` – třída: `EnableFolderBrowseButton` a `EnableFileBrowseButton`. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxeditbrowsectrl.h  
  
##  <a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton  
 Zobrazuje, nebo nejsou zobrazeny na tlačítko Procházet na aktuální procházet ovládací prvek upravit.  
  
```  
void EnableBrowseButton(
    BOOL bEnable=TRUE,  
    LPCTSTR szLabel=_T("..."));
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 `TRUE`Chcete-li zobrazit na tlačítko Procházet; `FALSE` nechcete zobrazit na tlačítko Procházet. Výchozí hodnota je `TRUE`.  
  
 `szLabel`  
 Popisek, který se zobrazí na tlačítko Procházet. Výchozí hodnota je " **...** ".  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bEnable` parametr `TRUE`, implementovat vlastní akce se provede při kliknutí na tlačítko Procházet. Pokud chcete implementovat vlastní akci, odvození třídy z `CMFCEditBrowseCtrl` třídy a pak přepsat jeho [onbrowse –](#onbrowse) metoda.  
  
 Pokud `bEnable` parametr `TRUE`, je procházecí režim ovládacího prvku `BrowseMode_Default`, jinak je procházecí režim `BrowseMode_None`. Další informace o režimech Procházet najdete v tématu [GetMode](#getmode) metoda.  
  
##  <a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton  
 Zobrazí tlačítko procházení na aktuální ovládací prvek upravit Procházet a vloží ovládacího prvku *procházení souborů* režimu.  
  
```  
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,  
    LPCTSTR lpszFilter=NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszDefExt`  
 Určuje výchozí příponu názvu souboru, který se používá v dialogovém okně Výběr souboru. Výchozí hodnota je `NULL`.  
  
 `lpszFilter`  
 Určuje výchozí řetězec filtru, který se používá v dialogovém okně Výběr souboru. Výchozí hodnota je `NULL`.  
  
 `dwFlags`  
 Dialogové okno pole příznaky. Výchozí hodnota je bitová kombinace (nebo) OFN_HIDEREADONLY a OFN_OVERWRITEPROMPT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud ovládací prvek upravit procházet je v režimu procházení souborů a uživatel klikne na tlačítko Procházet, tento ovládací prvek zobrazí dialogové okno Výběr standardní soubor.  
  
 Úplný seznam dostupných příznaků, najdete v části [název otevřeného souboru struktura](https://msdn.microsoft.com/library/ms646839.aspx).  
  
##  <a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl::EnableFolderBrowseButton  
 Zobrazí tlačítko procházení na aktuální ovládací prvek upravit Procházet a vloží ovládacího prvku *procházet složky* režimu.  
  
```  
void EnableFolderBrowseButton();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud ovládací prvek upravit procházet je v režimu procházení složek a uživatel klikne na tlačítko Procházet, tento ovládací prvek zobrazí dialogové okno Výběr standardní složku.  
  
##  <a name="getmode"></a>CMFCEditBrowseCtrl::GetMode  
 Načte procházecí režim aktuální ovládacích prvků pro úpravy Procházet.  
  
```  
CMFCEditBrowseCtrl::BrowseMode GetMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z hodnot výčtu, která určuje aktuální režim úpravy procházet ovládacího prvku. Procházecí režim určuje, zda rozhraní zobrazí tlačítko Procházet a jaká akce nastane, když uživatel klikne na toto tlačítko.  
  
 Následující tabulka uvádí možné vrácené hodnoty.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`BrowseMode_Default`|`custom mode`. Akce se programátorem definované se provádí.|  
|`BrowseMode_File`|`file mode`. Zobrazí se dialogové okno Prohlížeč standardní souboru.|  
|`BrowseMode_Folder`|`folder mode`. Zobrazí se dialogové okno Prohlížeč standardní složku.|  
|`BrowseMode_None`|Na tlačítko Procházet se nezobrazí.|  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `CMFCEditBrowseCtrl` objektu je inicializováno `BrowseMode_None` režimu. Upravit procházecí režim s [CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton), a [CMFCEditBrowseCtrl::EnableFolderBrowseButton ](#enablefolderbrowsebutton) metody.  
  
##  <a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate  
 Voláno rámcem po aktualizaci prvku procházet upravit s výsledkem procházet akce.  
  
```  
virtual void OnAfterUpdate();
```  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní akce.  
  
##  <a name="onbrowse"></a>CMFCEditBrowseCtrl::OnBrowse  
 Voláno rámcem po kliknutí na tlačítko Procházet ovládacích prvků pro úpravy Procházet.  
  
```  
virtual void OnBrowse();
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k provedení vlastní kód, když uživatel klikne na tlačítko Procházet ovládacích prvků pro úpravy Procházet. Odvodit vlastní třídu z `CMFCEditBrowseCtrl` třídy a přepsat její `OnBrowse` metoda. V této metodě implementovat vlastní procházet akce a volitelně aktualizovat textového pole ovládacích prvků pro úpravy Procházet. V aplikaci, použijte [enablebrowsebutton –](#enablebrowsebutton) metoda uvést do ovládacího prvku úprav Procházet *vlastní Procházet* režimu.  
  
##  <a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout  
 Překreslí aktuální procházet ovládací prvek upravit.  
  
```  
virtual void OnChangeLayout();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework při procházení režim úprav procházet řízení změn. Další informace najdete v tématu [CMFCEditBrowseCtrl::GetMode](#getmode).  
  
##  <a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::OnDrawBrowseButton  
 Voláno rámcem kreslení na tlačítko Procházet na Procházet ovládací prvek upravit.  
  
```  
virtual void OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsButtonPressed,  
    BOOL bIsButtonHot);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na kontextu zařízení.  
  
 `Rect`  
 Ohraničující obdélník na tlačítko Procházet.  
  
 `bIsButtonPressed`  
 `TRUE`Pokud stisknutí tlačítka; v opačném `FALSE`.  
  
 `bIsButtonHot`  
 `TRUE`Pokud je tlačítko označený; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto funkci v odvozené třídě a přizpůsobení vzhledu na tlačítko Procházet.  
  
##  <a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage  
 Nastaví vlastní obrázek na tlačítko Procházet ovládacích prvků pro úpravy Procházet.  
  
```  
void SetBrowseButtonImage(
    HICON hIcon,  
    BOOL bAutoDestroy= TRUE);

 
void SetBrowseButtonImage(
    HBITMAP hBitmap,  
    BOOL bAutoDestroy= TRUE);  
  
void SetBrowseButtonImage(UINT uiBmpResId);
```  
  
### <a name="parameters"></a>Parametry  
 `hIcon`  
 Popisovač ikonu.  
  
 `hBitmap`  
 Popisovač rastrový obrázek.  
  
 `uiBmpResId`  
 ID prostředku rastrový obrázek.  
  
 `bAutoDestroy`  
 `TRUE`můžete odstranit zadaný ikony nebo rastrového obrázku, když tato metoda ukončí; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li použít vlastní obrázek pro tlačítko procházení. Ve výchozím nastavení, rozhraní získává standardní bitové kopie při procházení ovládací prvek upravit, je *procházení souborů* nebo *procházet složky* režimu.  
  
##  <a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName  
 Voláno rámcem při zadávání názvu objektu neplatný soubor v textovém poli.  
  
```  
virtual BOOL OnIllegalFileName(CString& strFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `strFileName`  
 Určuje název souboru neplatný.  
  
### <a name="return-value"></a>Návratová hodnota  
 By měla vrátit `FALSE` Pokud tento název souboru nelze předat dál dialogu souboru. V takovém případě aktivní zpět do ovládacího prvku úprav a uživatel musí pokračovat úpravy. Výchozí implementace zobrazí okno se zprávou o tom, o název neplatný souboru a vrátí `FALSE`. Potlačí tuto metodu, opravte název souboru a vrátí `TRUE` pro další zpracování.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
