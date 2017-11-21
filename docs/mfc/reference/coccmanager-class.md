---
title: "Třída COccManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7d27b1d018b427360105f1e294f2d0385ce18f5f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="coccmanager-class"></a>COccManager – třída
Spravuje různých lokalit vlastního ovládacího prvku; implementované `COleControlContainer` a `COleControlSite` objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COccManager::CreateContainer](#createcontainer)|Vytvoří **COleContainer** objektu.|  
|[COccManager::CreateDlgControls](#createdlgcontrols)|Vytvoří ovládací prvky ActiveX, hostované přiřazeným `COleContainer` objektu.|  
|[COccManager::CreateSite](#createsite)|Vytvoří `COleClientSite` objektu.|  
|[COccManager::GetDefBtnCode](#getdefbtncode)|Načte kód výchozí tlačítko.|  
|[COccManager::IsDialogMessage](#isdialogmessage)|Určuje cíl zprávy dialogu.|  
|[COccManager::IsLabelControl](#islabelcontrol)|Určuje, zda je daný ovládací prvek ovládací prvek popisek.|  
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Určuje, jestli aktuální symbolické odpovídá symbolické zadaný ovládacího prvku.|  
|[COccManager::OnEvent](#onevent)|Pokusy o zpracování zadané události.|  
|[COccManager::PostCreateDialog](#postcreatedialog)|Uvolní prostředky přidělené během vytváření dialogové okno.|  
|[COccManager::PreCreateDialog](#precreatedialog)|Zpracuje šablony dialogového okna pro ovládací prvky ActiveX.|  
|[COccManager::SetDefaultButton](#setdefaultbutton)|Přepne stav výchozí daný ovládací prvek.|  
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Všechny existující ovládací prvky ActiveX odděluje z běžných ovládacích prvků v šabloně zadané dialogové okno.|  
  
## <a name="remarks"></a>Poznámky  
 Základní třídy, **CNoTrackObject**, je nedokumentovanými základní třídy (nachází se ve AFXTLS. H). Určený k použití pomocí rozhraní MFC framework, třídy odvozené od **CNoTrackObject** třída vyjmuté z zjišťování nevracení paměti. Není doporučeno jsou odvozeny přímo z **CNoTrackObject**.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CNoTrackObject`  
  
 `COccManager`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxocc.h  
  
##  <a name="createcontainer"></a>COccManager::CreateContainer  
 Voláno rámcem k vytvoření kontejneru ovládacího prvku.  
  
```  
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Ukazatel na objekt okna přidružené kontejneru vlastní stránky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený kontejner; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o vytváření vlastních webů najdete v tématu [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).  
  
##  <a name="createdlgcontrols"></a>COccManager::CreateDlgControls  
 Volání této funkce můžete vytvořit ovládací prvky ActiveX určeného `pOccDialogInfo` parametr.  
  
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
 Ukazatel na nadřazeného objektu dialogového okna.  
  
 `lpszResourceName`  
 Název prostředku vytvořeného.  
  
 `pOccDialogInfo`  
 Ukazatel na šablony dialogového okna použít k vytvoření objektu dialogového okna.  
  
 `lpResource`  
 Ukazatel na prostředek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se úspěšně; vytvořil ovládacího prvku jinak hodnota nula.  
  
##  <a name="createsite"></a>COccManager::CreateSite  
 Voláno rámcem k vytvoření ovládacího prvku lokality hostitelem kontejneru, na kterou odkazuje `pCtrlCont`.  
  
```  
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parametry  
 `pCtrlCont`  
 Ukazatel na kontejneru ovládacího prvku, který je hostitelem nové lokality ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený řízení lokality.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkci můžete vytvořit vlastního ovládacího prvku lokality, pomocí vaší [COleControlSite](../../mfc/reference/colecontrolsite-class.md)-odvozené třídy.  
  
 Každý kontejner řízení může být hostitelem více lokalit. Vytvořte další lokality pomocí několika volání `CreateSite`.  
  
##  <a name="getdefbtncode"></a>COccManager::GetDefBtnCode  
 Volání této funkce můžete určit, zda je ovládací prvek výchozí tlačítko.  
  
```  
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Okno objekt obsahující ovládacího prvku tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících hodnot:  
  
- **DLGC_DEFPUSHBUTTON** ovládací prvek je výchozího tlačítka v dialogovém okně.  
  
- **DLGC_UNDEFPUSHBUTTON** ovládací prvek není výchozího tlačítka v dialogovém okně.  
  
- **0** ovládací prvek není tlačítko.  
  
##  <a name="isdialogmessage"></a>COccManager::IsDialogMessage  
 Voláno rámcem k určení, zda zpráva je určený pro zadaný dialogových oken a pokud se jedná, zprávu zpracuje.  
  
```  
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndDlg*  
 Ukazatel na dialogové okno zamýšleného cílového zprávy.  
  
 `lpMsg`  
 Ukazatel na `MSG` struktura, která obsahuje zpráva, která má být zaškrtnuto.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je zpráva zpracována; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí chování `IsDialogMessage` je kontrola klávesnice zpráv a převést je na výběr odpovídající dialogových oken. Například tabulátor při stisknutí, vybere další ovládací prvek nebo skupinu ovládacích prvků.  
  
 Přepsání této funkce zajistit vlastní chování pro zprávy odeslané do zadaného dialogového okna.  
  
##  <a name="islabelcontrol"></a>COccManager::IsLabelControl  
 Volání této funkce můžete určit, zda je daný ovládací prvek ovládací prvek popisek.  
  
```  
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);  
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Ukazatel na okno obsahuje ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je ovládací prvek popisek; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek popisek je ten, který funguje jako popisek pro libovolnou řízení je další v řazení.  
  
##  <a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic  
 Volání této funkce můžete určit, jestli aktuální symbolické odpovídá která reprezentována ovládacího prvku.  
  
```  
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,  
    LPMSG lpMsg);

 
static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Ukazatel na okno obsahuje ovládací prvek.  
  
 `lpMsg`  
 Ukazatel na zprávu obsahující symbolické tak, aby odpovídaly.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud symbol odpovídá ovládacího prvku; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onevent"></a>COccManager::OnEvent  
 Voláno rámcem pro zpracování zadané události.  
  
```  
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,  
    UINT idCtrl,  
    AFX_EVENT* pEvent,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pCmdTarget*  
 Ukazatel `CCmdTarget` objekt pokus o zpracování události  
  
 `idCtrl`  
 ID prostředku ovládacího prvku.  
  
 `pEvent`  
 Události ke zpracování.  
  
 `pHandlerInfo`  
 Není-li **NULL**, `OnEvent` vyplní **pTarget** a **pmf** členy **AFX_CMDHANDLERINFO** struktury místo odeslání příkazu. Obvykle se tento parametr by měl být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla zpracována událost, jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkci můžete přizpůsobit výchozí proces zpracování událostí.  
  
##  <a name="precreatedialog"></a>COccManager::PreCreateDialog  
 Voláno rámcem při zpracování šablony dialogového okna pro ovládací prvky ActiveX před vytvořením skutečné dialogových oken.  
  
```  
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,  
    const DLGTEMPLATE* pOrigTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 `pOccDialogInfo`  
 **_AFX_OCC_DIALOG_INFO** struktura obsahující informace o šablony dialogového okna a všechny ovládací prvky ActiveX hostované pomocí dialogového okna.  
  
 *pOrigTemplate*  
 Ukazatel na šablony dialogového okna, který se má použít při vytváření dialogových oken.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na strukturu šablony dialogu, který je použit k vytvoření dialogové okno.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí chování zavolá `SplitDialogTemplate`, určení, pokud jsou všechny ActiveX ovládací prvky přítomen a vrátí šablony výsledné dialogového okna.  
  
 Funkci k přizpůsobení procesu vytvoření dialogového okna hostování ovládacích prvků ActiveX přepište.  
  
##  <a name="postcreatedialog"></a>COccManager::PostCreateDialog  
 Voláno rámcem uvolnit paměť přidělená pro šablony dialogového okna.  
  
```  
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `pOccDialogInfo`  
 **_AFX_OCC_DIALOG_INFO** struktura obsahující informace o šablony dialogového okna a všechny ovládací prvky ActiveX hostované pomocí dialogového okna.  
  
### <a name="remarks"></a>Poznámky  
 Tuto paměť byl přidělen voláním `SplitDialogTemplate`a používá se pro všechny hostované ovládací prvky ActiveX v dialogovém okně.  
  
 Přepsání této funkci můžete přizpůsobit proces čištění všechny prostředky používané pole objektu dialogového okna.  
  
##  <a name="setdefaultbutton"></a>COccManager::SetDefaultButton  
 Volání této funkce pro nastavení ovládacího prvku jako výchozího tlačítka.  
  
```  
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,  
    BOOL bDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Ukazatel na okno obsahuje ovládací prvek.  
  
 `bDefault`  
 Nenulové hodnoty, pokud se ovládací prvek by měl stane výchozí tlačítko; jinak hodnota nula.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Ovládací prvek musí mít **OLEMISC_ACTSLIKEBUTTON** stav nastaven bit. Další informace o **OLEMISC** příznaky, viz [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) v sadě Windows SDK.  
  
##  <a name="splitdialogtemplate"></a>COccManager::SplitDialogTemplate  
 Voláno rámcem rozdělit ovládacích prvků ActiveX z běžné ovládací prvky dialogového okna.  
  
```  
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,  
    DLGITEMTEMPLATE** ppOleDlgItems);
```  
  
### <a name="parameters"></a>Parametry  
 `pTemplate`  
 Ukazatel na šablony dialogového okna prověřit.  
  
 `ppOleDlgItems`  
 Seznam ukazatele k položkám pole dialogové okno, které jsou ovládací prvky ActiveX.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na strukturu šablony dialogové okno obsahující pouze není ActiveX – ovládací prvky. Pokud nejsou žádné ovládací prvky ActiveX **NULL** je vrácen.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou všechny ovládací prvky ActiveX, šablona se analyzují a vytvořit novou šablonu, obsahující pouze bez – ovládací prvky ActiveX. Ovládací prvky ActiveX nalezena během tohoto procesu se přidají do `ppOleDlgItems`.  
  
 Pokud nejsou žádné ovládací prvky ActiveX v šabloně, **NULL** je vrácen *.*  
  
> [!NOTE]
>  Paměť přidělená pro novou šablonu uvolněno v `PostCreateDialog` funkce.  
  
 Potlačí tuto funkci k přizpůsobení tohoto procesu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleControlSite – třída](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer – třída](../../mfc/reference/colecontrolcontainer-class.md)
