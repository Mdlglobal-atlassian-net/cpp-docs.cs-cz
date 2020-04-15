---
title: Třída COccManager
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
ms.openlocfilehash: 5637a4709e90bb14caff3fe4e396487e62e213e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360354"
---
# <a name="coccmanager-class"></a>Třída COccManager

Spravuje různé weby vlastních ovládacích prvku. a `COleControlSite` `COleControlContainer` objekty.

## <a name="syntax"></a>Syntaxe

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COccManager::CreateContainer](#createcontainer)|Vytvoří `COleContainer` objekt.|
|[COccManager::CreateDlgControls](#createdlgcontrols)|Vytvoří ovládací prvky ActiveX `COleContainer` hostované přidruženým objektem.|
|[COccManager::Vytvořit web](#createsite)|Vytvoří `COleClientSite` objekt.|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Načte kód výchozího tlačítka.|
|[COccManager::IsDialogMessage](#isdialogmessage)|Určuje cíl zprávy dialogového okna.|
|[COccManager::Ovládací prvek IsLabelControl](#islabelcontrol)|Určuje, zda je zadaný ovládací prvek ovládací prvek popisek.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Určuje, zda aktuální mnemotechnická pomůcka odpovídá mnemotechnické pomůcky zadaného ovládacího prvku.|
|[COccManager::OnEvent](#onevent)|Pokusí se zpracovat zadanou událost.|
|[COccManager::PostCreateDialog](#postcreatedialog)|Uvolní prostředky přidělené během vytváření dialogu.|
|[COccManager::PreCreateDialog](#precreatedialog)|Zpracuje šablonu dialogu pro ovládací prvky ActiveX.|
|[COccManager::SetDefaultButton](#setdefaultbutton)|Přepíná výchozí stav zadaného ovládacího prvku.|
|[COccManager::Šablona splitdialogu](#splitdialogtemplate)|Oddělí všechny existující ovládací prvky ActiveX od běžných ovládacích prvků v zadané šabloně dialogového okna.|

## <a name="remarks"></a>Poznámky

Základní třída `CNoTrackObject`, je základní třída bez dokladů (umístěná v AFXTLS. H). Třídy odvozené z `CNoTrackObject` této třídy jsou určeny pro použití rozhraním MFC a jsou osvobozeny od zjišťování nevracení paměti. Nedoporučuje se odvodit `CNoTrackObject`přímo z aplikace .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxocc.h

## <a name="coccmanagercreatecontainer"></a><a name="createcontainer"></a>COccManager::CreateContainer

Volat rámci k vytvoření kontejneru ovládacího prvku.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na objekt okna přidružený k vlastnímu kontejneru webu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený kontejner; jinak NULL.

### <a name="remarks"></a>Poznámky

Další informace o vytváření vlastních webů naleznete v [tématu COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

## <a name="coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a>COccManager::CreateDlgControls

Voláním této funkce vytvořte ovládací prvky ActiveX určené parametrem *pOccDialogInfo.*

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
Ukazatel na šablonu dialogu použitou k vytvoření objektu dialogu.

*lpZdroj*<br/>
Ukazatel na prostředek.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl ovládací prvek úspěšně vytvořen; jinak nula.

## <a name="coccmanagercreatesite"></a><a name="createsite"></a>COccManager::Vytvořit web

Volat rámci k vytvoření řídicí lokality, hostované kontejneru ukázal *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parametry

*pCtrlCont*<br/>
Ukazatel na kontejner ovládacího prvku, který je hostitelem nového webu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořenou řídicí lokalitu.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci vytvořit vlastní lokalitu ovládacího prvku, pomocí [COleControlSite](../../mfc/reference/colecontrolsite-class.md)-odvozené třídy.

Každý kontejner ovládacího prvku může hostovat více sítí. Vytvořte další weby `CreateSite`s více voláními .

## <a name="coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a>COccManager::GetDefBtnCode

Volání této funkce k určení, zda je ovládací prvek výchozí tlačítko.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Objekt okna obsahující ovládací prvek tlačítka.

### <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot:

- DLGC_DEFPUSHBUTTON Control je výchozí tlačítko v dialogovém okně.

- DLGC_UNDEFPUSHBUTTON Control není v dialogovém okně výchozím tlačítkem.

- **0** Ovládání není tlačítko.

## <a name="coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a>COccManager::IsDialogMessage

Volat rámci k určení, zda je zpráva určena pro zadané dialogové okno a pokud je, zpracovává zprávu.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*pWndDlg*<br/>
Ukazatel na zamýšlené cílové dialogové okno zprávy.

*lpMsg*<br/>
Ukazatel na `MSG` strukturu, která obsahuje zprávu, která má být kontrolována.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zpráva zpracována; jinak nula.

### <a name="remarks"></a>Poznámky

Výchozí chování `IsDialogMessage` je zkontrolovat zprávy klávesnice a převést je do výběrů pro odpovídající dialogové okno. Například klávesa TAB při stisknutí vybere další ovládací prvek nebo skupinu ovládacích prvků.

Přepište tuto funkci a zajistěte vlastní chování pro zprávy odeslané do zadaného dialogového okna.

## <a name="coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a>COccManager::Ovládací prvek IsLabelControl

Volání této funkce k určení, zda zadaný ovládací prvek je ovládací prvek popisek.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno obsahující ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je ovládací prvek popisek; jinak nula

### <a name="remarks"></a>Poznámky

Ovládací prvek popisek je ten, který funguje jako popisek pro jakýkoli ovládací prvek je další v pořadí.

## <a name="coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic

Volání této funkce k určení, pokud aktuální mnemotechnické pomůcky odpovídá, které představují ovládací prvek.

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
Ukazatel na zprávu obsahující mnemotechnické pomůcky tak, aby odpovídaly.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud mnemotechnická pomůcká pomůcká pomůcká pomůcká pomůcká pomůcká pomůcká jinak nula

### <a name="remarks"></a>Poznámky

## <a name="coccmanageronevent"></a><a name="onevent"></a>COccManager::OnEvent

Volat rámci pro zpracování zadané události.

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
ID prostředku ovládacího prvku.

*pUdálost*<br/>
Událost je zpracovávána.

*pHandlerInfo*<br/>
Pokud ne `OnEvent` NULL, vyplní `pTarget` a `pmf` členy struktury namísto `AFX_CMDHANDLERINFO` odeslání příkazu. Tento parametr by měl být obvykle null.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla událost zpracována, jinak nula.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci a přizpůsobte výchozí proces zpracování událostí.

## <a name="coccmanagerprecreatedialog"></a><a name="precreatedialog"></a>COccManager::PreCreateDialog

Nazývá rámci ke zpracování šablonu dialogu pro ovládací prvky ActiveX před vytvořením skutečné dialogové okno.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
Struktura `_AFX_OCC_DIALOG_INFO` obsahující informace o šabloně dialogového okna a všechny ovládací prvky ActiveX hostované dialogem.

*pOrigŠablona*<br/>
Ukazatel na šablonu dialogu, která má být použita při vytváření dialogového okna.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu šablony dialogu použitý k vytvoření dialogového okna.

### <a name="remarks"></a>Poznámky

Výchozí chování provede volání `SplitDialogTemplate`, určení, zda existují nějaké ovládací prvky ActiveX a potom vrátí výslednou šablonu dialogového okna.

Přepsáním této funkce přizpůsobte proces vytváření dialogového okna hostujícího ovládací prvky ActiveX.

## <a name="coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a>COccManager::PostCreateDialog

Volat rámci uvolnit paměť přidělenou pro šablonu dialogu.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
Struktura `_AFX_OCC_DIALOG_INFO` obsahující informace o šabloně dialogového okna a všechny ovládací prvky ActiveX hostované dialogem.

### <a name="remarks"></a>Poznámky

Tato paměť byla přidělena `SplitDialogTemplate`voláním aplikace a byla použita pro všechny hostované ovládací prvky ActiveX v dialogovém okně.

Přepsáním této funkce přizpůsobte proces čištění všech prostředků používaných objektem dialogového okna.

## <a name="coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a>COccManager::SetDefaultButton

Voláním této funkce nastavte ovládací prvek jako výchozí tlačítko.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno obsahující ovládací prvek.

*bVýchozí*<br/>
Nenulová, pokud by se ovládací prvek měl stát výchozím tlačítkem; jinak nula.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Ovládací prvek musí mít nastaven OLEMISC_ACTSLIKEBUTTON stavový bit. Další informace o ovlažení OLEMISC naleznete v tématu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) v sadě Windows SDK.

## <a name="coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a>COccManager::Šablona splitdialogu

Volat rámci rozdělit ovládací prvky ActiveX z běžných ovládacích prvků dialogového okna.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Parametry

*pŠablona*<br/>
Ukazatel na šablonu dialogu, která má být zkontrolována.

*ppOleDlgItems*<br/>
Seznam ukazatelů na položky dialogového okna, které jsou ovládacími prvky ActiveX.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu šablony dialogu obsahující pouze ovládací prvky, které nejsou ovládací prvky ActiveX. Pokud nejsou k dispozici žádné ovládací prvky ActiveX, je vrácena hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud jsou nalezeny některé ovládací prvky ActiveX, je šablona analyzována a vytvoří se nová šablona obsahující pouze ovládací prvky, které nejsou ovládací prvky ActiveX. Všechny ovládací prvky ActiveX nalezené během tohoto procesu jsou přidány do *položky ppOleDlgItems*.

Pokud v šabloně nejsou žádné ovládací prvky ActiveX, je vrácena hodnota NULL *.*

> [!NOTE]
> Paměť přidělená pro novou šablonu `PostCreateDialog` je uvolněna ve funkci.

Přepište tuto funkci a přizpůsobte tento proces.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite – třída](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer – třída](../../mfc/reference/colecontrolcontainer-class.md)
