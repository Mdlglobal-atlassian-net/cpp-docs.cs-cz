---
title: Cfindreplacedialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
dev_langs:
- C++
helpviewer_keywords:
- CFindReplaceDialog [MFC], CFindReplaceDialog
- CFindReplaceDialog [MFC], Create
- CFindReplaceDialog [MFC], FindNext
- CFindReplaceDialog [MFC], GetFindString
- CFindReplaceDialog [MFC], GetNotifier
- CFindReplaceDialog [MFC], GetReplaceString
- CFindReplaceDialog [MFC], IsTerminating
- CFindReplaceDialog [MFC], MatchCase
- CFindReplaceDialog [MFC], MatchWholeWord
- CFindReplaceDialog [MFC], ReplaceAll
- CFindReplaceDialog [MFC], ReplaceCurrent
- CFindReplaceDialog [MFC], SearchDown
- CFindReplaceDialog [MFC], m_fr
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cabd6f331ed7348fe84a585a863ccb7e90b992fc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204002"
---
# <a name="cfindreplacedialog-class"></a>Cfindreplacedialog – třída
Umožňuje implementovat dialogová okna Najít a nahradit standardní řetězec ve vaší aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Voláním této funkce k vytvoření `CFindReplaceDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFindReplaceDialog::Create](#create)|Vytvoří a zobrazí `CFindReplaceDialog` dialogové okno.|  
|[CFindReplaceDialog::FindNext](#findnext)|Voláním této funkce určete, jestli uživatel chce najde další výskyt řetězce hledání.|  
|[CFindReplaceDialog::GetFindString](#getfindstring)|Volání této funkce načtete aktuální řetězec hledání.|  
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Voláním této funkce načtete `FINDREPLACE` struktura v obslužné rutině registrované zprávy.|  
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Volání této funkce načtete aktuální nahradit řetězec.|  
|[CFindReplaceDialog::IsTerminating](#isterminating)|Voláním této funkce k určení, zda dialogové okno se ukončuje.|  
|[CFindReplaceDialog::MatchCase](#matchcase)|Voláním této funkce určete, jestli uživatel chce přesně shodovat s velikostí písmen řetězce hledání.|  
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Voláním této funkce určete, jestli uživatel chce, aby hledat pouze celá slova.|  
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Voláním této funkce určete, jestli uživatel chce, aby všechny výskyty řetězec, který má být nahrazen.|  
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Voláním této funkce určete, jestli uživatel chce vyměnit aktuálního slova.|  
|[CFindReplaceDialog::SearchDown](#searchdown)|Voláním této funkce určete, jestli uživatel chce, aby hledání, aby mohli pokračovat ve směru dolů.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CFindReplaceDialog::m_fr](#m_fr)|Struktura používané k úpravám `CFindReplaceDialog` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Na rozdíl od jiných Windows běžných dialogových oken `CFindReplaceDialog` objekty jsou nemodální, což umožňuje uživatelům interakci s ostatními okny, pokud nejsou na obrazovce. Existují dva typy z `CFindReplaceDialog` objekty: Vyhledejte dialogová okna a dialogová okna Najít a nahradit. I když dialogových oknech umožní uživateli vstupní hledání a hledání a nahrazení řetězce, ne provádějí vyhledání nebo nahrazení funkce. Musíte je přidat do aplikace.  
  
 K vytvoření `CFindReplaceDialog` objektu, použijte poskytnutý konstruktoru (která nemá žádné argumenty). Protože to je nemodální dialogové okno, přidělit objekt, který pomocí haldy **nové** operátor, spíše než v zásobníku.  
  
 Jednou `CFindReplaceDialog` objekt byl vytvořen, je třeba zavolat [vytvořit](#create) členskou funkci k vytváření a zobrazování dialogových oken.  
  
 Použití [m_fr](#m_fr) struktura inicializace dialogových oken před voláním `Create`. `m_fr` Struktury je typu [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea). Další informace o této struktuře naleznete v tématu Windows SDK.  
  
 Aby nadřazené okno upozornit najít/nahradit požadavky, je nutné použít Windows [RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947) fungovat a využívat [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) makra map zpráv v rámce okno, která zpracovává tuto zprávu registrovaný.  
  
 Můžete určit, zda uživatel se rozhodl ukončí dialogové okno s `IsTerminating` členskou funkci.  
  
 `CFindReplaceDialog` využívá COMMDLG. Soubor knihovny DLL, která se dodává s Windows verze 3.1 nebo novější.  
  
 Přizpůsobení dialogových oken, odvoďte třídu z `CFindReplaceDialog`zadejte šablonu vlastního dialogu a přidání mapy zpráv pro zpracování zpráv s oznámením z rozšířené ovládací prvky. Všechny nezpracované zprávy by měly být předány základní třídy.  
  
 Přizpůsobení funkce háku se nevyžaduje.  
  
 Další informace o používání `CFindReplaceDialog`, naleznete v tématu [společné třídy dialogových oken](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [Ccommondialog –](../../mfc/reference/ccommondialog-class.md)  
  
 `CFindReplaceDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="cfindreplacedialog"></a>  CFindReplaceDialog::CFindReplaceDialog  
 Vytvoří `CFindReplaceDialog` objektu.  
  
```  
CFindReplaceDialog();
```  
  
### <a name="remarks"></a>Poznámky  
 Protože `CFindReplaceDialog` objekt je nemodální dialogové okno, je nutné ji vytvořit v haldě pomocí **nové** operátor.  
  
 Během odstraňování, pokusí provést rozhraní framework **odstranit tento** na ukazatel do dialogového okna. Pokud jste vytvořili v zásobníku, dialogových oken **to** ukazatel neexistuje a může způsobit nedefinované chování.  
  
 Další informace o procesu vytváření `CFindReplaceDialog` objekty, najdete [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) Přehled. Použití [CFindReplaceDialog::Create](#create) členské funkce k zobrazení dialogového okna.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]  
  
##  <a name="create"></a>  CFindReplaceDialog::Create  
 Vytvoří a zobrazí Hledat nebo najít/nahradit dialogové okno pole objektu, závisí na hodnotě `bFindDialogOnly`.  
  
```  
virtual BOOL Create(
    BOOL bFindDialogOnly,  
    LPCTSTR lpszFindWhat,  
    LPCTSTR lpszReplaceWith = NULL,  
    DWORD dwFlags = FR_DOWN,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *bFindDialogOnly*  
 Tento parametr nastaven na hodnotu TRUE, chcete-li zobrazit **najít** dialogové okno. Nastavte na FALSE, pokud chcete zobrazit **najít/nahradit** dialogové okno.  
  
 *lpszFindWhat*  
 Ukazatel na řetězec výchozí vyhledávání, když se zobrazí dialogové okno. Pokud má hodnotu NULL, dialogové okno neobsahuje výchozí hledaný řetězec.  
  
 *lpszReplaceWith*  
 Ukazatel na řetězec nahrazení výchozí, když se zobrazí dialogové okno. Pokud má hodnotu NULL, dialogové okno neobsahuje výchozí řetězec nahrazení.  
  
 *dwFlags*  
 Jeden nebo více příznaků, které vám umožní přizpůsobit nastavení dialogovém okně kombinované pomocí bitového operátoru OR. Výchozí hodnota je FR_DOWN, které určuje, že hledání pokračovat směrem dolů. Zobrazit [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea) struktura v sadě Windows SDK pro další informace o těchto příznacích.  
  
 *pParentWnd*  
 Ukazatel na okno nadřazené nebo vlastník dialogových oken. To je okno, které se zobrazí zvláštní zpráva označující, že je požadována akce najít a nahradit. Pokud má hodnotu NULL, použije se v hlavním okně aplikace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud objekt dialog box byl úspěšně vytvořen; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aby nadřazené okno upozornit najít/nahradit požadavky, je nutné použít Windows [RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947) funkce, vrácená hodnota je zpráva číslo jedinečné pro instanci aplikace. Okno rámce by měl mít položku mapování zpráv, který deklaruje funkci zpětného volání ( `OnFindReplace` v následujícím příkladu), která zpracovává tuto zprávu registrovaný. Následující fragment kódu je příklad toho, jak to provést u okna rámce třídy s názvem `CMyRichEditView`:  
  
 [!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]  
  
 [!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]  
  
 V rámci vaší `OnFindReplace` funkce, interpretovat záměry uživatele pomocí [CFindReplaceDialog::FindNext](#findnext) a [CFindReplaceDialog::IsTerminating](#isterminating) metod a vy vytvoříte kód pro operace hledání a nahrazení.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).  
  
##  <a name="findnext"></a>  CFindReplaceDialog::FindNext  
 Voláním této funkce z funkce zpětného volání k určení, jestli uživatel chce najde další výskyt hledaný řetězec.  
  
```  
BOOL FindNext() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud chce uživatel najde další výskyt hledaný řetězec; jinak 0.  
  
##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString  
 Voláním této funkce z funkce zpětného volání k načtení výchozí řetězec k vyhledání.  
  
```  
CString GetFindString() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí řetězec k vyhledání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getnotifier"></a>  CFindReplaceDialog::GetNotifier  
 Volání této funkce načtete ukazatel na aktuální najít dialogového okna nahradit.  
  
```  
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 *lParam*  
 *Lparam* předanou do okna rámce `OnFindReplace` členskou funkci.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuální dialogových oken.  
  
### <a name="remarks"></a>Poznámky  
 Se má použít v rámci funkce zpětného volání pro přístup k dialogovému oknu aktuální, zavolejte jeho členů, funkcí a přístup `m_fr` struktury.  
  
### <a name="example"></a>Příklad  
 Zobrazit [CFindReplaceDialog::Create](#create) příklad toho, jak zaregistrovat obslužnou rutinu OnFindReplace dostávala oznámení z dialogového okna Najít Nahradit.  
  
 [!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString  
 Volání této funkce načtete aktuální nahradit řetězec.  
  
```  
CString GetReplaceString() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí řetězec, pomocí kterého se má nahradit nalezené řetězce.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFindReplaceDialog::GetFindString](#getfindstring).  
  
##  <a name="isterminating"></a>  CFindReplaceDialog::IsTerminating  
 Voláním této funkce v rámci funkce zpětného volání k určení, zda uživatel se rozhodl ukončí dialogové okno.  
  
```  
BOOL IsTerminating() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud uživatel se rozhodl ukončí dialogové okno. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato funkce vrátí nenulovou hodnotu, měli byste zavolat `DestroyWindow` členskou funkci aktuálním dialogovém okně pole a nastavíte proměnné ukazatele žádné dialogové okno pole na hodnotu NULL. Volitelně můžete také ukládat poslední zadaný text najít/nahradit a použít k inicializaci dalším dialogovém okně Najít a nahradit.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFindReplaceDialog::GetFindString](#getfindstring).  
  
##  <a name="m_fr"></a>  CFindReplaceDialog::m_fr  
 Používané k úpravám `CFindReplaceDialog` objektu.  
  
```  
FINDREPLACE m_fr;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_fr` Struktura typu [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea). Jeho členové uložení vlastnosti z objektu dialogového okna. Po sestavení `CFindReplaceDialog` objektu, můžete použít `m_fr` na různé hodnoty v dialogovém okně Upravit.  
  
 Další informace o této struktuře naleznete v tématu `FINDREPLACE` struktura v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).  
  
##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase  
 Voláním této funkce určete, jestli uživatel chce přesně shodovat s velikostí písmen řetězce hledání.  
  
```  
BOOL MatchCase() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud chce uživatel najít výskytů řetězce vyhledávání, které přesně shodovat s velikostí písmen hledaný řetězec; jinak 0.  
  
##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord  
 Voláním této funkce určete, jestli uživatel chce, aby hledat pouze celá slova.  
  
```  
BOOL MatchWholeWord() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud chce uživatel hledat pouze celá slova hledaný řetězec; jinak 0.  
  
##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll  
 Voláním této funkce určete, jestli uživatel chce, aby všechny výskyty řetězec, který má být nahrazen.  
  
```  
BOOL ReplaceAll() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud uživatel požaduje, aby všechny řetězce odpovídající řetězec nahrazení nahradit; jinak 0.  
  
##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent  
 Voláním této funkce určete, jestli uživatel chce vyměnit aktuálního slova.  
  
```  
BOOL ReplaceCurrent() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud uživatel požaduje, že aktuálně vybraný řetězec nahradit řetězec nahrazení; jinak 0.  
  
##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown  
 Voláním této funkce určete, jestli uživatel chce, aby hledání, aby mohli pokračovat ve směru dolů.  
  
```  
BOOL SearchDown() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud uživatel chce, aby hledání pokračovat ve směru dolů; 0, pokud uživatel chce, aby hledání pokračovat směrem vzhůru.  
  
## <a name="see-also"></a>Viz také  
 [Ccommondialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)  
