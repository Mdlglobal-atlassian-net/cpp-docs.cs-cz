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
ms.openlocfilehash: 6c611297353f82e4ec90365cbe33db763d9c9838
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367536"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl – třída

Třída `CMFCEditBrowseCtrl` podporuje ovládací prvek pro procházení úprav, což je upravitelné textové pole, které volitelně obsahuje tlačítko pro procházení. Když uživatel klepne na tlačítko Procházet, ovládací prvek provede vlastní akci nebo zobrazí standardní dialogové okno, které obsahuje prohlížeč souborů nebo prohlížeč složek.

## <a name="syntax"></a>Syntaxe

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Výchozí konstruktor.|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Povolí nebo zakáže (skryje) tlačítko procházet.|
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Povolí tlačítko procházet a umístí ovládací prvek pro procházení souborů do režimu *procházení souborů.*|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Povolí tlačítko procházet a umístí ovládací prvek pro procházení pro úpravy do režimu *procházení složek.*|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Vrátí aktuální režim procházení.|
|[CMFCEditBrowseCtrl::onafterupdate](#onafterupdate)|Volat rámci po upravit procházet ovládací prvek je aktualizován s výsledkem procházet akce.|
|[CMFCEditBrowseCtrl::při procházení](#onbrowse)|Volat rámci po uživatel klepne na tlačítko procházet.|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Překreslí aktuální ovládací prvek procházení úprav.|
|[CMFCEditBrowseCtrl::ondrawBrowseButton](#ondrawbrowsebutton)|Volat rámci k nakreslení tlačítko procházet.|
|[CMFCEditBrowseCtrl::OnIllegalNázev_souboru](#onillegalfilename)|Volat rámci při neplatný název souboru byl zadán do ovládacího prvku upravit.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Přeloží zprávy okna před jejich odesláním do funkcí [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systému Windows. Syntaxe a další informace naleznete [v tématu CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Nastaví vlastní obrázek pro tlačítko procházet.|

## <a name="remarks"></a>Poznámky

Pomocí ovládacího prvku pro procházení úprav vyberte název souboru nebo složky. Volitelně můžete pomocí ovládacího prvku provést vlastní akci, například k zobrazení dialogového okna. Můžete zobrazit nebo nezobrazit tlačítko procházet a můžete použít vlastní popisek nebo obrázek na tlačítko.

*Režim procházení* ovládacího prvku proprocházení úprav určuje, zda se zobrazí tlačítko procházet a jaká akce nastane po klepnutí na tlačítko. Další informace naleznete v metodě [GetMode.](#getmode)

Třída `CMFCEditBrowseCtrl` podporuje následující režimy.

- **vlastní režim**

   Vlastní akce se provádí, když uživatel klepne na tlačítko procházet. Můžete například zobrazit dialogové okno specifické pro aplikaci.

- **režim souboru**

   Standardní dialogové okno pro výběr souboru se zobrazí, když uživatel klepne na tlačítko Procházet.

- **režim složky**

   Po klepnutí na tlačítko procházet se zobrazí dialogové okno pro výběr standardní složky.

## <a name="how-to-specify-an-edit-browse-control"></a>Postup: Zadání ovládacího prvku Upravit procházení

Chcete-li do aplikace začlenit ovládací prvek pro procházení úprav, proveďte následující kroky:

1. Pokud chcete implementovat vlastní režim procházení, odvodit vlastní třídu z `CMFCEditBrowseCtrl` třídy a pak přepsat [CMFCEditBrowseCtrl::OnBrowse](#onbrowse) metoda. V přepsané metodě proveďte vlastní akci procházení a aktualizujte ovládací prvek pro procházení úprav s výsledkem.

1. Vloždoujte `CMFCEditBrowseCtrl` objekt nebo odvozený objekt ovládacího prvku pro procházení do nadřazeného objektu okna.

1. Pokud k vytvoření dialogového okna použijete **Průvodce třídami,** přidejte do formuláře dialogového okna ovládací prvek pro úpravy ( `CEdit`). Přidejte také proměnnou pro přístup k ovládacímu prvku v souboru záhlaví. V souboru záhlaví změňte typ `CEdit` proměnné `CMFCEditBrowseCtrl`z na . Ovládací prvek pro procházení úprav bude vytvořen automaticky. Pokud nepoužijete **Průvodce třídou** `CMFCEditBrowseCtrl` , přidejte proměnnou do `Create` souboru záhlaví a zavolejte její metodu.

1. Pokud přidáte ovládací prvek pro procházení úprav do dialogového okna, nastavte výměnu dat pomocí nástroje **ClassWizard.**

1. Voláním metody [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton)nebo [EnableBrowseButton](#enablebrowsebutton) nastavte režim procházení a zobrazte tlačítko procházet. Volání [GetMode](#getmode) metoda získat aktuální režim procházení.

1. Chcete-li poskytnout vlastní obrázek pro tlačítko procházet, zavolejte metodu [SetBrowseButtonImage](#setbrowsebuttonimage) nebo přepište metodu [OnDrawBrowseButton.](#ondrawbrowsebutton)

1. Chcete-li odebrat tlačítko pro procházení z ovládacího prvku upravit procházení, zavolejte metodu [EnableBrowseButton](#enablebrowsebutton) s parametrem *bEnable* nastaveným na hodnotu FALSE.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CEditovat](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat dvě `CMFCEditBrowseCtrl` metody `EnableFolderBrowseButton` `EnableFileBrowseButton`ve třídě: a . Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxeditbrowsectrl.h

## <a name="cmfceditbrowsectrlenablebrowsebutton"></a><a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton

Zobrazí nebo nezobrazí tlačítko procházet v aktuálním ovládacím prvku procházet.

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
TRUE pro zobrazení tlačítka procházet; FALSE nezobrazí tlačítko procházet. Výchozí hodnota je TRUE.

*szLabel*<br/>
Popisek, který se zobrazí na tlačítko procházet. Výchozí hodnota je " **...**".

### <a name="remarks"></a>Poznámky

Pokud je parametr *bEnable* TRUE, implementujte vlastní akci, která se má provést po klepnutí na tlačítko procházet. Chcete-li implementovat vlastní akci, `CMFCEditBrowseCtrl` odvodit třídu z třídy a pak přepsat jeho [OnBrowse](#onbrowse) metody.

Pokud je parametr *bEnable* TRUE, je režim `BrowseMode_Default`procházení ovládacího prvku ; v opačném případě `BrowseMode_None`je režim procházení . Další informace o režimech procházení naleznete v metodě [GetMode.](#getmode)

## <a name="cmfceditbrowsectrlenablefilebrowsebutton"></a><a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton

Zobrazí tlačítko Procházet v aktuálním ovládacím prvku pro procházení úprav a přepne jej do režimu *procházení souborů.*

```
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>Parametry

*lpszDefExt*<br/>
Určuje výchozí příponu názvu souboru, která se používá v dialogovém okně pro výběr souboru. Výchozí hodnota je NULL.

*lpszFiltr*<br/>
Určuje výchozí řetězec filtru, který se používá v dialogovém okně výběru souboru. Výchozí hodnota je NULL.

*dwFlags*<br/>
Příznaky dialogového okna. Výchozí hodnota je bitová kombinace (OR) OFN_HIDEREADONLY a OFN_OVERWRITEPROMPT.

### <a name="remarks"></a>Poznámky

Když je ovládací prvek pro procházení souborů v režimu procházení souborů a uživatel klepne na tlačítko Procházet, zobrazí se standardní dialogové okno pro výběr souboru.

Úplný seznam dostupných příznaků naleznete v tématu [OPENFILENAME structure](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

## <a name="cmfceditbrowsectrlenablefolderbrowsebutton"></a><a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl::EnableFolderBrowseButton

Zobrazí tlačítko Procházet v aktuálním ovládacím prvku pro procházení úprav a umístí ovládací prvek do režimu *procházení složek.*

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Poznámky

Když je ovládací prvek pro procházení úprav v režimu procházení složek a uživatel klepne na tlačítko Procházet, zobrazí se dialogové okno standardní výběr složky.

## <a name="cmfceditbrowsectrlgetmode"></a><a name="getmode"></a>CMFCEditBrowseCtrl::GetMode

Načte režim procházení aktuálního ovládacího prvku proprocházení úprav.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Jedna z hodnot výčtu, která určuje aktuální režim ovládacího prvku proprocházení úprav. Režim procházení určuje, zda rozhraní framework zobrazí tlačítko procházet a jaká akce nastane, když uživatel klepne na toto tlačítko.

V následující tabulce jsou uvedeny možné vrácené hodnoty.

|Hodnota|Popis|
|-----------|-----------------|
|`BrowseMode_Default`|**vlastní režim**. Provádí se akce definovaná programátorem.|
|`BrowseMode_File`|**režimu souboru**. Zobrazí se standardní dialogové okno prohlížeče souborů.|
|`BrowseMode_Folder`|**režimu složek**. Zobrazí se dialogové okno prohlížeče standardních složek.|
|`BrowseMode_None`|Tlačítko procházet se nezobrazí.|

### <a name="remarks"></a>Poznámky

Ve výchozím `CMFCEditBrowseCtrl` nastavení je objekt `BrowseMode_None` inicializován do režimu. Upravte režim procházení pomocí metod [CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)a [CMFCEditBrowseCtrl::EnableFolderBrowseButton.](#enablefolderbrowsebutton)

## <a name="cmfceditbrowsectrlonafterupdate"></a><a name="onafterupdate"></a>CMFCEditBrowseCtrl::onafterupdate

Volat rámci po upravit procházet ovládací prvek je aktualizován s výsledkem procházet akce.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě k implementaci vlastní akce.

## <a name="cmfceditbrowsectrlonbrowse"></a><a name="onbrowse"></a>CMFCEditBrowseCtrl::při procházení

Volat rámci po uživatel klepne na tlačítko procházet upravit procházet ovládacího prvku.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete spustit vlastní kód, když uživatel klepne na tlačítko Procházet ovládacího prvku proprocházení. Odvodit vlastní `CMFCEditBrowseCtrl` třídu z `OnBrowse` třídy a přepsat její metodu. V této metodě implementujte vlastní akci procházení a volitelně aktualizujte textové pole ovládacího prvku upravit procházení. V aplikaci použijte metodu [EnableBrowseButton](#enablebrowsebutton) k přepychu ovládacího prvku pro procházení úprav do vlastního režimu *procházení.*

## <a name="cmfceditbrowsectrlonchangelayout"></a><a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout

Překreslí aktuální ovládací prvek procházení úprav.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu při změně režimu procházení ovládacího prvku procházet. Další informace naleznete v tématu [CMFCEditBrowseCtrl::GetMode](#getmode).

## <a name="cmfceditbrowsectrlondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::ondrawBrowseButton

Volat rámci nakreslit tlačítko procházet na upravit procházet ovládací prvek.

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení.

*Rect*<br/>
Ohraničovací obdélník tlačítka procházet.

*bIsButtonStisknuto*<br/>
PRAVDA, pokud je stisknuto tlačítko; jinak NEPRAVDA.

*bIsButtonHot*<br/>
TRUE, pokud je tlačítko zvýrazněno; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci v odvozené třídě přizpůsobit vzhled tlačítka procházet.

## <a name="cmfceditbrowsectrlsetbrowsebuttonimage"></a><a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage

Nastaví vlastní obrázek na tlačítku Procházet ovládacího prvku Upravit procházení.

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

*hIkona*<br/>
Popisovač ikony.

*hBitmap*<br/>
Popisovač rastrového obrázek.

*uiBmpResId*<br/>
ID prostředku rastrového plánu.

*bAutoDestroy*<br/>
TRUE pro odstranění zadané ikony nebo bitmapy při ukončení této metody; jinak NEPRAVDA. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete použít vlastní obrázek na tlačítko procházet. Ve výchozím nastavení rozhraní získá standardní obraz, když je ovládací prvek pro procházení úprav v režimu *procházení souborů* nebo *procházení složek.*

## <a name="cmfceditbrowsectrlonillegalfilename"></a><a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalNázev_souboru

Volat rámci při neplatný název souboru byl zadán do ovládacího prvku upravit.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>Parametry

*Strfilename*<br/>
Určuje neplatný název souboru.

### <a name="return-value"></a>Návratová hodnota

By měl vrátit FALSE, pokud tento název souboru nelze předat dále do dialogového okna souboru. V takovém případě je fokus nastaven zpět na ovládací prvek úprav a uživatel by měl pokračovat v úpravách. Výchozí implementace zobrazí okno se zprávou s dělit uživatele o neplatném názvu souboru a vrátí hodnotu FALSE. Tuto metodu můžete přepsat, opravit název souboru a vrátit hodnotu TRUE pro další zpracování.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
