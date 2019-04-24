---
title: Cmfceditbrowsectrl – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 0c6fb39e17e22bcac60d50b87f7370c6a9f91db9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237639"
---
# <a name="cmfceditbrowsectrl-class"></a>Cmfceditbrowsectrl – třída

`CMFCEditBrowseCtrl` Třída podporuje textové pole procházení, což je upravitelné textové pole, který volitelně obsahuje tlačítko Procházet. Když uživatel klikne na tlačítko Procházet, ovládací prvek provede vlastní akci nebo zobrazí standardní dialogové okno, které obsahuje prohlížeč souborů nebo prohlížeč složek.

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
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Povolí tlačítko Procházet a umístí ovládací prvek pro úpravy Procházet *procházení souborů* režimu.|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Povolí tlačítko Procházet a umístí ovládací prvek pro úpravy Procházet *procházení složek* režimu.|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Vrátí aktuální režim procházení.|
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Volá se rozhraním po aktualizaci textové pole procházení s výsledek akce procházení.|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Volá se rozhraním po kliknutí na tlačítko Procházet.|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Překreslí aktuální textové pole procházení.|
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Volá se rozhraním, chcete-li nakreslit tlačítko Procházet.|
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Volá se rozhraním, když byl zadán neplatný název souboru v textovém poli.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Přeloží okno zprávy před odesláním do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkce Windows. Syntaxe a další informace najdete v tématu [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Nastaví vlastní obrázek pro tlačítko Procházet.|

## <a name="remarks"></a>Poznámky

Použití ovládacího prvku úprav Procházet a vyberte název souboru nebo složky. Volitelně můžete použijte ovládací prvek k provedení vlastní akce, například k zobrazení dialogového okna. Můžete zobrazit nebo se nezobrazí tlačítko Procházet a na tlačítko můžete použít vlastní popisek nebo image.

*Režimu procházení* procházet upravit ovládací prvek určuje, zda se zobrazí tlačítko Procházet a jaká akce se vyvolá se při kliknutí na tlačítko. Další informace najdete v tématu [GetMode](#getmode) metody.

`CMFCEditBrowseCtrl` Třída podporuje následující režimy.

- **vlastní režim**

   Vlastní akce se provádí, když uživatel klikne na tlačítko Procházet. Například může zobrazit dialogové okno s konkrétní aplikace.

- **režim souboru**

   Když uživatel klikne na tlačítko Procházet, zobrazí se dialogové okno Výběr standardní soubor.

- **režimu složky**

   Když uživatel klikne na tlačítko Procházet, zobrazí se dialogové okno Výběr standardní složku.

## <a name="how-to-specify-an-edit-browse-control"></a>Postupy: Zadejte textové pole procházení

Proveďte následující kroky a začlenit procházet ovládacího prvku pro úpravy ve vaší aplikaci:

1. Pokud chcete implementovat vlastní procházecí režim, odvodit vlastní třídu z `CMFCEditBrowseCtrl` třídy a pak přepsat [CMFCEditBrowseCtrl::OnBrowse](#onbrowse) metoda. Přepsané metody provést akci vlastní procházení a aktualizace textové pole procházení k výsledku.

1. Buď pro vložení `CMFCEditBrowseCtrl` nebo objektu odvozené úpravy procházet ovládacího prvku do nadřazeného okna objektu.

1. Pokud používáte **Průvodce třídami** vytvořit dialogové okno, přidejte ovládací prvek úprav ( `CEdit`) do pole formuláře dialogového okna. Přidejte také proměnnou pro přístup k ovládacímu prvku v hlavičkovém souboru. V souboru záhlaví změnit typ proměnné z `CEdit` k `CMFCEditBrowseCtrl`. Textové pole procházení se vytvoří automaticky. Pokud použijete **Průvodce třídami**, přidat `CMFCEditBrowseCtrl` proměnné pro hlavičku souboru a poté zavolejte jeho `Create` metoda.

1. Pokud přidáte ovládací prvek pro procházení úpravy do dialogového okna, použijte **ClassWizard** nástroj nastavení dat systému exchange.

1. Volání [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton), nebo [enablebrowsebutton –](#enablebrowsebutton) metodu pro nastavení režimu procházení a zobrazení tlačítka Procházet. Volání [GetMode](#getmode) metodu k získání aktuální procházecí režim.

1. Pokud chcete poskytnout vlastní image pro tlačítko procházení, zavolejte [SetBrowseButtonImage](#setbrowsebuttonimage) metody nebo přepsání [OnDrawBrowseButton](#ondrawbrowsebutton) metody.

1. Chcete-li na tlačítko Procházet odebrání textové pole procházení, zavolejte [enablebrowsebutton –](#enablebrowsebutton) metodu *bEnable* parametr nastaven na hodnotu FALSE.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít dvě metody v `CMFCEditBrowseCtrl` třídy: `EnableFolderBrowseButton` a `EnableFileBrowseButton`. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxeditbrowsectrl.h

##  <a name="enablebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableBrowseButton

Zobrazí nebo nejsou zobrazeny na tlačítko Procházet na aktuální textové pole procházení.

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
TRUE, pokud chcete zobrazit tlačítko procházení; FALSE, nedojde k zobrazení na tlačítko Procházet. Výchozí hodnota je TRUE.

*szLabel*<br/>
Popisek, který je zobrazený na tlačítku pro procházení. Výchozí hodnota je " **...** ".

### <a name="remarks"></a>Poznámky

Pokud *bEnable* parametr má hodnotu TRUE, implementujte vlastní akce k provedení po kliknutí na tlačítko Procházet. K provedení vlastní akce, odvoďte třídu z `CMFCEditBrowseCtrl` třídy a potom přepíše jeho [onbrowse –](#onbrowse) metoda.

Pokud *bEnable* parametr má hodnotu TRUE, je procházecí režim ovládacího prvku `BrowseMode_Default`; v opačném případě je procházecí režim `BrowseMode_None`. Další informace o procházení režimech najdete v článku [GetMode](#getmode) metody.

##  <a name="enablefilebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFileBrowseButton

Zobrazí tlačítko procházení v aktuální textové pole procházení a umístí ovládací prvek *procházení souborů* režimu.

```
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>Parametry

*lpszDefExt*<br/>
Určuje výchozí příponu souboru, který se používá v dialogovém okně Výběr souboru. Výchozí hodnota je NULL.

*lpszFilter*<br/>
Určuje výchozí řetězec filtru, který se používá v dialogovém okně Výběr souboru. Výchozí hodnota je NULL.

*dwFlags*<br/>
Dialogové okno pole příznaky. Výchozí hodnota je bitová kombinace (nebo) OFN_HIDEREADONLY a OFN_OVERWRITEPROMPT.

### <a name="remarks"></a>Poznámky

Když je textové pole procházení v režimu procházení souboru a uživatel klikne na tlačítko Procházet, ovládací prvek zobrazí dialogové okno Výběr standardní soubor.

Úplný seznam dostupných příznaků najdete v tématu [LPSTRFILE struktury](/windows/desktop/api/commdlg/ns-commdlg-tagofna).

##  <a name="enablefolderbrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFolderBrowseButton

Zobrazí tlačítko procházení v aktuální textové pole procházení a umístí ovládací prvek *procházení složek* režimu.

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Poznámky

Když je textové pole procházení v režimu procházení složky a uživatel klikne na tlačítko Procházet, ovládací prvek zobrazí dialogové okno Výběr standardní složku.

##  <a name="getmode"></a>  CMFCEditBrowseCtrl::GetMode

Načte režim procházení aktuální textové pole procházení.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Jedna z hodnot výčtu, které určuje aktuální režim úpravy procházet ovládacího prvku. Procházecí režim určuje, zda zobrazí rozhraní na tlačítko Procházet a jaké akce nastane, pokud uživatel klikne na toto tlačítko.

Následující tabulka obsahuje seznam možných vrácených hodnot.

|Value|Popis|
|-----------|-----------------|
|`BrowseMode_Default`|**vlastní režim**. Programátorem definované akce je provedena.|
|`BrowseMode_File`|**režim souboru**. Zobrazí se dialogové okno Prohlížeč standardní soubor.|
|`BrowseMode_Folder`|**režimu složky**. Zobrazí se dialogové okno Prohlížeč standardní složku.|
|`BrowseMode_None`|Není zobrazeno tlačítko Procházet.|

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CMFCEditBrowseCtrl` objekt je inicializován na `BrowseMode_None` režimu. Upravit procházecí režim s [CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton), a [CMFCEditBrowseCtrl::EnableFolderBrowseButton ](#enablefolderbrowsebutton) metody.

##  <a name="onafterupdate"></a>  CMFCEditBrowseCtrl::OnAfterUpdate

Volá se rozhraním po aktualizaci textové pole procházení s výsledek akce procházení.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě k provedení vlastní akce.

##  <a name="onbrowse"></a>  CMFCEditBrowseCtrl::OnBrowse

Volá se rozhraním po kliknutí na tlačítko Procházet ovládacích prvků pro úpravy Procházet.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete spouštět vlastní kód, když uživatel klikne na tlačítko Procházet ovládacích prvků pro úpravy Procházet. Odvodit vlastní třídu z `CMFCEditBrowseCtrl` třídy a přepsat její `OnBrowse` metody. V této metodě implementovat vlastní procházení akce a volitelně aktualizaci textového pole ovládacích prvků pro úpravy Procházet. Ve vaší aplikaci používat [enablebrowsebutton –](#enablebrowsebutton) metoda vložit textové pole procházení *vlastní procházení* režimu.

##  <a name="onchangelayout"></a>  CMFCEditBrowseCtrl::OnChangeLayout

Překreslí aktuální textové pole procházení.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když procházecí režim úpravy procházet řízení změn. Další informace najdete v tématu [CMFCEditBrowseCtrl::GetMode](#getmode).

##  <a name="ondrawbrowsebutton"></a>  CMFCEditBrowseCtrl::OnDrawBrowseButton

Volá se rozhraním, chcete-li nakreslit tlačítko Procházet na textové pole procházení.

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení.

*Rect*<br/>
Ohraničující obdélník na tlačítko Procházet.

*bIsButtonPressed*<br/>
Hodnota TRUE, pokud se stiskne tlačítko; v opačném případě hodnota FALSE.

*bIsButtonHot*<br/>
Hodnota TRUE, pokud je zvýrazněný na tlačítko. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci v odvozené třídě přizpůsobit vzhled na tlačítko Procházet.

##  <a name="setbrowsebuttonimage"></a>  CMFCEditBrowseCtrl::SetBrowseButtonImage

Nastaví vlastní obrázek na tlačítko procházení u ovládacího prvku pro úpravy Procházet.

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

*hIcon*<br/>
Popisovač ikony.

*hBitmap*<br/>
Popisovač rastrový obrázek.

*uiBmpResId*<br/>
ID prostředku rastrového obrázku.

*bAutoDestroy*<br/>
TRUE, pokud chcete odstranit zadané ikona nebo rastrový obrázek, když se tato metoda ukončí; v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete použít vlastní obrázek na tlačítko Procházet. Ve výchozím nastavení, rozhraní získá standardní bitové kopie, když je textové pole procházení v *procházení souborů* nebo *procházení složek* režimu.

##  <a name="onillegalfilename"></a>  CMFCEditBrowseCtrl::OnIllegalFileName

Volá se rozhraním, když byl zadán neplatný název souboru v textovém poli.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>Parametry

*strFileName*<br/>
Určuje název souboru neplatné.

### <a name="return-value"></a>Návratová hodnota

By měl vrátit hodnotu FALSE, pokud tento název souboru nelze předat dál dialogového okna souboru. V tomto případě fokus se nastaví zpátky do ovládacího prvku edit a uživatel by měl pokračovat v úpravách. Výchozí implementace zobrazí okno se zprávou sděluje uživateli o neplatný název souboru a vrátí hodnotu FALSE. Potlačí tuto metodu, opravte název souboru a vrátí hodnotu TRUE pro další zpracování.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
