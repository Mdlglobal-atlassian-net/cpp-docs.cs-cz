---
title: Coccmanager – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cabf1cde43f11997de27b2b2f148482d4f024455
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852364"
---
# <a name="coccmanager-class"></a>Coccmanager – třída
Spravuje různé vlastní ovládací prvky stránky; implementované `COleControlContainer` a `COleControlSite` objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COccManager::CreateContainer](#createcontainer)|Vytvoří `COleContainer` objektu.|  
|[COccManager::CreateDlgControls](#createdlgcontrols)|Vytvoří ovládací prvky ActiveX, hostitelem přidružené `COleContainer` objektu.|  
|[COccManager::CreateSite](#createsite)|Vytvoří `COleClientSite` objektu.|  
|[COccManager::GetDefBtnCode](#getdefbtncode)|Získá kód výchozí tlačítko.|  
|[COccManager::IsDialogMessage](#isdialogmessage)|Určuje cíl zprávy dialogu.|  
|[COccManager::IsLabelControl](#islabelcontrol)|Určuje, zda zadaný ovládací prvek je ovládací prvek popisku.|  
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Určuje, pokud aktuální symbol odpovídá symbolické zadaný ovládací prvek.|  
|[COccManager::OnEvent](#onevent)|Pokusí se zpracovat zadané události.|  
|[COccManager::PostCreateDialog](#postcreatedialog)|Uvolní prostředky přidělené během vytváření dialogového okna.|  
|[COccManager::PreCreateDialog](#precreatedialog)|Zpracuje šablony dialogového okna pro ovládací prvky ActiveX.|  
|[COccManager::SetDefaultButton](#setdefaultbutton)|Přepíná výchozí stav zadaný ovládací prvek.|  
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Všechny existující ovládací prvky ActiveX odděluje z běžných ovládacích prvků v šabloně zadané dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
 Základní třída `CNoTrackObject`, je nedokumentované základní třídy (nachází se ve AFXTLS. H). Je určená pro použití v rámci knihovny MFC rozhraní a třídy odvozené z `CNoTrackObject` třídy jsou vyloučené z detekce nevrácení paměti. Není doporučeno, jsou odvozeny přímo z `CNoTrackObject`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CNoTrackObject`  
  
 `COccManager`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxocc.h  
  
##  <a name="createcontainer"></a>  COccManager::CreateContainer  
 Volá se rozhraním, vytvoření kontejneru ovládacího prvku.  
  
```  
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Ukazatel na objekt okna spojenými s daným kontejnerem vlastní stránky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený kontejner; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o vytváření vlastních webů, najdete v části [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).  
  
##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls  
 Volání této funkce můžete vytvořit ovládací prvky ActiveX, které jsou určené *pOccDialogInfo* parametru.  
  
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
 *pWndParent*  
 Ukazatel na nadřazený prvek z objektu dialogového okna.  
  
 *lpszResourceName*  
 Název prostředku vytvořeného.  
  
 *pOccDialogInfo*  
 Ukazatel na dialogové okno šablony použité k vytvoření objektu dialogového okna.  
  
 *lpResource*  
 Ukazatel na prostředek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud ovládací prvek byl vytvořen úspěšně; jinak nula.  
  
##  <a name="createsite"></a>  COccManager::CreateSite  
 Volá se rozhraním pro vytvoření ovládacího prvku webu hostitelem kontejneru, na které odkazuje *pCtrlCont*.  
  
```  
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parametry  
 *pCtrlCont*  
 Ukazatel na kontejneru ovládacího prvku, který je hostitelem nové lokality ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený ovládací prvek webu.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkce můžete vytvořit vlastní ovládací prvek webu, pomocí vaší [colecontrolsite –](../../mfc/reference/colecontrolsite-class.md)-odvozené třídy.  
  
 Každý kontejner ovládacího prvku může hostovat více webů. Vytvoření dalších lokalit s více volání `CreateSite`.  
  
##  <a name="getdefbtncode"></a>  COccManager::GetDefBtnCode  
 Voláním této funkce k určení, zda je ovládací prvek výchozí příkazové tlačítko.  
  
```  
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Objekt okna obsahující ovládací prvek tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden z následujících hodnot:  
  
- Ovládací prvek DLGC_DEFPUSHBUTTON je výchozí tlačítko v dialogovém okně.  
  
- Ovládací prvek DLGC_UNDEFPUSHBUTTON není výchozí tlačítko v dialogovém okně.  
  
- **0** ovládací prvek není tlačítko.  
  
##  <a name="isdialogmessage"></a>  COccManager::IsDialogMessage  
 Volá se rozhraním, chcete-li zjistit, jestli zpráva je určená pro zadaný dialogových oken a pokud se jedná, zpracuje zprávu.  
  
```  
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndDlg*  
 Ukazatel na dialogovém okně požadovaný cíl zprávy.  
  
 *lpMsg*  
 Ukazatel `MSG` strukturu, která obsahuje zprávy, která se má zkontrolovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud zpráva se zpracuje; jinak nula.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí chování `IsDialogMessage` je chcete zkontrolovat zprávy týkající se klávesnice a převést je na vybrané možnosti pro příslušné dialogové okno. Například klávesu TAB, při stisknutí, vybere další ovládací prvek nebo skupinu ovládacích prvků.  
  
 Přepsání této funkce zajišťují vlastní chování pro zprávy odeslané do zadaného dialogového okna.  
  
##  <a name="islabelcontrol"></a>  COccManager::IsLabelControl  
 Voláním této funkce k určení, zda zadaný ovládací prvek je ovládací prvek popisku.  
  
```  
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);  
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Ukazatel do okna obsahující ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je ovládací prvek popisek; jinak nula  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek popisku je ten, který funguje jako popisek pro jakýkoli ovládací prvek se chystá v řazení.  
  
##  <a name="ismatchingmnemonic"></a>  COccManager::IsMatchingMnemonic  
 Voláním této funkce k určení, pokud aktuální symbol se shoduje s reprezentovaný ovládacím prvkem.  
  
```  
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,  
    LPMSG lpMsg);

 
static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Ukazatel do okna obsahující ovládací prvek.  
  
 *lpMsg*  
 Ukazatel na zprávu obsahující jim tak, aby odpovídaly.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud mnemotechnika odpovídá ovládacího prvku; jinak nula  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onevent"></a>  COccManager::OnEvent  
 Volá se rozhraním pro zpracování zadané události.  
  
```  
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,  
    UINT idCtrl,  
    AFX_EVENT* pEvent,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pCmdTarget*  
 Ukazatel `CCmdTarget` objekt pokus o zpracování událostí  
  
 *idCtrl*  
 ID prostředku ovládacího prvku.  
  
 *pEvent*  
 Zpracovává událost.  
  
 *pHandlerInfo*  
 Pokud není NULL, `OnEvent` vyplní `pTarget` a `pmf` členy `AFX_CMDHANDLERINFO` struktura namísto odesílání příkazu. Tento parametr by měl obvykle mít hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud událost byla zpracována, jinak nula.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkce můžete přizpůsobit výchozí proces zpracování událostí.  
  
##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog  
 Volá se rozhraním před vytvořením skutečných dialogových oken zpracování šablony dialogového okna pro ovládací prvky ActiveX.  
  
```  
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,  
    const DLGTEMPLATE* pOrigTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 *pOccDialogInfo*  
 `_AFX_OCC_DIALOG_INFO` Struktura obsahující informace o šabloně dialogu a všechny ovládací prvky ActiveX, který je hostitelem dialogového okna.  
  
 *pOrigTemplate*  
 Ukazatel na šablony dialogového okna, který se má použít při vytváření dialogových oken.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na strukturu šablony dialogového okna umožňuje vytvořit dialogové okno.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí chování zavolá `SplitDialogTemplate`, určující, pokud jsou všechny ActiveX ovládací prvky k dispozici a vrátí šablony výsledná dialogového okna.  
  
 Přepsání této funkce můžete přizpůsobit proces vytvoření dialogového okna hostování ovládacích prvků ActiveX.  
  
##  <a name="postcreatedialog"></a>  COccManager::PostCreateDialog  
 Volá se rozhraním, které k uvolnění paměti přidělené pro šablony dialogového okna.  
  
```  
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pOccDialogInfo*  
 `_AFX_OCC_DIALOG_INFO` Struktura obsahující informace o šabloně dialogu a všechny ovládací prvky ActiveX, který je hostitelem dialogového okna.  
  
### <a name="remarks"></a>Poznámky  
 Tuto paměť byla přidělena voláním `SplitDialogTemplate`a byla použita pro všechny hostované ovládací prvky ActiveX v dialogovém okně.  
  
 Přepsání této funkce můžete přizpůsobit proces čištění jakýchkoli prostředků používá pole objektu dialogového okna.  
  
##  <a name="setdefaultbutton"></a>  COccManager::SetDefaultButton  
 Voláním této funkce ovládací prvek nastavit jako výchozího tlačítka.  
  
```  
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,  
    BOOL bDefault);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Ukazatel do okna obsahující ovládací prvek.  
  
 *bDefault*  
 Nenulové, pokud ovládací prvek by měl být výchozí tlačítko; jinak nula.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak nula.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Ovládací prvek musí mít OLEMISC_ACTSLIKEBUTTON stav bit sady. Další informace o OLEMISC příznaky, najdete v článku [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) téma v sadě Windows SDK.  
  
##  <a name="splitdialogtemplate"></a>  COccManager::SplitDialogTemplate  
 Volá se rozhraním, aby rozdělit tyto ovládací prvky ActiveX z běžných ovládacích prvků dialogového okna.  
  
```  
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,  
    DLGITEMTEMPLATE** ppOleDlgItems);
```  
  
### <a name="parameters"></a>Parametry  
 *pTemplate*  
 Ukazatel na šabloně dialogu prověřit.  
  
 *ppOleDlgItems*  
 Seznam ukazatelů na prvky dialogového okna, které jsou ovládací prvky ActiveX.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na strukturu šablony dialogového okna obsahující pouze ovládací prvky bez ActiveX. Pokud neexistují žádné ovládací prvky ActiveX, je vrácena hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se nenajdou žádné ovládací prvky ActiveX, šablony se analyzují a novou šablonu, který obsahuje pouze bez – ovládací prvky ActiveX, je vytvořen. Všechny ovládací prvky ActiveX nalezena během tohoto procesu se přidají do *ppOleDlgItems*.  
  
 Pokud v šabloně nejsou žádné ovládací prvky ActiveX, je vrácena hodnota NULL *.*  
  
> [!NOTE]
>  Paměť přidělená pro novou šablonu je uvolněn v `PostCreateDialog` funkce.  
  
 Potlačí tuto funkci k přizpůsobení tohoto procesu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Colecontrolsite – třída](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer – třída](../../mfc/reference/colecontrolcontainer-class.md)
