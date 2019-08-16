---
title: CMFCEditBrowseCtrl – třída
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
ms.openlocfilehash: db99c5e72e84bb359184f4c62594fcddff7d8ff6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505354"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl – třída

`CMFCEditBrowseCtrl` Třída podporuje ovládací prvek pro úpravy, který je upravitelný textový rámeček, který může volitelně obsahovat tlačítko pro procházení. Když uživatel klikne na tlačítko Procházet, ovládací prvek provede vlastní akci nebo zobrazí standardní dialogové okno, které obsahuje prohlížeč souborů nebo prohlížeč složek.

## <a name="syntax"></a>Syntaxe

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Výchozí konstruktor|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Povolí nebo zakáže (skryje) tlačítko Procházet.|
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Povolí tlačítko Procházet a vloží ovládací prvek pro úpravy do režimu *procházení souborů* .|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Povolí tlačítko Procházet a vloží ovládací prvek pro procházení do složky do režimu *procházení* .|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Vrátí aktuální režim procházení.|
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Volá se rozhraním, když se ovládací prvek pro procházení úprav aktualizuje s výsledkem akce procházení.|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Volá se rozhraním, když uživatel klikne na tlačítko Procházet.|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Překreslí aktuální ovládací prvek pro úpravy.|
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Volá se rozhraním, aby se nakreslilo tlačítko pro procházení.|
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Volá se rozhraním, když se v textovém poli zadal neplatný název souboru.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Přeloží zprávy oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Syntaxi a další informace naleznete v tématu [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Nastaví vlastní obrázek pro tlačítko Procházet.|

## <a name="remarks"></a>Poznámky

Pomocí ovládacího prvku pro úpravu procházení vyberte název souboru nebo složky. Volitelně můžete použít ovládací prvek k provedení vlastní akce, například k zobrazení dialogového okna. Tlačítko Procházet můžete zobrazit nebo nezobrazit a můžete použít vlastní popisek nebo obrázek na tlačítku.

*Režim procházení* ovládacího prvku pro úpravy určuje, zda se zobrazí tlačítko Procházet a jaká akce nastane při kliknutí na tlačítko. Další informace naleznete v tématu metoda [GetMode](#getmode) .

`CMFCEditBrowseCtrl` Třída podporuje následující režimy.

- **vlastní režim**

   Vlastní akce se provede, když uživatel klikne na tlačítko Procházet. Můžete například zobrazit dialogové okno specifické pro aplikaci.

- **režim souboru**

   Standardní dialogové okno pro výběr souboru se zobrazí, když uživatel klikne na tlačítko Procházet.

- **režim složky**

   Dialogové okno pro výběr standardní složky se zobrazí, když uživatel klikne na tlačítko Procházet.

## <a name="how-to-specify-an-edit-browse-control"></a>Postupy: Zadání ovládacího prvku pro procházení pro úpravy

Provedením následujících kroků zahrňte do své aplikace ovládací prvek pro procházení úprav:

1. Pokud chcete implementovat vlastní režim procházení, odvodit z `CMFCEditBrowseCtrl` třídy vlastní třídu a potom přepsat metodu [CMFCEditBrowseCtrl:: Browse](#onbrowse) . V přepsané metodě spusťte vlastní akci procházení a aktualizujte ovládací prvek pro úpravu procházení s výsledkem.

1. Vložte buď `CMFCEditBrowseCtrl` objekt, nebo odvozený objekt ovládacího prvku pro úpravy procházení do objektu nadřazeného okna.

1. Použijete-li **Průvodce třídami** k vytvoření dialogového okna, přidejte ovládací prvek pro úpravy `CEdit`() do formuláře dialogového okna. Přidejte také proměnnou pro přístup k ovládacímu prvku v hlavičkovém souboru. V souboru hlaviček změňte typ proměnné z `CEdit` na. `CMFCEditBrowseCtrl` Ovládací prvek pro procházení úprav bude vytvořen automaticky. Pokud nepoužijete **Průvodce třídami**, přidejte `CMFCEditBrowseCtrl` do hlavičkového souboru proměnnou a potom zavolejte její `Create` metodu.

1. Přidáte-li do dialogového okna Ovládací prvek pro úpravy, použijte nástroj **ClassWizard** k nastavení výměny dat.

1. Pro nastavení režimu procházení a zobrazení tlačítka Procházet volejte metodu [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton)nebo [EnableBrowseButton](#enablebrowsebutton) . Pro získání [](#getmode) aktuálního režimu procházení volejte metodu GetMode.

1. Chcete-li zadat vlastní obrázek pro tlačítko Procházet, zavolejte metodu [SetBrowseButtonImage](#setbrowsebuttonimage) nebo přepište metodu [OnDrawBrowseButton](#ondrawbrowsebutton) .

1. Chcete-li odebrat tlačítko Procházet z ovládacího prvku pro procházení úprav, zavolejte metodu [EnableBrowseButton](#enablebrowsebutton) s parametrem *bEnable* nastaveným na hodnotu false.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít dvě metody ve `CMFCEditBrowseCtrl` třídě: `EnableFolderBrowseButton` a `EnableFileBrowseButton`. Tento příklad je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxeditbrowsectrl. h

##  <a name="enablebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableBrowseButton

Zobrazí nebo nezobrazuje tlačítko pro procházení v aktuálním ovládacím prvku pro úpravy.

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
TRUE pro zobrazení tlačítka Procházet; FALSE – nezobrazit tlačítko pro procházení Výchozí hodnota je TRUE (pravda).

*szLabel*<br/>
Popisek, který se zobrazí na tlačítku pro procházení. Výchozí hodnota je " **...** ".

### <a name="remarks"></a>Poznámky

Pokud má parametr *bEnable* hodnotu true, implementujte vlastní akci, která se provede při kliknutí na tlačítko Procházet. Chcete-li implementovat vlastní akci, odvodit třídu z `CMFCEditBrowseCtrl` třídy a potom přepsat svou metodu pro [procházení](#onbrowse) .

Pokud má parametr *bEnable* hodnotu true, je `BrowseMode_Default`režim procházení ovládacího prvku. v opačném případě je `BrowseMode_None`režim procházení. Další informace o režimech procházení naleznete v tématu [](#getmode) metoda GetMode.

##  <a name="enablefilebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFileBrowseButton

Zobrazí tlačítko Procházet v aktuálním ovládacím prvku pro úpravy a vloží ovládací prvek do režimu *procházení souborů* .

```
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>Parametry

*lpszDefExt*<br/>
Určuje výchozí příponu názvu souboru, která se používá v dialogovém okně Výběr souboru. Výchozí hodnota je NULL.

*lpszFilter*<br/>
Určuje výchozí řetězec filtru, který se používá v dialogovém okně Výběr souboru. Výchozí hodnota je NULL.

*dwFlags*<br/>
Příznaky dialogových oken Výchozí hodnota je bitová kombinace (nebo) hodnot OFN_HIDEREADONLY a OFN_OVERWRITEPROMPT.

### <a name="remarks"></a>Poznámky

Když je ovládací prvek pro procházení úprav v režimu procházení souborů a uživatel klikne na tlačítko Procházet, ovládací prvek zobrazí standardní dialogové okno pro výběr souboru.

Úplný seznam dostupných příznaků najdete v tématu [Struktura lpstrFile](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

##  <a name="enablefolderbrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFolderBrowseButton

Zobrazí tlačítko Procházet v aktuálním ovládacím prvku pro úpravy a vloží ovládací prvek do režimu *procházení složky* .

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Poznámky

Když je ovládací prvek procházení pro úpravy v režimu procházení složky a uživatel klikne na tlačítko Procházet, ovládací prvek zobrazí standardní dialogové okno pro výběr složky.

##  <a name="getmode"></a>CMFCEditBrowseCtrl:: GetMode

Načte režim procházení aktuálního ovládacího prvku pro úpravy.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Jedna z hodnot výčtu, která určuje aktuální režim ovládacího prvku pro procházení úprav. Režim procházení určuje, zda rozhraní zobrazí tlačítko Procházet a k čemu dojde, když uživatel klikne na toto tlačítko.

V následující tabulce jsou uvedeny možné návratové hodnoty.

|Value|Popis|
|-----------|-----------------|
|`BrowseMode_Default`|**vlastní režim**. Provede se akce definovaná programátorem.|
|`BrowseMode_File`|**režim souboru**. Zobrazí se standardní dialogové okno prohlížeče souborů.|
|`BrowseMode_Folder`|**režim složky**. Zobrazí se dialogové okno standardní prohlížeč složek.|
|`BrowseMode_None`|Tlačítko Procházet není zobrazeno.|

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CMFCEditBrowseCtrl` je objekt inicializován do `BrowseMode_None` režimu. Upravte režim procházení pomocí metod [CMFCEditBrowseCtrl:: EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl:: EnableFileBrowseButton](#enablefilebrowsebutton)a [CMFCEditBrowseCtrl:: EnableFolderBrowseButton](#enablefolderbrowsebutton) .

##  <a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate

Volá se rozhraním, když se ovládací prvek pro procházení úprav aktualizuje s výsledkem akce procházení.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastní akce.

##  <a name="onbrowse"></a>  CMFCEditBrowseCtrl::OnBrowse

Volá se rozhraním, když uživatel klikne na tlačítko Procházet v ovládacím prvku pro procházení úprav.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li spustit vlastní kód, když uživatel klikne na tlačítko Procházet v ovládacím prvku upravit procházení. Odvodit vlastní třídu od `CMFCEditBrowseCtrl` třídy a přepsat její `OnBrowse` metodu. V této metodě implementujte vlastní akci procházení a volitelně aktualizujte textové pole ovládacího prvku pro procházení. V aplikaci použijte metodu [EnableBrowseButton](#enablebrowsebutton) k umístění ovládacího prvku pro procházení pro úpravy v režimu *vlastního procházení* .

##  <a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout

Překreslí aktuální ovládací prvek pro úpravy.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když se změní režim procházení ovládacího prvku pro procházení. Další informace naleznete v tématu [CMFCEditBrowseCtrl:: GetMode](#getmode).

##  <a name="ondrawbrowsebutton"></a>  CMFCEditBrowseCtrl::OnDrawBrowseButton

Volá se rozhraním, aby se nakreslilo tlačítko pro procházení v ovládacím prvku pro úpravy.

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

*OBD*<br/>
Ohraničující obdélník tlačítka pro procházení

*bIsButtonPressed*<br/>
TRUE, pokud je stisknuto tlačítko; v opačném případě FALSE.

*bIsButtonHot*<br/>
TRUE, pokud je tlačítko zvýrazněno; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto funkci můžete přepsat v odvozené třídě a přizpůsobit tak vzhled tlačítka Procházet.

##  <a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage

Nastaví vlastní obrázek na tlačítku pro procházení ovládacího prvku pro procházení.

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
Popisovač rastrového obrázku.

*uiBmpResId*<br/>
ID prostředku rastrového obrázku.

*bAutoDestroy*<br/>
TRUE pro odstranění zadané ikony nebo rastrového obrázku při ukončení této metody; v opačném případě FALSE. Výchozí hodnota je TRUE (pravda).

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li použít vlastní image na tlačítko Procházet. Ve výchozím nastavení rozhraní získá standardní obrázek, když je ovládací prvek pro procházení úprav v režimu procházení *souborů* nebo *Složka procházení* .

##  <a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName

Volá se rozhraním, když se v textovém poli zadal neplatný název souboru.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>Parametry

*strFileName*<br/>
Určuje neplatný název souboru.

### <a name="return-value"></a>Návratová hodnota

By měla vracet hodnotu FALSE, pokud tento název souboru nelze předat dál do dialogového okna souboru. V takovém případě se fokus nastaví zpátky na ovládací prvek pro úpravy a uživatel by měl pokračovat v úpravách. Výchozí implementace zobrazí okno se zprávou oznamující uživateli nepovolený název souboru a vrátí hodnotu FALSE. Tuto metodu můžete přepsat, opravit název souboru a pro další zpracování vrátit hodnotu TRUE.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
