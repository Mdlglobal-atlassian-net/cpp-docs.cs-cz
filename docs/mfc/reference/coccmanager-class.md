---
title: COccManager – třída
ms.date: 11/04/2016
f1_keywords:
- COccManager
- AFXOCC/COccManager
- AFXOCC/COccManager::CreateContainer
- AFXOCC/COccManager::CreateDlgControls
- AFXOCC/COccManager::CreateSite
- AFXOCC/COccManager::GetDefBtnCode
- AFXOCC/COccManager::IsDialogMessage
- AFXOCC/COccManager::IsLabelControl
- AFXOCC/COccManager::IsMatchingMnemonic
- AFXOCC/COccManager::OnEvent
- AFXOCC/COccManager::PostCreateDialog
- AFXOCC/COccManager::PreCreateDialog
- AFXOCC/COccManager::SetDefaultButton
- AFXOCC/COccManager::SplitDialogTemplate
helpviewer_keywords:
- COccManager [MFC], CreateContainer
- COccManager [MFC], CreateDlgControls
- COccManager [MFC], CreateSite
- COccManager [MFC], GetDefBtnCode
- COccManager [MFC], IsDialogMessage
- COccManager [MFC], IsLabelControl
- COccManager [MFC], IsMatchingMnemonic
- COccManager [MFC], OnEvent
- COccManager [MFC], PostCreateDialog
- COccManager [MFC], PreCreateDialog
- COccManager [MFC], SetDefaultButton
- COccManager [MFC], SplitDialogTemplate
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
ms.openlocfilehash: c2a49e3396879e5f1e0864ab5342b57541c6b36c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504490"
---
# <a name="coccmanager-class"></a>COccManager – třída

Spravuje různé weby vlastních ovládacích prvků. implementováno objekty `COleControlSite`a. `COleControlContainer`

## <a name="syntax"></a>Syntaxe

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COccManager::CreateContainer](#createcontainer)|`COleContainer` Vytvoří objekt.|
|[COccManager::CreateDlgControls](#createdlgcontrols)|Vytvoří ovládací prvky ActiveX hostované přidruženým `COleContainer` objektem.|
|[COccManager::CreateSite](#createsite)|`COleClientSite` Vytvoří objekt.|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Načte kód výchozího tlačítka.|
|[COccManager::IsDialogMessage](#isdialogmessage)|Určuje cíl zprávy dialogového okna.|
|[COccManager::IsLabelControl](#islabelcontrol)|Určuje, zda je určený ovládací prvek ovládací prvek popisek.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Určuje, zda aktuální ovládací prvek odpovídá symbolickému znaku zadaného ovládacího prvku.|
|[COccManager::OnEvent](#onevent)|Pokusí se zpracovat zadanou událost.|
|[COccManager::PostCreateDialog](#postcreatedialog)|Uvolní prostředky přidělené při vytváření dialogu.|
|[COccManager::PreCreateDialog](#precreatedialog)|Zpracuje šablonu dialogového okna pro ovládací prvky ActiveX.|
|[COccManager::SetDefaultButton](#setdefaultbutton)|Přepíná výchozí stav zadaného ovládacího prvku.|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Odděluje všechny existující ovládací prvky ActiveX od běžných ovládacích prvků v zadané šabloně dialogového okna.|

## <a name="remarks"></a>Poznámky

Základní třída `CNoTrackObject`je nedokumentovaná základní třída (která se nachází v AFXTLS. H). Určené pro použití v rozhraní knihovny MFC, třídy odvozené od `CNoTrackObject` třídy jsou vyloučeny z detekce nevrácení paměti. Nedoporučujeme odvozovat přímo z `CNoTrackObject`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxocc. h

##  <a name="createcontainer"></a>COccManager:: CreateContainer

Volá se rozhraním, aby se vytvořil kontejner ovládacího prvku.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na objekt okna přidružený k vlastnímu kontejneru webu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený kontejner; jinak NULL.

### <a name="remarks"></a>Poznámky

Další informace o vytváření vlastních lokalit naleznete v tématu [COleControlContainer:: AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls

Voláním této funkce vytvoříte ovládací prvky ActiveX určené parametrem *pOccDialogInfo* .

```
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    LPCTSTR lpszResourceName,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);

virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    void* lpResource,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
Ukazatel na nadřazený objekt dialogového okna.

*lpszResourceName*<br/>
Název vytvářeného prostředku.

*pOccDialogInfo*<br/>
Ukazatel na šablonu dialogového okna sloužící k vytvoření objektu dialogového okna.

*lpResource*<br/>
Ukazatel na prostředek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl ovládací prvek úspěšně vytvořen; jinak nula.

##  <a name="createsite"></a>COccManager::CreateSite

Volá se rozhraním, aby se vytvořila lokalita ovládacího prvku, která je hostovaná kontejnerem, na který odkazuje *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parametry

*pCtrlCont*<br/>
Ukazatel na kontejner ovládacího prvku hostujícího novou lokalitu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený web ovládacího prvku.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce vytvoříte vlastní web ovládacího prvku pomocí třídy odvozené od [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

Každý kontejner ovládacích prvků může hostovat několik lokalit. Vytvořte další weby s více voláními `CreateSite`.

##  <a name="getdefbtncode"></a>COccManager::GetDefBtnCode

Voláním této funkce určíte, zda je ovládací prvek výchozí tlačítko pro vložení.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Objekt okna obsahující ovládací prvek tlačítko.

### <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot:

- Ovládací prvek DLGC_DEFPUSHBUTTON je výchozí tlačítko v dialogovém okně.

- Ovládací prvek DLGC_UNDEFPUSHBUTTON není výchozím tlačítkem v dialogovém okně.

- **0** ovládací prvek není tlačítko.

##  <a name="isdialogmessage"></a>COccManager::IsDialogMessage

Volá se rozhraním, aby se zjistilo, jestli je zpráva určená pro zadané dialogové okno, a pokud je, zpracovává zprávu.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*pWndDlg*<br/>
Ukazatel na zamýšlený cílový dialog zprávy.

*lpMsg*<br/>
Ukazatel na `MSG` strukturu, která obsahuje zprávu, kterou chcete zkontrolovat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je zpráva zpracována; jinak nula.

### <a name="remarks"></a>Poznámky

Výchozím chováním `IsDialogMessage` je kontrolovat zprávy klávesnice a převést je na výběr pro příslušné dialogové okno. Například Klávesa TAB při stisknutí vybere další ovládací prvek nebo skupinu ovládacích prvků.

Tuto funkci můžete přepsat tak, aby poskytovala vlastní chování pro zprávy odeslané do určeného dialogového okna.

##  <a name="islabelcontrol"></a>  COccManager::IsLabelControl

Voláním této funkce určíte, zda je určený ovládací prvek ovládací prvek popisek.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno obsahující ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je ovládací prvek popisek; jinak nula

### <a name="remarks"></a>Poznámky

Ovládací prvek popisek je ten, který funguje jako popisek pro jakýkoli ovládací prvek, který je v řazení další.

##  <a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic

Voláním této funkce určíte, zda aktuální symbolické symbol odpovídá, který je reprezentován ovládacím prvkem.

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno obsahující ovládací prvek.

*lpMsg*<br/>
Ukazatel na zprávu obsahující klávesové zkratky, který se má shodovat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se ovládací prvky shodují s ovládacím prvkem; jinak nula

### <a name="remarks"></a>Poznámky

##  <a name="onevent"></a>COccManager::-sudý

Volá se rozhraním, aby se zpracovala zadaná událost.

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*pCmdTarget*<br/>
Ukazatel na `CCmdTarget` objekt, který se pokouší zpracovat událost

*idCtrl*<br/>
ID prostředku ovládacího prvku

*pEvent*<br/>
Událost, která se zpracovává.

*pHandlerInfo*<br/>
Pokud hodnota není null `OnEvent` , vyplní `pTarget` místo `pmf` odeslání příkazu členy `AFX_CMDHANDLERINFO` a strukturu. Tento parametr obvykle by měl mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla událost zpracována, jinak nula.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci pro přizpůsobení výchozího procesu zpracování událostí.

##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog

Volá se rozhraním před vytvořením vlastního dialogového okna pro zpracování šablony dialogového okna pro ovládací prvky ActiveX.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO` Struktura obsahující informace o šabloně dialogového okna a všech ovládacích prvcích ActiveX hostovaných dialogem.

*pOrigTemplate*<br/>
Ukazatel na šablonu dialogového okna, který se má použít při vytváření dialogového okna.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu šablon dialogového okna použitou k vytvoření dialogového okna.

### <a name="remarks"></a>Poznámky

Výchozí chování provede volání `SplitDialogTemplate`, určení, zda existují nějaké ovládací prvky ActiveX a potom vrátí výslednou šablonu dialogového okna.

Přepište tuto funkci pro přizpůsobení procesu vytvoření dialogového okna hostujícího ovládací prvky ActiveX.

##  <a name="postcreatedialog"></a>COccManager::P ostCreateDialog

Volá se rozhraním, aby se uvolnila paměť přidělená pro šablonu dialogového okna.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO` Struktura obsahující informace o šabloně dialogového okna a všech ovládacích prvcích ActiveX hostovaných dialogem.

### <a name="remarks"></a>Poznámky

Tato paměť byla přidělena voláním `SplitDialogTemplate`a byla použita pro všechny hostované ovládací prvky ActiveX v dialogovém okně.

Tuto funkci můžete přepsat, chcete-li upravit proces čištění všech prostředků používaných objektem dialogového okna.

##  <a name="setdefaultbutton"></a>COccManager::SetDefaultButton

Voláním této funkce nastavíte ovládací prvek jako výchozí tlačítko.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno obsahující ovládací prvek.

*bDefault*<br/>
Nenulové, pokud by se měl ovládací prvek stát výchozím tlačítkem; jinak nula.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Ovládací prvek musí mít nastaven bit stavu OLEMISC_ACTSLIKEBUTTON. Další informace o příznacích OLEMISC naleznete v tématu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) v Windows SDK.

##  <a name="splitdialogtemplate"></a>COccManager::SplitDialogTemplate

Volá se rozhraním, aby se mohla rozdělit ovládací prvky ActiveX z běžných ovládacích prvků dialogu.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Parametry

*pTemplate*<br/>
Ukazatel na šablonu dialogového okna, který se má prozkoumat.

*ppOleDlgItems*<br/>
Seznam ukazatelů na položky dialogového okna, které jsou ovládacími prvky ActiveX.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu šablony dialogového okna obsahující pouze ovládací prvky, které nejsou ovládacími prvky ActiveX. Pokud nejsou k dispozici žádné ovládací prvky ActiveX, je vrácena hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud se najde nějaké ovládací prvky ActiveX, vytvoří se šablona a vytvoří se nová šablona obsahující jenom ovládací prvky, které nepatří do ActiveX. Do *ppOleDlgItems*byly přidány všechny ovládací prvky ActiveX, které byly nalezeny během tohoto procesu.

Pokud v šabloně nejsou žádné ovládací prvky ActiveX, je vrácena hodnota NULL *.*

> [!NOTE]
>  Paměť přidělená nové šabloně je uvolněna ve `PostCreateDialog` funkci.

Potlačením této funkce přizpůsobíte tento proces.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite – třída](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer – třída](../../mfc/reference/colecontrolcontainer-class.md)
