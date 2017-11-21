---
title: "Třída CFileDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileDialog
- AFXDLGS/CFileDialog
- AFXDLGS/CFileDialog::CFileDialog
- AFXDLGS/CFileDialog::AddCheckButton
- AFXDLGS/CFileDialog::AddComboBox
- AFXDLGS/CFileDialog::AddControlItem
- AFXDLGS/CFileDialog::AddEditBox
- AFXDLGS/CFileDialog::AddMenu
- AFXDLGS/CFileDialog::AddPlace
- AFXDLGS/CFileDialog::AddPushButton
- AFXDLGS/CFileDialog::AddRadioButtonList
- AFXDLGS/CFileDialog::AddSeparator
- AFXDLGS/CFileDialog::AddText
- AFXDLGS/CFileDialog::ApplyOFNToShellDialog
- AFXDLGS/CFileDialog::DoModal
- AFXDLGS/CFileDialog::EnableOpenDropDown
- AFXDLGS/CFileDialog::EndVisualGroup
- AFXDLGS/CFileDialog::GetCheckButtonState
- AFXDLGS/CFileDialog::GetControlItemState
- AFXDLGS/CFileDialog::GetControlState
- AFXDLGS/CFileDialog::GetEditBoxText
- AFXDLGS/CFileDialog::GetFileExt
- AFXDLGS/CFileDialog::GetFileName
- AFXDLGS/CFileDialog::GetFileTitle
- AFXDLGS/CFileDialog::GetFolderPath
- AFXDLGS/CFileDialog::GetIFileDialogCustomize
- AFXDLGS/CFileDialog::GetIFileOpenDialog
- AFXDLGS/CFileDialog::GetIFileSaveDialog
- AFXDLGS/CFileDialog::GetNextPathName
- AFXDLGS/CFileDialog::GetOFN
- AFXDLGS/CFileDialog::GetPathName
- AFXDLGS/CFileDialog::GetReadOnlyPref
- AFXDLGS/CFileDialog::GetResult
- AFXDLGS/CFileDialog::GetResults
- AFXDLGS/CFileDialog::GetSelectedControlItem
- AFXDLGS/CFileDialog::GetStartPosition
- AFXDLGS/CFileDialog::HideControl
- AFXDLGS/CFileDialog::IsPickFoldersMode
- AFXDLGS/CFileDialog::MakeProminent
- AFXDLGS/CFileDialog::RemoveControlItem
- AFXDLGS/CFileDialog::SetCheckButtonState
- AFXDLGS/CFileDialog::SetControlItemState
- AFXDLGS/CFileDialog::SetControlItemText
- AFXDLGS/CFileDialog::SetControlLabel
- AFXDLGS/CFileDialog::SetControlState
- AFXDLGS/CFileDialog::SetControlText
- AFXDLGS/CFileDialog::SetDefExt
- AFXDLGS/CFileDialog::SetEditBoxText
- AFXDLGS/CFileDialog::SetProperties
- AFXDLGS/CFileDialog::SetSelectedControlItem
- AFXDLGS/CFileDialog::SetTemplate
- AFXDLGS/CFileDialog::StartVisualGroup
- AFXDLGS/CFileDialog::UpdateOFNFromShellDialog
- AFXDLGS/CFileDialog::OnButtonClicked
- AFXDLGS/CFileDialog::OnCheckButtonToggled
- AFXDLGS/CFileDialog::OnControlActivating
- AFXDLGS/CFileDialog::OnFileNameChange
- AFXDLGS/CFileDialog::OnFileNameOK
- AFXDLGS/CFileDialog::OnFolderChange
- AFXDLGS/CFileDialog::OnInitDone
- AFXDLGS/CFileDialog::OnItemSelected
- AFXDLGS/CFileDialog::OnLBSelChangedNotify
- AFXDLGS/CFileDialog::OnShareViolation
- AFXDLGS/CFileDialog::OnTypeChange
- AFXDLGS/CFileDialog::m_ofn
dev_langs: C++
helpviewer_keywords:
- CFileDialog [MFC], CFileDialog
- CFileDialog [MFC], AddCheckButton
- CFileDialog [MFC], AddComboBox
- CFileDialog [MFC], AddControlItem
- CFileDialog [MFC], AddEditBox
- CFileDialog [MFC], AddMenu
- CFileDialog [MFC], AddPlace
- CFileDialog [MFC], AddPushButton
- CFileDialog [MFC], AddRadioButtonList
- CFileDialog [MFC], AddSeparator
- CFileDialog [MFC], AddText
- CFileDialog [MFC], ApplyOFNToShellDialog
- CFileDialog [MFC], DoModal
- CFileDialog [MFC], EnableOpenDropDown
- CFileDialog [MFC], EndVisualGroup
- CFileDialog [MFC], GetCheckButtonState
- CFileDialog [MFC], GetControlItemState
- CFileDialog [MFC], GetControlState
- CFileDialog [MFC], GetEditBoxText
- CFileDialog [MFC], GetFileExt
- CFileDialog [MFC], GetFileName
- CFileDialog [MFC], GetFileTitle
- CFileDialog [MFC], GetFolderPath
- CFileDialog [MFC], GetIFileDialogCustomize
- CFileDialog [MFC], GetIFileOpenDialog
- CFileDialog [MFC], GetIFileSaveDialog
- CFileDialog [MFC], GetNextPathName
- CFileDialog [MFC], GetOFN
- CFileDialog [MFC], GetPathName
- CFileDialog [MFC], GetReadOnlyPref
- CFileDialog [MFC], GetResult
- CFileDialog [MFC], GetResults
- CFileDialog [MFC], GetSelectedControlItem
- CFileDialog [MFC], GetStartPosition
- CFileDialog [MFC], HideControl
- CFileDialog [MFC], IsPickFoldersMode
- CFileDialog [MFC], MakeProminent
- CFileDialog [MFC], RemoveControlItem
- CFileDialog [MFC], SetCheckButtonState
- CFileDialog [MFC], SetControlItemState
- CFileDialog [MFC], SetControlItemText
- CFileDialog [MFC], SetControlLabel
- CFileDialog [MFC], SetControlState
- CFileDialog [MFC], SetControlText
- CFileDialog [MFC], SetDefExt
- CFileDialog [MFC], SetEditBoxText
- CFileDialog [MFC], SetProperties
- CFileDialog [MFC], SetSelectedControlItem
- CFileDialog [MFC], SetTemplate
- CFileDialog [MFC], StartVisualGroup
- CFileDialog [MFC], UpdateOFNFromShellDialog
- CFileDialog [MFC], OnButtonClicked
- CFileDialog [MFC], OnCheckButtonToggled
- CFileDialog [MFC], OnControlActivating
- CFileDialog [MFC], OnFileNameChange
- CFileDialog [MFC], OnFileNameOK
- CFileDialog [MFC], OnFolderChange
- CFileDialog [MFC], OnInitDone
- CFileDialog [MFC], OnItemSelected
- CFileDialog [MFC], OnLBSelChangedNotify
- CFileDialog [MFC], OnShareViolation
- CFileDialog [MFC], OnTypeChange
- CFileDialog [MFC], m_ofn
ms.assetid: fda4fd3c-08b8-4ce0-8e9d-7bab23f8c6c0
caps.latest.revision: "47"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2dead08eaeb525e626e9c1f02af346b0c3998260
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cfiledialog-class"></a>CFileDialog – třída
Zapouzdří běžné dialogových oken, který se používá pro otevření souboru nebo soubor uložte operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFileDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileDialog::CFileDialog](#cfiledialog)|Vytvoří `CFileDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileDialog::AddCheckButton](#addcheckbutton)|Přidá tlačítko zaškrtnutí na dialogové okno.|  
|[CFileDialog::AddComboBox](#addcombobox)|Přidá pole se seznamem do dialogu.|  
|[CFileDialog::AddControlItem](#addcontrolitem)|Přidá položku do kontejneru ovládacího prvku v dialogovém okně.|  
|[CFileDialog::AddEditBox](#addeditbox)|Přidá do dialogu textové pole.|  
|[CFileDialog::AddMenu](#addmenu)|Dialogové okno umožňuje přidat nabídku.|  
|[CFileDialog::AddPlace](#addplace)|Přetíženo. Přidá že umístí do složky, do seznamu k dispozici pro uživatele k otevření nebo uložení položky.|  
|[CFileDialog::AddPushButton](#addpushbutton)|Přidá tlačítko do dialogového okna.|  
|[CFileDialog::AddRadioButtonList](#addradiobuttonlist)|Přidá skupiny přepínačů (také označované jako přepínač) do dialogu.|  
|[CFileDialog::AddSeparator](#addseparator)|Přidá oddělovač do dialogového okna.|  
|[CFileDialog::AddText](#addtext)|Přidá do dialogu textového obsahu.|  
|[CFileDialog::ApplyOFNToShellDialog](#applyofntoshelldialog)|Aktualizace stavu `CFileDialog` tak, aby odpovídaly parametry a příznaky, které jsou uložené v `m_ofn` členské proměnné.|  
|[CFileDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožní uživateli můžete vybrat.|  
|[CFileDialog::EnableOpenDropDown](#enableopendropdown)|Umožňuje v rozevíracím seznamu **otevřete** nebo **Uložit** tlačítka v dialogovém okně.|  
|[CFileDialog::EndVisualGroup](#endvisualgroup)|Zastaví Přidání elementů do visual skupiny v dialogovém okně.|  
|[CFileDialog::GetCheckButtonState](#getcheckbuttonstate)|Získá aktuální stav kontroly tlačítko (zaškrtávací políčko) v dialogovém okně.|  
|[CFileDialog::GetControlItemState](#getcontrolitemstate)|Získá aktuální stav položky v ovládacím prvku kontejneru najít v dialogovém okně.|  
|[CFileDialog::GetControlState](#getcontrolstate)|Získá aktuální viditelnost a jejich stavů daný ovládací prvek.|  
|[CFileDialog::GetEditBoxText](#geteditboxtext)|Získá aktuální text v ovládacím prvku upravit.|  
|[CFileDialog::GetFileExt](#getfileext)|Vrátí klapku vybraného souboru.|  
|[CFileDialog::GetFileName](#getfilename)|Vrátí název souboru vybraného souboru.|  
|[CFileDialog::GetFileTitle](#getfiletitle)|Vrátí název vybraného souboru.|  
|[CFileDialog::GetFolderPath](#getfolderpath)|Načte cestu aktuálně otevřít složku nebo adresář pro styl Průzkumníku **otevřete** nebo **uložit jako** běžné dialogové okno.|  
|[CFileDialog::GetIFileDialogCustomize](#getifiledialogcustomize)|Načte vnitřní objekt COM pro přizpůsobený `CFileDialog` objektu.|  
|[CFileDialog::GetIFileOpenDialog](#getifileopendialog)|Načte vnitřní objekt COM pro `CFileDialog` používané jako **otevřete** dialogové okno souborů.|  
|[CFileDialog::GetIFileSaveDialog](#getifilesavedialog)|Načte vnitřní objekt COM pro `CFileDialog` používané jako **Uložit** dialogové okno souborů.|  
|[CFileDialog::GetNextPathName](#getnextpathname)|Vrací úplnou cestu k další vybraného souboru.|  
|[CFileDialog::GetOFN](#getofn)|Načte `OPENFILENAME` struktura `CFileDialog` objektu.|  
|[CFileDialog::GetPathName](#getpathname)|Vrátí úplnou cestu vybraného souboru.|  
|[CFileDialog::GetReadOnlyPref](#getreadonlypref)|Vrátí stav jen pro čtení vybraného souboru.|  
|[CFileDialog::GetResult](#getresult)|Získá volbou, která uživatel provedené v dialogovém okně.|  
|[CFileDialog::GetResults](#getresults)|Získá volby uživatele v dialogovém okně, které umožňuje vícenásobný výběr.|  
|[CFileDialog::GetSelectedControlItem](#getselectedcontrolitem)|Získá konkrétní položku z zadaného kontejneru ovládacích prvků v dialogovém okně.|  
|[CFileDialog::GetStartPosition](#getstartposition)|Vrátí pozici první prvek seznamu souborů.|  
|[CFileDialog::HideControl](#hidecontrol)|Skryje daný ovládací prvek ve stylu Průzkumníku **otevřete** nebo **uložit jako** běžné dialogové okno.|  
|[CFileDialog::IsPickFoldersMode](#ispickfoldersmode)|Určuje, zda aktuální dialogové okno v režimu výběr složky.|  
|[CFileDialog::MakeProminent](#makeprominent)|Místech ovládacího prvku v dialogovém okně tak, aby vystupoval ve srovnání s další přidané ovládací prvky.|  
|[CFileDialog::RemoveControlItem](#removecontrolitem)|Odebere položku z kontejneru ovládacího prvku v dialogovém okně.|  
|[CFileDialog::SetCheckButtonState](#setcheckbuttonstate)|V dialogovém okně nastaví aktuální stav kontroly tlačítka (zaškrtávací políčko).|  
|[CFileDialog::SetControlItemState](#setcontrolitemstate)|Nastaví aktuální stav položky v ovládacím prvku kontejneru najít v dialogovém okně.|  
|[CFileDialog::SetControlItemText](#setcontrolitemtext)|Nastaví text položky ovládacího prvku. Například text, který doprovází přepínače nebo položku v nabídce.|  
|[CFileDialog::SetControlLabel](#setcontrollabel)|Nastaví text související s ovládacím prvkem, jako je text tlačítka nebo popisek pole upravit.|  
|[CFileDialog::SetControlState](#setcontrolstate)|Nastaví aktuální viditelnost a jejich stavů daný ovládací prvek.|  
|[CFileDialog::SetControlText](#setcontroltext)|Nastaví text pro daný ovládací prvek ve stylu Průzkumníku **otevřete** nebo **uložit jako** běžné dialogové okno.|  
|[CFileDialog::SetDefExt](#setdefext)|Nastaví výchozí příponu názvu souboru pro styl Průzkumníku **otevřete** nebo **uložit jako** běžné dialogové okno.|  
|[CFileDialog::SetEditBoxText](#seteditboxtext)|Nastaví aktuální text v ovládacím prvku upravit.|  
|[CFileDialog::SetProperties](#setproperties)|Poskytuje úložiště vlastností, která definuje výchozí hodnoty, který se má použít pro položku ukládají.|  
|[CFileDialog::SetSelectedControlItem](#setselectedcontrolitem)|Nastaví vybraný stav konkrétní položky skupiny přepínačů nebo v poli se seznamem najít v dialogovém okně.|  
|[CFileDialog::SetTemplate](#settemplate)|Nastaví pole šablony dialogového okna pro `CFileDialog` objektu.|  
|[CFileDialog::StartVisualGroup](#startvisualgroup)|Deklaruje visual skupiny v dialogovém okně. Do této skupiny přidat následující volání do kterékoli metody "Přidat" těchto elementů.|  
|[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)|Aktualizace dat uložených v `m_ofn` členské proměnné tak, aby odpovídala aktuální stav dialogového okna souboru.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileDialog::OnButtonClicked](#onbuttonclicked)|Volá se při kliknutí na tlačítko.|  
|[CFileDialog::OnCheckButtonToggled](#oncheckbuttontoggled)|Volá se při zaškrtávací políčko je zaškrtnuté nebo nezaškrtnuté.|  
|[CFileDialog::OnControlActivating](#oncontrolactivating)|Voláno, pokud se ovládací prvek aktivní.|  
|[CFileDialog::OnFileNameChange](#onfilenamechange)|Zpracovává `WM_NOTIFY CDN_SELCHANGE` zprávy.|  
|[CFileDialog::OnFileNameOK](#onfilenameok)|Ověří zadaný v dialogovém okně název souboru.|  
|[CFileDialog::OnFolderChange](#onfolderchange)|Zpracovává `WM_NOTIFY CDN_FOLDERCHANGE` zprávy.|  
|[CFileDialog::OnInitDone](#oninitdone)|Zpracovává `WM_NOTIFY CDN_INITDONE` zprávy.|  
|[CFileDialog::OnItemSelected](#onitemselected)|Voláno, pokud je vybrána položka kontejneru.|  
|[CFileDialog::OnLBSelChangedNotify](#onlbselchangednotify)|Umožňuje provést vlastní akci, když se změní výběr souboru.|  
|[CFileDialog::OnShareViolation](#onshareviolation)|Obslužné rutiny sdílet porušení.|  
|[CFileDialog::OnTypeChange](#ontypechange)|Zpracovává `WM_NOTIFY CDN_TYPECHANGE` zprávy.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileDialog::m_ofn](#m_ofn)|Windows `OPENFILENAME` struktura. Poskytuje přístup k základní soubor dialogové okno pole parametrů.|  
  
## <a name="remarks"></a>Poznámky  
 Společná dialogová okna soubor umožňují implementovat výběr souborů dialogových oken, například **otevření souboru** a **uložit jako**, způsobem, který je v souladu s Windows standardů.  
  
 Můžete použít `CFileDialog` tak, jak jsou s konstruktorem zadaná nebo odvozujete vlastní třídy dialogového okna z `CFileDialog` a zápis konstruktoru tak, aby vyhovovala vašim potřebám. V obou případech tyto dialogy budou chovat jako standardní dialogová okna MFC vzhledem k tomu, že jsou odvozeny od [CCommonDialog třída](../../mfc/reference/ccommondialog-class.md). `CFileDialog`spoléhá na COMMDLG. Soubor knihovny DLL, která je součástí systému Windows.  
  
 Vzhled a funkce `CFileDialog` s [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] se liší od předchozích verzích systému Windows. Výchozí hodnota `CFileDialog` automaticky použije nové [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] styl bez změn kódu, pokud je program kompilován a pro běh [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Použití `bVistaStyle` parametr v konstruktoru ručně přepsat tuto automatických aktualizací. Výjimkou automatických aktualizací je přizpůsobené dialogová okna. Nebude převeden do nového stylu. Další informace o konstruktoru najdete v tématu [CFileDialog::CFileDialog](#cfiledialog).  
  
> [!NOTE]
>  ID systému správy se liší v [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] z dřívějších verzích systému Windows, když používáte `CFileDialog`. Je nutné aktualizovat všechny odkazy na `CFileDialog` ovládací prvky v kódu předtím, než můžete portu projektu ze starší verze systému Windows.  
  
 Některé `CFileDialog` metody nejsou podporovány v rámci [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Zkontrolujte jednotlivé metoda tématu informace o tom, zda je metoda podporována. Kromě toho nejsou podporovány následující funkce zděděné pod [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
- [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)  
  
- [CDialog::OnSetFont](../../mfc/reference/cdialog-class.md#onsetfont)  
  
 Zprávy windows pro `CFileDialog` třída lišit v závislosti na jaké operačního systému, kterou používáte. Například Windows XP nepodporuje [CDialog::OnCancel](../../mfc/reference/cdialog-class.md#oncancel) a [CDialog::OnOK](../../mfc/reference/cdialog-class.md#onok) pro `CFileDialog` třídy. Ale [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] je podporují. Další informace o různých zprávy, které jsou generovány a pořadí, ve kterém jsou přijaty najdete v tématu [CFileDialog ukázka: protokolování – pořadí událostí](../../visual-cpp-samples.md).  
  
 Použít `CFileDialog` objektu, nejprve vytvořit objekt pomocí `CFileDialog` konstruktor. Po dialogové okno byl vytvořený, můžete nastavit nebo změnit všechny hodnoty v [CFileDialog::m_ofn](#m_ofn) struktura k chybě při inicializaci hodnoty nebo stavy, které ovládacím prvkům v dialogovém okně. `m_ofn` Struktura je typu `OPENFILENAME`. Další informace najdete v tématu [název otevřeného souboru](http://msdn.microsoft.com/library/windows/desktop/ms646839) struktura ve Windows SDK.  
  
 Po inicializaci ovládacím prvkům v dialogovém okně volat [CFileDialog::DoModal](#domodal) metodu pro zobrazení dialogu pole tak, aby uživatel můžete zadat název a cesta k souboru. `DoModal`Vrátí, zda uživatel kliknutí na OK (IDOK) nebo na tlačítko Zrušit (IDCANCEL). Pokud `DoModal` vrátí IDOK, můžete použít jednu z `CFileDialog` veřejné členské funkce načíst informace o chápat uživatelem.  
  
> [!NOTE]
>  V části [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], více volá, aby se [IFileDialog::SetFileTypes](http://msdn.microsoft.com/library/windows/desktop/bb775980) dojde k chybě. Druhé volání `SetFileTypes` pro všechny instance `CFileDialog` vrátí `E_UNEXPECTED` v [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Některé `CFileDialog` metoda funkce volání `SetFileTypes`. Například dvě volání `CFileDialog::DoModal` pro stejnou instanci `CFileDialog` generuje [ASSERT](diagnostic-services.md#assert).  
  
 `CFileDialog`zahrnuje několik chráněné členy, které vám umožní provádět vlastní zpracování sdílené složky narušení, ověření názvu souboru a oznámení o změně pole se seznamem. Funkce zpětného volání, které většinu aplikací není nutné použít, protože výchozí zpracování je automatické jsou chráněné členy. Mapy zpráv položky pro tyto funkce nejsou vyžadovány, protože jsou to standardní virtuální funkce.  
  
 Můžete použít Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkce k určení, zda došlo k chybě během inicializace dialogových oken a další informace o této chybě.  
  
 Zničení `CFileDialog` automaticky zpracovává objekty. Není nutné volat [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog).  
  
 Chcete-li umožnit uživateli vybrat více souborů, nastavte `OFN_ALLOWMULTISELECT` příznak před voláním `DoModal`. Je třeba zadat vlastní vyrovnávací paměť názvu souboru pro uložení seznamu vrácených více názvů souborů. To udělat tak, že nahradíte `m_ofn.lpstrFile` pomocí ukazatele do vyrovnávací paměti jste přidělili, co vytvoříte `CFileDialog`, ale před voláním `DoModal`.  
  
 Kromě toho je nutné nastavit `m_ofn.nMaxFile` pomocí počet znaků ve vyrovnávací paměti, na kterou odkazuje `m_ofn.lpstrFile`. Pokud nastavíte maximální počet souborů, aby byl vybrán k `n`, požadované vyrovnávací paměť je `n * (_MAX_PATH + 1) + 1`. První položka vrátila ve vyrovnávací paměti je cesta ke složce, kde byly vybrané soubory. Pro [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]– styl dialogových oken, řetězec názvu adresáře a souboru jsou ukončené hodnotou null znakem navíc null po poslední název souboru. Tento formát umožňuje dialogových oken stylu Průzkumníku vrátit dlouhé názvy souborů s mezerami. Pro starého dialogových oken řetězec názvu adresáře a souboru se oddělují mezerami a funkce, která používá krátké názvy souborů pro názvy souborů s prostory.  
  
 Následující příklad ukazuje, jak používat vyrovnávací paměť k načtení a seznamu více názvů souborů.  
  
 [!code-cpp[NVC_MFCFiles#23](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_1.cpp)]  
  
 Chcete-li změnit velikost vyrovnávací paměti v reakci na uživatele vyberte více názvů souborů, musí být odvozeny novou třídu z `CFileDialog` a přepsat [CFileDialog::OnFileNameChange](#onfilenamechange) metoda.  
  
 Pokud odvozujete novou třídu z `CFileDialog`, můžete použít mapy zpráv zpracovat všechny zprávy. Rozšíření zpracování zpráv výchozí, odvození třídy z `CFileDialog`, přidejte mapy zpráv do nové třídy a zadejte členské funkce pro nové zprávy. Nemáte poskytují funkce háku přizpůsobit dialogové okno.  
  
 Chcete-li přizpůsobit dialogové okno, odvození třídy z `CFileDialog`, zadejte šablonu dialogové okno Vlastní pole a přidat mapy zpráv pro zpracování zprávy s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy předejte základní třídy. Chcete-li přizpůsobit funkce háku nemáte.  
  
 Při použití [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] styl `CFileDialog`, nemůžete použít mapy zpráv a dialogové okno pole šablon. Místo toho musíte použít rozhraní modelu COM pro podobné funkce.  
  
 Další informace o tom, jak používat `CFileDialog`, najdete v části [třídy společných dialogů](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFileDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="addcheckbutton"></a>CFileDialog::AddCheckButton  
 Přidá tlačítko zaškrtnutí na dialogové okno.  
  
```  
HRESULT AddCheckButton(
    DWORD dwIDCtl,  
    const CString& strLabel,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID zaškrtněte tlačítko Přidat.  
  
 `strLabel`  
 Název tlačítka kontroly.  
  
 `bChecked`  
 Logickou hodnotu udávající, aktuální stav na tlačítko se zaškrtnutím. `TRUE`Pokud zaškrtnutí; `FALSE` jinak  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addcombobox"></a>CFileDialog::AddComboBox  
 Přidá pole se seznamem do dialogu.  
  
```  
HRESULT AddComboBox(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID pole se seznamem přidat.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addcontrolitem"></a>CFileDialog::AddControlItem  
 Přidá položku do kontejneru ovládacího prvku v dialogovém okně.  
  
```  
HRESULT AddControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku kontejneru přidat položku do.  
  
 `dwIDItem`  
 ID položky.  
  
 `strLabel`  
 Text položky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addeditbox"></a>CFileDialog::AddEditBox  
 Přidá do dialogu textové pole.  
  
```  
HRESULT AddEditBox(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID textové pole pro přidání.  
  
 `strText`  
 Upravit název pole.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addmenu"></a>CFileDialog::AddMenu  
 Dialogové okno umožňuje přidat nabídku.  
  
```  
HRESULT AddMenu(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID nabídky přidat.  
  
 `strLabel`  
 Název nabídky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addplace"></a>CFileDialog::AddPlace  
 Přidá že umístí do složky, do seznamu k dispozici pro uživatele k otevření nebo uložení položky.  
  
```  
void AddPlace(
    LPCWSTR lpszFolder,  
    FDAP fdap = FDAP_TOP) throw();

 
void AddPlace(
    IShellItem* psi,  
    FDAP fdap = FDAP_TOP) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFolder`  
 Cesta ke složce, které budou dostupné pro uživatele. To může být pouze do složky.  
  
 `fdap`  
 Určuje, kde je umístěn složce v seznamu.  
  
 `psi`  
 Ukazatel IShellItem, která představuje složku, které budou dostupné pro uživatele. To může být pouze do složky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addpushbutton"></a>CFileDialog::AddPushButton  
 Přidá tlačítko do dialogového okna.  
  
```  
HRESULT AddPushButton(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID na tlačítko Přidat.  
  
 `strLabel`  
 Název tlačítka.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addradiobuttonlist"></a>CFileDialog::AddRadioButtonList  
 Přidá skupiny přepínačů (také označované jako přepínač) do dialogu.  
  
```  
HRESULT AddRadioButtonList(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID skupiny přepínače přidat.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addseparator"></a>CFileDialog::AddSeparator  
 Přidá oddělovač do dialogového okna.  
  
```  
HRESULT AddSeparator(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 Přidat ID oddělovače.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addtext"></a>CFileDialog::AddText  
 Přidá k dialogové okno text.  
  
```  
HRESULT AddText(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID text přidat.  
  
 `strText`  
 Název textu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="applyofntoshelldialog"></a>CFileDialog::ApplyOFNToShellDialog  
 Aktualizuje aktuální stav [CFileDialog](../../mfc/reference/cfiledialog-class.md) na základě hodnot, které jsou uložené v `m_ofn` datové struktury.  
  
```  
void ApplyOFNToShellDialog();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve verzích Windows před [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], člen [název otevřeného souboru](https://msdn.microsoft.com/library/ms911906.aspx) struktura dat byla nepřetržitě synchronizována se stavem `CFileDialog`. Všechny změny [m_ofn](#m_ofn) členské proměnné se okamžitě projeví ve stavu dialogového okna. Navíc okamžitě aktualizovat všechny změny stavu dialogové okno `m_ofn` členské proměnné.  
  
 V [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], hodnoty `m_ofn` členské proměnné a stavu `CFileDialog` se nezaručuje, že má být synchronizována. Tato funkce vynutí stav `CFileDialog` aktualizovat tak, aby odpovídala `m_ofn` struktura. Windows zavolá tato funkce automaticky během [CFileDialog::DoModal](#domodal).  
  
 Další informace o tom, jak používat `CFileDialog` třídy pod [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], najdete v části [CFileDialog třída](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog).  
  
##  <a name="cfiledialog"></a>CFileDialog::CFileDialog  
 Volání této funkce můžete vytvořit standardní dialogové okno souboru systému Windows.  
  
```  
explicit CFileDialog(
    BOOL bOpenFileDialog,  
    LPCTSTR lpszDefExt = NULL,  
    LPCTSTR lpszFileName = NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT,  
    LPCTSTR lpszFilter = NULL,  
    CWnd* pParentWnd = NULL,  
    DWORD dwSize = 0,  
    BOOL bVistaStyle = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bOpenFileDialog`  
 Parametr, který určuje, jaký typ dialogové okno vytvořit. Nastavte ji na `TRUE` k vytvoření **otevřít soubor** dialogové okno. Nastavte ji na `FALSE` k vytvoření **uložit jako** dialogové okno.  
  
 [v]`lpszDefExt`  
 Výchozí přípona názvu souboru. Pokud uživatel neobsahuje známou příponou, (jeden, který má přidružení v počítači uživatele) do pole název souboru, rozšíření určeného `lpszDefExt` se automaticky připojí k názvu souboru. Pokud tento parametr je `NULL`, se připojí žádné rozšíření.  
  
 [v]`lpszFileName`  
 Název počáteční souboru, který se zobrazí v poli Název souboru. Pokud `NULL`, zobrazí se žádné počáteční název souboru.  
  
 [v]`dwFlags`  
 Kombinace jeden nebo více příznaky, které můžete použít k přizpůsobení dialogové okno. Popis tyto příznaky najdete v tématu [název otevřeného souboru](http://msdn.microsoft.com/library/windows/desktop/ms646839) struktura ve Windows SDK. Pokud změníte `m_ofn.Flags` struktury člen, použijte operátor bitové operace OR změny zachovat výchozí chování beze změn.  
  
 [v]`lpszFilter`  
 Řadu páry řetězec, které určují filtry můžete použít k souboru. Pokud zadáte filtry souborů, zobrazí se pouze soubory, které odpovídají kritériím filtru v seznamu souborů. Další informace o tom, jak pracovat s filtry souborů v části poznámky.  
  
 [v]`pParentWnd`  
 Ukazatel na okno nadřazené nebo vlastníka dialogového okna souboru.  
  
 [v]`dwSize`  
 Velikost `OPENFILENAME` struktura. Tato hodnota závisí na verzi operačního systému. MFC používá tento parametr k určení odpovídající druh dialogové okno vytvořit (například, nových [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] dialogová okna místo dialogová okna systému Windows NT 4). Výchozí velikost 0 znamená, že kód MFC určí správné rozměry dialogového okna používat podle verze operačního systému, na kterém je program spustit.  
  
 [v]`bVistaStyle`  
 **Poznámka:** tento parametr je k dispozici v sadě Visual Studio 2008 a novější a bude je způsobit dialogového okna Nový styl a používat pouze v případě, že používáte [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] nebo novější.  
  
 Parametr, který určuje typ dialogového okna souboru. Nastavte ji na `TRUE` používat nové dialogy souboru styl Vista. Jinak se použije staré styl dialogová okna. Naleznete v části poznámky Další informace spuštěna pod Vista.  
  
### <a name="remarks"></a>Poznámky  
 Buď **otevřít soubor** nebo **uložit jako** sestavený dialogové okno, v závislosti na hodnotě `bOpenFileDialog`.  
  
 Určení výchozí rozšíření pomocí `lpszDefExt` nemusí poskytovat chování, které očekáváte, protože je málokdy předvídatelný jaká rozšíření se přidružení souborů v počítači uživatele. Pokud potřebujete větší kontrolu nad připojování výchozí přípona, můžete odvodit vlastní třídy z `CFileDialog`a přepsat `CFileDialog::OnFileNameOK` metodu za účelem zpracování vlastní rozšíření.  
  
 Chcete-li povolit uživateli vybrat více souborů, nastavte `OFN_ALLOWMULTISELECT` příznak před voláním [DoModal](#domodal). Je třeba zadat vlastní vyrovnávací paměť názvu souboru pro uložení seznamu vrácených více názvů souborů. To udělat tak, že nahradíte `m_ofn.lpstrFile` pomocí ukazatele do vyrovnávací paměti jste přidělili, co vytvoříte [CFileDialog](../../mfc/reference/cfiledialog-class.md), ale před voláním `DoModal`. Kromě toho je nutné nastavit `m_ofn.nMaxFile` s počtem znaků ve vyrovnávací paměti, na kterou odkazuje `m_ofn.lpstrFile`. Pokud nastavíte maximální počet souborů, aby byl vybrán k `n`, nezbytné vyrovnávací paměť je `n`*(_MAX_PATH + 1) + 1. Příklad:  
  
 [!code-cpp[NVC_MFCFiles#23](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_1.cpp)]  
  
 Chcete-li zajistit, aby uživatel ke změně velikosti dialogové okno stylu Průzkumníku pomocí myši nebo klávesnice, nastavte `OFN_ENABLESIZING` příznak. Nastavením tohoto příznaku je nutné pouze v případě, že poskytuje háku postup nebo vlastní šablony. Příznak funguje pouze v dialogovém okně knihovny stylu Průzkumníku; dialogová okna starého nelze změnit.  
  
 `lpszFilter` Parametr se používá k určení typu název souboru, který se má zobrazit v seznamu souborů musí mít soubor. První řetězec v páru řetězec popisuje filtr; druhý řetězec Určuje příponu názvu souboru použít. Při použití středník (znak ';') jako oddělovač, který může zadat několik rozšíření. Řetězec končí dva ' &#124;' znaky, za nímž následuje `NULL` znak. Můžete použít také [CString](../../atl-mfc-shared/using-cstring.md) objekt pro tento parametr.  
  
 Například [!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)] umožňuje uživatelům otevírat soubory, které mají rozšíření XLC (graf) nebo XLS (list), mimo jiné. Filtr pro aplikaci Excel může zapsat jako:  
  
 [!code-cpp[NVC_MFCFiles#24](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_2.cpp)]  
  
 Ale pokud budete chtít použít tento řetězec k přímo aktualizovat `OPENFILENAME` struktura, by měl oddělování vaší řetězců s znak hodnoty null, '\0' místo svislých pruhů ('&#124;').  
  
 `bVistaStyle` Parametr platí jenom v případě, že je spuštěná s pověřeními [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. V dřívějších verzích systému Windows tento parametr je ignorován. Pokud `bVistaStyle` je nastaven na `TRUE`, když zkompilujete program s Visual Studio 2008 nebo novější, nový styl Vista **dialogové okno souboru** se použije. V opačném styl předchozí MFC **dialogové okno souboru** se použije.  
  
 Šablony dialogu nejsou podporovány na na základě dialogová okna`bVistaStyle`  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileDialog::DoModal](#domodal).  
  
##  <a name="domodal"></a>CFileDialog::DoModal  
 Volání této funkce můžete zobrazit dialogové okno souboru systému Windows běžné a povolit uživatelům procházet soubory a adresáře a zadejte název souboru.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **IDOK** nebo **IDCANCEL**. Pokud **IDCANCEL** je vrácen, volání Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkce k určení, zda došlo k chybě.  
  
 **IDOK** a **IDCANCEL** jsou konstanty, které označuje, zda uživatel vybrané na tlačítko OK nebo Storno.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různé možnosti – dialogové okno souboru nastavením členy **m_ofn** struktura, bude třeba provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
 Například pokud chcete umožnit uživateli vybrat více souborů, nastavte `OFN_ALLOWMULTISELECT` příznak před voláním `DoModal`, jak je znázorněno v příkladu v tomto tématu.  
  
 Když uživatel klikne na tlačítko OK nebo Storno dialogových oken nebo ukončení vybere možnost z dialogových oken řídit nabídky, ovládací prvek se vrátí do vaší aplikace. Můžete pak volat jiné členské funkce načíst informace o nastavení nebo vstupů uživatele do dialogového okna.  
  
 `DoModal`je virtuální funkci přepsat ze třídy `CDialog`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#25](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_3.cpp)]  
  
##  <a name="enableopendropdown"></a>CFileDialog::EnableOpenDropDown  
 Umožňuje rozevíracím seznamu v okně Otevřít nebo uložit tlačítka v dialogovém okně.  
  
```  
HRESULT EnableOpenDropDown(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID rozevíracího seznamu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="endvisualgroup"></a>CFileDialog::EndVisualGroup  
 Zastaví Přidání elementů do visual skupiny v dialogovém okně.  
  
```  
HRESULT EndVisualGroup();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěšného; Chyba hodnotu, jinak hodnota.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcheckbuttonstate"></a>CFileDialog::GetCheckButtonState  
 Načte aktuální stav kontroly tlačítko (zaškrtávací políčko) v dialogovém okně.  
  
```  
HRESULT GetCheckButtonState(
    DWORD dwIDCtl,  
    BOOL& bChecked);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID políčko.  
  
 `bChecked`  
 Stav zaškrtnutí políčka. `TRUE`označuje zaškrtnuté; `FALSE` označuje nezaškrtnuté.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcontrolitemstate"></a>CFileDialog::GetControlItemState  
 Načte aktuální stav položky v ovládacím prvku kontejneru najít v dialogovém okně.  
  
```  
HRESULT GetControlItemState(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    CDCONTROLSTATEF& dwState);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku kontejneru.  
  
 `dwIDItem`  
 ID položky.  
  
 `dwState`  
 Odkaz na proměnnou, která přijímá jeden z více hodnot z CDCONTROLSTATE výčet, který označuje aktuální stav ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcontrolstate"></a>CFileDialog::GetControlState  
 Načte aktuální viditelnost a jejich stavů daný ovládací prvek.  
  
```  
HRESULT GetControlState(
    DWORD dwIDCtl,  
    CDCONTROLSTATEF& dwState);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku.  
  
 `dwState`  
 Odkaz na proměnnou, která přijímá jeden nebo více hodnot z CDCONTROLSTATE výčet, který označuje aktuální stav ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="geteditboxtext"></a>CFileDialog::GetEditBoxText  
 Načte aktuální text v ovládacím prvku upravit.  
  
```  
HRESULT GetEditBoxText(
    DWORD dwIDCtl,  
    CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID pole pro úpravy.  
  
 `strText`  
 Textové hodnoty.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getfileext"></a>CFileDialog::GetFileExt  
 Volání této funkce načíst příponou názvu souboru do dialogových oken.  
  
```  
CString GetFileExt() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Přípona názvu souboru.  
  
### <a name="remarks"></a>Poznámky  
 Například pokud je název souboru zadaná DATA. Soubory TXT, `GetFileExt` vrátí "TXT".  
  
 Pokud `m_ofn.Flags` má `OFN_ALLOWMULTISELECT` nastaven příznak, tento řetězec obsahuje posloupnost řetězce ukončené hodnotou null, první řetězcem, který se cesta k adresáři souboru skupiny vybrané, za nímž následuje názvy všechny soubory vybrané uživatelem. Chcete-li načíst cest k souborům, použijte [GetStartPosition](#getstartposition) a [GetNextPathName](#getnextpathname) členské funkce.  
  
##  <a name="getfilename"></a>CFileDialog::GetFileName  
 Volání této funkce načíst název zadaný v dialogovém okně název souboru.  
  
```  
CString GetFileName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název souboru.  
  
### <a name="remarks"></a>Poznámky  
 Název souboru obsahuje předponu i rozšíření. Například `GetFileName` vrátí "TEXT. UŽ"pro soubor C:\FILES\TEXT.DAT.  
  
 Pokud `m_ofn.Flags` má `OFN_ALLOWMULTISELECT` příznak nastaven, by měly volat [GetStartPosition](#getstartposition) a [GetNextPathName](#getnextpathname) načtení cesty souboru.  
  
##  <a name="getfiletitle"></a>CFileDialog::GetFileTitle  
 Volání této funkce můžete získat název souboru zadali v dialogovém okně.  
  
```  
CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název souboru.  
  
### <a name="remarks"></a>Poznámky  
 Název souboru obsahuje pouze předponu jeho, bez cestu nebo rozšíření. Například `GetFileTitle` vrátí "TEXT" pro soubor C:\FILES\TEXT.DAT.  
  
 Pokud `m_ofn.Flags` má `OFN_ALLOWMULTISELECT` nastaven příznak, tento řetězec obsahuje posloupnost řetězce ukončené hodnotou null, první řetězcem, který se cesta k adresáři souboru skupiny vybrané, za nímž následuje názvy všechny soubory vybrané uživatelem. Z tohoto důvodu použít [GetStartPosition](#getstartposition) a [GetNextPathName](#getnextpathname) členské funkce pro načtení další název souboru v seznamu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileDialog::DoModal](#domodal).  
  
##  <a name="getfolderpath"></a>CFileDialog::GetFolderPath  
 Volání této funkce člen se načíst cestu aktuálně otevřít složku nebo adresář pro stylu Průzkumníku otevřít nebo uložit jako běžné dialogové.  
  
```  
CString GetFolderPath() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující aktuálně otevřít složku nebo adresář.  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno musí být vytvořen s **OFN_EXPLORER** styl; jinak metoda selže s kontrolní výrazy.  
  
 Tuto metodu lze volat pouze tehdy, když se zobrazuje dialogové okno. Po zavření dialogu, tato funkce přestane fungovat a metodu se nezdaří s kontrolní výrazy.  
  
##  <a name="getifiledialogcustomize"></a>CFileDialog::GetIFileDialogCustomize  
 Načte ukazatel pro vnitřní objekt COM danou [CFileDialog](../../mfc/reference/cfiledialog-class.md).  
  
```  
IFileDialogCustomize* GetIFileDialogCustomize();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na vnitřní objekt COM pro `CFileDialog`. Je vaší povinností k uvolnění tento ukazatel správně.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci použít pouze v části [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] s objektem, který má `bVistaStyle` nastavena na `true`. Pokud použijete tuto funkci při `bVistaStyle` je `false`, vrátí `NULL` v režimu vydání a throw kontrolní výrazy v režimu ladění.  
  
 Další informace o `IFileDialogCustomize` rozhraní najdete v tématu [IFileDialogCustomize](http://msdn.microsoft.com/library/windows/desktop/bb775912).  
  
### <a name="example"></a>Příklad  
 Tento příklad načte vnitřní objekt COM. Pokud chcete spustit tento příklad kódu, je nutné jej pod zkompilovat [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  
  
 [!code-cpp[NVC_MFC_CFileDialog#4](../../mfc/reference/codesnippet/cpp/cfiledialog-class_4.cpp)]  
  
##  <a name="getifileopendialog"></a>CFileDialog::GetIFileOpenDialog  
 Načte ukazatel pro vnitřní objekt COM danou `CFileDialog`.  
  
```  
IFileOpenDialog* GetIFileOpenDialog();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na vnitřní objekt COM pro `CFileDialog`. Je vaší povinností k uvolnění tento ukazatel správně.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci použít pouze v části [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] s objektem, který má `bVistaStyle` nastavena na `true`. Funkce vrátí hodnotu `NULL` Pokud `CFileDialog` není **otevřete** dialogové okno nebo, pokud `bVistaStyle` je nastaven na `false`. V tomto případě konečné pouze funkce vrátí `NULL` v režimu vydání – v režimu ladění se vyvolá výjimku kontrolní výrazy.  
  
 Další informace o `IFileOpenDialog` rozhraní najdete v tématu [IFileOpenDialog](http://msdn.microsoft.com/library/windows/desktop/bb775834).  
  
### <a name="example"></a>Příklad  
 Tento příklad načte vnitřní objekt COM. Pokud chcete spustit tento kód, je nutné jej pod zkompilovat [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  
  
 [!code-cpp[NVC_MFC_CFileDialog#2](../../mfc/reference/codesnippet/cpp/cfiledialog-class_5.cpp)]  
  
##  <a name="getifilesavedialog"></a>CFileDialog::GetIFileSaveDialog  
 Načte ukazatel pro vnitřní objekt COM danou `CFileDialog`.  
  
```  
IFileSaveDialog* GetIFileSaveDialog();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na vnitřní objekt COM pro `CFileDialog`. Je vaší povinností k uvolnění tento ukazatel správně.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci použít pouze v části [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] s objektem, který má `bVistaStyle` nastavena na `true`. Tato funkce vrací `NULL` Pokud `CFileDialog` není **Uložit** dialogové okno nebo, pokud `bVistaStyle` je nastaven na `false`. V tomto případě konečné pouze funkce vrátí `NULL` v režimu vydání – v režimu ladění se vyvolá výjimku kontrolní výrazy.  
  
 Další informace o `IFileSaveDialog` rozhraní najdete v tématu [IFileSaveDialog](http://msdn.microsoft.com/library/windows/desktop/bb775688).  
  
### <a name="example"></a>Příklad  
 Tento příklad načte vnitřní objekt COM. Pokud chcete spustit tento příklad kódu, je nutné jej pod zkompilovat [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  
  
 [!code-cpp[NVC_MFC_CFileDialog#3](../../mfc/reference/codesnippet/cpp/cfiledialog-class_6.cpp)]  
  
##  <a name="getnextpathname"></a>CFileDialog::GetNextPathName  
 Volání této funkce pro načtení další filename ze skupiny vybrané v dialogovém okně.  
  
```  
CString GetNextPathName(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Odkaz na **pozice** hodnoty vrácené předchozí `GetNextPathName` nebo `GetStartPosition` volání funkce. **NULL** Pokud bylo dosaženo konce seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Úplná cesta souboru.  
  
### <a name="remarks"></a>Poznámky  
 Cesta název souboru obsahuje název souboru a cesta k adresáři celý. Například `GetNextPathName` vrátí "C:\FILES\TEXT. UŽ"pro soubor C:\FILES\TEXT.DAT. Můžete použít `GetNextPathName` ve smyčce dopředného iterace Pokud vytvořit počáteční pozice pomocí volání `GetStartPosition`.  
  
 Pokud výběr obsahuje pouze jeden soubor, bude vrácen tento název souboru.  
  
##  <a name="getofn"></a>CFileDialog::GetOFN  
 Načte přidruženého **název otevřeného souboru** struktura.  
  
```  
const OPENFILENAME& GetOFN() const;  
  
OPENFILENAME& GetOFN();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 [Název otevřeného souboru](http://msdn.microsoft.com/library/windows/desktop/ms646839) struktura.  
  
### <a name="remarks"></a>Poznámky  
 Druhá verze této funkce použijte k chybě při inicializaci vzhled **otevřít soubor** nebo **uložit jako** po je vytvořený, ale předtím, než se zobrazí se dialogové `DoModal` – členská funkce. Například můžete nastavit **lpstrTitle** členem **m_ofn** na titulek má dialogu mít.  
  
##  <a name="getpathname"></a>CFileDialog::GetPathName  
 Volání této funkce načíst úplnou cestu souboru zadanou v dialogovém okně.  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Úplná cesta souboru.  
  
### <a name="remarks"></a>Poznámky  
 Cesta název souboru obsahuje název souboru a cesta k adresáři celý. Například `GetPathName` vrátí "C:\FILES\TEXT. UŽ"pro soubor C:\FILES\TEXT.DAT.  
  
 Pokud `m_ofn.Flags` má `OFN_ALLOWMULTISELECT` nastaven příznak, tento řetězec obsahuje posloupnost z null teminated řetězce první řetězcem, který se cesta k adresáři souboru skupiny vybrané, za nímž následuje názvy všech souborů vybraných uživatelem. Z tohoto důvodu použít [GetStartPosition](#getstartposition) a [GetNextPathName](#getnextpathname) členské funkce pro načtení další název souboru v seznamu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileDialog::DoModal](#domodal).  
  
##  <a name="getreadonlypref"></a>CFileDialog::GetReadOnlyPref  
 Volání této funkce k určení, zda pole jen pro čtení vybral v dialogových Windows standardní soubor otevřít a uložit jako.  
  
```  
BOOL GetReadOnlyPref() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulová Pokud je zaškrtnuto políčko jen pro čtení v dialogovém okně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zaškrtněte políčko jen pro čtení můžete skrýt, a to nastavením `OFN_HIDEREADONLY` styl v `CFileDialog` konstruktor.  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]Styl `CFileDialog` objekty nepodporují tuto funkci. Pokus o použití této funkce na [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] styl `CFileDialog` vyvolá výjimku [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).   
  
##  <a name="getresult"></a>CFileDialog::GetResult  
 Načte volbou, která uživatel provedené v dialogovém okně.  
  
```  
IShellItem* GetResult() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel IShellItem, který představuje volby uživatele.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getresults"></a>CFileDialog::GetResults  
 Načte volby uživatele v dialogovém okně, které umožňuje vícenásobný výběr.  
  
```  
IShellItemArray* GetResults() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel IShellItemArray, pomocí kterého je přístupná položek vybraných v dialogovém okně.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getselectedcontrolitem"></a>CFileDialog::GetSelectedControlItem  
 Načte položku konkrétní z ovládacího prvku zadaného kontejneru. v dialogovém okně.  
  
```  
HRESULT GetSelectedControlItem(
    DWORD dwIDCtl,  
    DWORD& dwIDItem);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku kontejneru.  
  
 `dwIDItem`  
 ID položky, kterou uživatel vybraný v ovládacím prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getstartposition"></a>CFileDialog::GetStartPosition  
 Volání této funkce člen načíst pozice prvního názvu cesty souboru v seznamu, pokud `m_ofn.Flags` má `OFN_ALLOWMULTISELECT` nastaven příznak.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci; **NULL** Pokud je seznam prázdný.  
  
##  <a name="hidecontrol"></a>CFileDialog::HideControl  
 Volání této funkce člen ke skrytí daný ovládací prvek ve stylu Průzkumníku otevřít nebo uložit jako běžné dialogové.  
  
```  
void HideControl(int nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 ID ovládacího prvku skrýt.  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno musí být vytvořen s **OFN_EXPLORER** styl; jinak funkce selže s kontrolní výrazy.  
  
##  <a name="ispickfoldersmode"></a>CFileDialog::IsPickFoldersMode  
 Určuje, zda aktuální dialogové okno v režimu výběr složky.  
  
```  
BOOL IsPickFoldersMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud dialogu je v režimu výběr složky; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_ofn"></a>CFileDialog::m_ofn  
 `m_ofn`je struktura typu `OPENFILENAME`. Data v této struktuře představuje aktuální stav `CFileDialog`.  
  
### <a name="remarks"></a>Poznámky  
 Tato struktura se používá k chybě při inicializaci vzhled **otevřít soubor** nebo **uložit jako** dialogu, co ji vytvoříte, ale před zobrazením s [DoModal](#domodal) metoda. Například můžete nastavit `lpstrTitle` členem `m_ofn` na titulek má dialogu mít.  
  
 Pomocí [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] styl [CFileDialog](../../mfc/reference/cfiledialog-class.md), `m_ofn` není zaručeno, že vždy odpovídat stav dialogové okno. Synchronizovat se službou dialogového okna v dřívějších verzích systému Windows. V tématu [CFileDialog::ApplyOFNToShellDialog](#applyofntoshelldialog) a [CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog) pro další informace o synchronizaci `m_ofn` struktura a `CFileDialog` stavu v části [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  
  
 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]Styl souboru dialogová okna nepodporují určité členy a příznaky z `CFileDialog`. V důsledku toho tyto nebude mít žádný vliv.  
  
 Následuje seznam členů, které nepodporují [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
- `lpstrCustomFilter`  
  
- `lpstrInitialDir`  
  
- `lCustData`  
  
- `lpfnHook`  
  
- `lpTemplateName`  
  
 Následující příznaky nejsou podporovány a proto nemají žádný vliv, pokud použijete [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] styl `CFileDialog`:  
  
-   OFN_ENABLEHOOK  
  
-   OFN_ENABLEINCLUDENOTIFY  
  
-   OFN_ENABLETEMPLATE  
  
-   OFN_ENABLETEMPLATEHANDLE  
  
-   OFN_EXPLORER  
  
-   OFN_EXTENSIONDIFFERENT  
  
-   OFN_HIDEREADONLY  
  
-   OFN_LONGNAMES - efektivně vždy na v[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_NOLONGNAMES - efektivně vždy vypnout v[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_NONETWORKBUTTON - efektivně vždy na v[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_READONLY  
  
-   OFN_SHOWHELP  
  
 Další informace o tuto strukturu, najdete v článku [název otevřeného souboru](http://msdn.microsoft.com/library/windows/desktop/ms646839) struktura ve Windows SDK.  
  
##  <a name="makeprominent"></a>CFileDialog::MakeProminent  
 Místech ovládacího prvku v dialogovém okně tak, aby vystupoval ve srovnání s další ovládací prvky.  
  
```  
HRESULT MakeProminent(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onbuttonclicked"></a>CFileDialog::OnButtonClicked  
 Volá se při kliknutí na tlačítko.  
  
```  
virtual void OnButtonClicked(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID tlačítko.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="oncheckbuttontoggled"></a>CFileDialog::OnCheckButtonToggled  
 Volá se při zaškrtávací políčko je zaškrtnuté nebo nezaškrtnuté.  
  
```  
virtual void OnCheckButtonToggled(
    DWORD dwIDCtl,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID políčko.  
  
 `bChecked`  
 Zaškrtnuté nebo nezaškrtnuté.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="oncontrolactivating"></a>CFileDialog::OnControlActivating  
 Voláno, když je aktivován ovládací prvek.  
  
```  
virtual void OnControlActivating(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onfilenamechange"></a>CFileDialog::OnFileNY` `změn  
 Potlačí tuto metodu, pokud chcete zpracovat `WM_NOTIFY` `CDN_SELCHANGE` zprávy.  
  
```  
virtual void OnFileNameChange();
```  
  
### <a name="remarks"></a>Poznámky  
 Odešle systému `CDN_SELCHANGE` zprávy, když uživatel vybere nový soubor nebo složku v seznamu souborů **otevřete** nebo **uložit jako** dialogové okno. Potlačí tuto metodu, pokud chcete provádět všechny akce v odpovědi na tuto zprávu.  
  
 Systém odešle tuto zprávu pouze v případě, že dialogové okno byl vytvořen s příznakem OFN_EXPLORER zapnutý. Další informace o oznámení najdete v tématu [CDN_SELCHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646865). Informace o příznak OFN_EXPLORER najdete v tématu [název otevřeného souboru](http://msdn.microsoft.com/library/windows/desktop/ms646839) struktura a [otevřít a uložit jako dialogových oken](http://msdn.microsoft.com/library/windows/desktop/ms646960).  
  
##  <a name="onfilenameok"></a>CFileDialog::OnFileNameOK  
 Tato funkce přepsání, pouze v případě, že chcete zadat vlastní ověření názvů souborů, které jsou vloženy do běžné dialogové okno souboru.  
  
```  
virtual BOOL OnFileNameOK();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 1, pokud název souboru není platný název souboru. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce umožňuje odmítnout název souboru z nějakého důvodu specifické pro aplikaci. Za normálních okolností není potřeba tuto funkci použít, protože rozhraní framework poskytuje výchozí ověření názvů souborů a zobrazí okno se zprávou, pokud je zadán neplatný název souboru.  
  
 Pokud vrátí hodnotu 1, dialogové okno zůstane zobrazené pro uživatele k zadání jiného názvu souboru. Postup dialogové okno zavře dialogové okno, pokud je návratový 0. Další nenulové hodnoty vrátí hodnoty momentálně rezervovaných a by se neměla používat.  
  
##  <a name="onfolderchange"></a>CFileDialog::OnFolderChange  
 Funkci pro zpracování přepsat **WM_NOTIFYCDN_FOLDERCHANGE** zprávy.  
  
```  
virtual void OnFolderChange();
```  
  
### <a name="remarks"></a>Poznámky  
 Odeslání zprávy oznámení jsou při otevření v dialogovém okně Otevřít nebo uložit jako novou složku.  
  
 Oznámení se odesílá pouze v případě, že styl OFN_EXPLORER pochází dialogové okno. Další informace o oznámení najdete v tématu [CDN_FOLDERCHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646859). Informace o stylu OFN_EXPLORER najdete v tématu [název otevřeného souboru](http://msdn.microsoft.com/library/windows/desktop/ms646839) struktura a [otevřít a uložit jako dialogových oken](http://msdn.microsoft.com/library/windows/desktop/ms646960).  
  
##  <a name="oninitdone"></a>CFileDialog::OnInitDone  
 Funkci pro zpracování přepsat `WM_NOTIFY` `CDN_INITDONE` zprávy.  
  
```  
virtual void OnInitDone();
```  
  
### <a name="remarks"></a>Poznámky  
 Systém odešle tuto zprávu oznámení po dokončení uspořádání ovládacích prvků v systému **otevřete** nebo **uložit jako** dialogové okno aby uvolnil prostor pro ovládací prvky dialogového okna podřízené.  
  
 Systém odešle to jenom v případě, že styl OFN_EXPLORER pochází dialogové okno. Další informace o oznámení najdete v tématu [CDN_INITDONE](http://msdn.microsoft.com/library/windows/desktop/ms646863). Informace o stylu OFN_EXPLORER najdete v tématu [název otevřeného souboru](http://msdn.microsoft.com/library/windows/desktop/ms646839) struktura a [otevřít a uložit jako dialogových oken](http://msdn.microsoft.com/library/windows/desktop/ms646960).  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]Styl souboru dialogová okna nepodporují tuto funkci. Pokus o použití této funkce na [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] vyvolá dialogové okno souboru styl [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md). 
  
##  <a name="onitemselected"></a>CFileDialog::OnItemSelected  
 Voláno, pokud je vybraná položka kontejneru.  
  
```  
virtual void OnItemSelected(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku kontejneru.  
  
 `dwIDItem`  
 ID položky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onlbselchangednotify"></a>CFileDialog::OnLBSelChangedNotify  
 Tato funkce je volána, když aktuální výběr v seznamu se má změnit.  
  
```  
virtual void OnLBSelChangedNotify(
    UINT nIDBox,  
    UINT iCurSel,  
    UINT nCode);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDBox*  
 ID pole se seznamem nebo pole se seznamem, v němž došlo k výběru.  
  
 `iCurSel`  
 Index aktuální výběr.  
  
 `nCode`  
 Kód oznámení ovládacího prvku. Tento parametr musí mít jednu z následujících hodnot:  
  
- **CD_LBSELCHANGE** Určuje `iCurSel` pro vybranou položku v seznamu jedním výběrem.  
  
- **CD_LBSELSUB** Určuje, že `iCurSel` je již vybrána v multiselection seznamu.  
  
- **CD_LBSELADD** Určuje, že `iCurSel` je vybraný v multiselection seznamu.  
  
- **CD_LBSELNOITEMS** Určuje, že žádná výběru v multiselection seznamu existuje.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkce můžete poskytnout vlastní zpracování změn výběr v seznamu. Například tuto funkci můžete použít k zobrazení přístupová práva nebo datum – poslední změny každého souboru uživatel vybere.  
  
##  <a name="onshareviolation"></a>CFileDialog::OnShareViolation  
 Přepsání této funkce můžete poskytnout vlastní zpracování narušení sdílení.  
  
```  
virtual UINT OnShareViolation(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPathName`  
 Cesta souboru, na kterém došlo k narušení sdílení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících hodnot:  
  
- **OFN_SHAREFALLTHROUGH** název souboru je vrácena z dialogového okna.  
  
- **OFN_SHARENOWARN** žádná další akce je potřeba provést.  
  
- **OFN_SHAREWARN** uživatel obdrží standardní upozornění pro tuto chybu.  
  
### <a name="remarks"></a>Poznámky  
 Za normálních okolností není potřeba tuto funkci použít, protože rozhraní framework poskytuje výchozí kontrola porušení sdílené složky a zobrazí okno se zprávou, pokud dojde k narušení sdílení.  
  
 Pokud chcete kontrolu narušení sdílení zakázat, použijte bitový operátor OR kombinovat příznak **OFN_SHAREAWARE** s `m_ofn.Flags`.  
  
##  <a name="ontypechange"></a>CFileDialog::OnTypeChange  
 Funkci pro zpracování přepsat **WM_NOTIFYCDN_TYPECHANGE** zprávy.  
  
```  
virtual void OnTypeChange();
```  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel vybere nový typ souboru ze seznamu typů souborů v okně Otevřít nebo uložit jako dialogové odeslána zpráva oznámení.  
  
 Oznámení se odesílá pouze v případě, že styl OFN_EXPLORER pochází dialogové okno. Další informace o oznámení najdete v tématu [CDN_TYPECHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646868). Informace o stylu OFN_EXPLORER najdete v tématu [název otevřeného souboru](http://msdn.microsoft.com/library/windows/desktop/ms646839) struktura a [otevřít a uložit jako dialogových oken](http://msdn.microsoft.com/library/windows/desktop/ms646960).  
  
##  <a name="removecontrolitem"></a>CFileDialog::RemoveControlItem  
 Odebere položku z kontejneru ovládacího prvku v dialogovém okně.  
  
```  
HRESULT RemoveControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku kontejneru odebrat položku z.  
  
 `dwIDItem`  
 ID položky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcheckbuttonstate"></a>CFileDialog::SetCheckButtonState  
 V dialogovém okně nastaví aktuální stav kontroly tlačítka (zaškrtávací políčko).  
  
```  
HRESULT SetCheckButtonState(
    DWORD dwIDCtl,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID políčko.  
  
 `bChecked`  
 Stav zaškrtnutí políčka. `TRUE`označuje zaškrtnuté; `FALSE` označuje Unchecked.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcontrolitemstate"></a>CFileDialog::SetControlItemState  
 Nastaví aktuální stav položky v ovládacím prvku kontejneru najít v dialogovém okně.  
  
```  
HRESULT SetControlItemState(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    CDCONTROLSTATEF dwState);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku kontejneru.  
  
 `dwIDItem`  
 ID položky.  
  
 `dwState`  
 Jedna nebo více hodnot z výčtu CDCONTROLSTATE které označují nový stav ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcontrolitemtext"></a>CFileDialog::SetControlItemText  
 Nastaví text položky ovládacího prvku. Například text, který doprovází přepínače nebo položku v nabídce.  
  
```  
HRESULT SetControlItemText(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku kontejneru.  
  
 `dwIDItem`  
 ID položky.  
  
 `strLabel`  
 Text položky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcontrollabel"></a>CFileDialog::SetControlLabel  
 Nastaví text související s ovládacím prvkem, jako je text tlačítka nebo popisek pole upravit.  
  
```  
HRESULT SetControlLabel(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku.  
  
 `strLabel`  
 Název ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcontrolstate"></a>CFileDialog::SetControlState  
 Nastaví aktuální viditelnost a jejich stavů daný ovládací prvek.  
  
```  
HRESULT SetControlState(
    DWORD dwIDCtl,  
    CDCONTROLSTATEF dwState);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku.  
  
 `dwState`  
 Jedna nebo více hodnot z výčtu CDCONTROLSTATE které označují aktuální stav ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcontroltext"></a>CFileDialog::SetControlText  
 Volat tuto metodu a nastavit text pro daný ovládací prvek ve stylu Průzkumníku **otevřete** nebo **uložit jako** dialogové okno.  
  
```  
void SetControlText(
    int nID,  
    LPCSTR lpsz);

 
void SetControlText(
    int nID,  
    const wchar_t *lpsz);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nID`  
 ID ovládacího prvku, pro kterou chcete nastavit text.  
  
 [v]`lpsz`  
 Ukazatel na řetězec, který obsahuje nastavení pro ovládací prvek text.  
  
### <a name="remarks"></a>Poznámky  
 Obě verze této funkce jsou platné pro aplikace, které používají kódování Unicode. Ale je platná pro aplikace, které používají pouze verze s typem LPCSTR [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)].  
  
 Chcete-li použít tuto metodu, musíte vytvořit dialogové okno s OFN_EXPLORER styl. Funkce, jinak se nezdaří s kontrolní výrazy.  
  
##  <a name="setdefext"></a>CFileDialog::SetDefExt  
 Volejte tuto funkci nastavit příponu názvu souboru výchozí styl Průzkumníku otevřít nebo uložit jako běžné dialogové.  
  
```  
void SetDefExt(LPCSTR lpsz);
```  
  
### <a name="parameters"></a>Parametry  
 `lpsz`  
 Ukazatel na řetězec obsahující výchozí rozšíření pro pole objektu dialogového okna. Tento řetězec nesmí obsahovat tečku (.).  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno musí být vytvořen s **OFN_EXPLORER** styl; jinak funkce selže s kontrolní výrazy.  
  
##  <a name="seteditboxtext"></a>CFileDialog::SetEditBoxText  
 Nastaví aktuální text v ovládacím prvku upravit.  
  
```  
HRESULT SetEditBoxText(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID pole pro úpravy.  
  
 `strText`  
 Textové hodnoty.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setproperties"></a>CFileDialog::SetProperties  
 Poskytuje úložiště vlastností, která definuje výchozí hodnoty, který se má použít pro položku ukládají.  
  
```  
BOOL SetProperties(LPCWSTR lpszPropList);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPropList`  
 Seznam předdefinovaných vlastností oddělených ";". Seznam příznaků, najdete v článku `Flags` části [název otevřeného souboru](http://msdn.microsoft.com/en-us/8cecfd45-f7c1-4f8d-81a0-4e7fecc3b104).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setselectedcontrolitem"></a>CFileDialog::SetSelectedControlItem  
 Nastaví vybraný stav konkrétní položky skupiny přepínačů nebo v poli se seznamem najít v dialogovém okně.  
  
```  
HRESULT SetSelectedControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID ovládacího prvku kontejneru.  
  
 `dwIDItem`  
 ID položky, kterou uživatel vybraný v ovládacím prvku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settemplate"></a>CFileDialog::SetTemplate  
 Nastaví pole šablony dialogového okna pro [CFileDialog](../../mfc/reference/cfiledialog-class.md) objektu.  
  
```  
void SetTemplate(
    UINT nWin3ID,  
    UINT nWin4ID);

 
void SetTemplate(
    LPCTSTR lpWin3ID,  
    LPCTSTR lpWin4ID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nWin3ID`  
 Obsahuje počet ID prostředku šablony pro jiný Explorer `CFileDialog` objektu. Tato šablona se používá pouze v systému Windows NT 3.51, nebo když styl OFN_EXPLORER není k dispozici.  
  
 [v]`nWin4ID`  
 Obsahuje počet ID prostředku šablony pro aplikaci Explorer `CFileDialog` objektu. Tato šablona se používá pouze v [!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)] a novější verze, systém Windows 95 a novější verze, nebo pokud je styl OFN_EXPLORER přítomna.  
  
 [v]`lpWin3ID`  
 Obsahuje název prostředku šablony pro jiný Explorer `CFileDialog` objektu. Tato šablona se používá pouze v systému Windows NT 3.51, nebo když styl OFN_EXPLORER není k dispozici.  
  
 [v]`lpWin4ID`  
 Obsahuje název prostředku šablony Průzkumníku `CFileDialog` objektu. Tato šablona se používá pouze v [!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)] a novější verze, systém Windows 95 a novější verze, nebo pokud je styl OFN_EXPLORER přítomna.  
  
### <a name="remarks"></a>Poznámky  
 Systém bude používat pouze jeden z určené šablony. Systém zjišťuje, kterou šablonu použít na základě přítomnosti styl OFN_EXPLORER a operační systém, který je aplikace spuštěna v. Zadáním bez Explorer i stylu Průzkumníku šablony, je snadné podpory systému Windows NT 3.51, [!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)] a novější verze a systém Windows 95 a novější verze.  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]Styl souboru dialogová okna nepodporují tuto funkci. Pokus o použití této funkce na [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] vyvolá dialogové okno souboru styl [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md). Další možností je použití vlastní dialogového okna. Další informace o používání vlastní `CFileDialog`, najdete v části [IFileDialogCustomize](http://msdn.microsoft.com/library/windows/desktop/bb775912).  
  
##  <a name="startvisualgroup"></a>CFileDialog::StartVisualGroup  
 Deklaruje visual skupiny v dialogovém okně. Do této skupiny přidat následující volání do kterékoli metody "Přidat" těchto elementů.  
  
```  
HRESULT StartVisualGroup(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parametry  
 `dwIDCtl`  
 ID visual skupiny.  
  
 `strLabel`  
 Název skupiny.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="updateofnfromshelldialog"></a>CFileDialog::UpdateOFNFromShellDialog  
 Aktualizace `m_ofn` struktura dat [CFileDialog](../../mfc/reference/cfiledialog-class.md) na základě aktuálního stavu objektu interní.  
  
```  
void UpdateOFNFromShellDialog();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve verzích Windows před [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], člen [název otevřeného souboru](https://msdn.microsoft.com/library/ms911906.aspx) struktura dat byla nepřetržitě synchronizována se stavem `CFileDialog`. Všechny změny [m_ofn](#m_ofn) členské proměnné přímo vliv na stav dialogové okno. Změny stavu dialogu také aktualizovat okamžitě m_ofn členské proměnné.  
  
 V [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], `m_ofn` datová struktura nebudou automaticky aktualizovány. Chcete-li zaručit, že data v `m_ofn` členské proměnné, by měly volat `UpdateOFNFromShellDialog` funkce před přístupu k datům. Tato funkce Windows automaticky zavolá během zpracování [IFileDialog::OnFileOK](http://msdn.microsoft.com/library/windows/desktop/bb775879).  
  
 Další informace o tom, jak používat `CFileDialog` třídy pod [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], najdete v části [CFileDialog třída](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Příklad  
 Aktualizace v tomto příkladu `CFileDialog` před jejich zobrazením. Před aktualizací `m_ofn` členské proměnné, potřebujeme k synchronizaci na aktuální stav dialogového okna.  
  
 [!code-cpp[NVC_MFC_CFileDialog#1](../../mfc/reference/codesnippet/cpp/cfiledialog-class_7.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

