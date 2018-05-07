---
title: Třída CFindReplaceDialog | Microsoft Docs
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
ms.openlocfilehash: 21499f65ac762dfd08d90decad41eedf3dfc5cdf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog – třída
Umožňuje implementovat standardní řetězec vyhledání a nahrazení dialogových oken v aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Volání této funkce můžete vytvořit `CFindReplaceDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFindReplaceDialog::Create](#create)|Vytvoří a zobrazí `CFindReplaceDialog` dialogové okno.|  
|[CFindReplaceDialog::FindNext](#findnext)|Volání této funkce určete, jestli uživatel chce najít další výskyt najít řetězec.|  
|[CFindReplaceDialog::GetFindString](#getfindstring)|Volání této funkce pro získání aktuálního řetězce najít.|  
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Volání této funkce můžete získat **FINDREPLACE** struktury ve vaší obslužné rutiny zpráv registrované.|  
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Volání této funkce pro získání aktuálního řetězce nahrazení.|  
|[CFindReplaceDialog::IsTerminating](#isterminating)|Volání této funkce určete, zda je ukončován dialogové okno.|  
|[CFindReplaceDialog::MatchCase](#matchcase)|Volání této funkce určete, jestli uživatel chce přesně shodují v případě najít řetězec.|  
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Volání této funkce určete, jestli uživatel chce hledat jenom celá slova.|  
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Volání této funkce určete, jestli uživatel chce, aby všechny výskyty řetězec, který má být nahrazen.|  
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Volání této funkce určete, jestli uživatel chce aktuální slovo, které mají být nahrazeny.|  
|[CFindReplaceDialog::SearchDown](#searchdown)|Volání této funkce určete, jestli uživatel chce vyhledávání, chcete-li pokračovat v klesající směru.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CFindReplaceDialog::m_fr](#m_fr)|Struktura sloužící k přizpůsobení `CFindReplaceDialog` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Na rozdíl od jiných Windows běžných dialogových oken `CFindReplaceDialog` objekty jsou nemodální, což umožňuje uživatelům interakci s jinými, které se na obrazovce. Existují dva typy z `CFindReplaceDialog` objekty: najít dialogových oken a dialogová okna vyhledání a nahrazení. I když dialogových oken povolit uživatelům vstupní vyhledávání a hledání a nahrazení řetězce, neslouží k provádění hledání nebo nahrazení funkce. Je nutné přidat do aplikace.  
  
 K vytvoření `CFindReplaceDialog` objektu, pomocí zadané konstruktoru (což je bez argumentů). Vzhledem k tomu, že je nemodální dialogové okno, přidělit objekt na používání haldy **nové** operátor, a nikoli v zásobníku.  
  
 Jednou `CFindReplaceDialog` objekt byl vytvořen, je třeba zavolat [vytvořit](#create) – členská funkce k vytváření a zobrazování dialogových oken.  
  
 Použití [m_fr](#m_fr) struktura inicializace dialogu před voláním **vytvořit**. `m_fr` Struktura je typu [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835). Další informace o tuto strukturu najdete v části Windows SDK.  
  
 Aby nadřazené okno, které mají být informování vyhledání a nahrazení požadavků, musíte použít Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) fungovat a využívat [on_registered_message –](message-map-macros-mfc.md#on_registered_message) makra map zpráv vaší rámce okno, která zpracovává registrované zpráva.  
  
 Můžete určit, zda uživatel se rozhodl ukončit dialogové okno s `IsTerminating` – členská funkce.  
  
 `CFindReplaceDialog` spoléhá na COMMDLG. Soubor knihovny DLL, která se dodává s verzí systému Windows verze 3.1 nebo novější.  
  
 Chcete-li přizpůsobit dialogové okno, odvození třídy z `CFindReplaceDialog`zadejte dialogové okno vlastní šablony a přidat mapy zpráv pro zpracování zprávy s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měla být předána základní třídy.  
  
 Přizpůsobení funkce háku se nevyžaduje.  
  
 Další informace o používání `CFindReplaceDialog`, najdete v části [třídy společných dialogů](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFindReplaceDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="cfindreplacedialog"></a>  CFindReplaceDialog::CFindReplaceDialog  
 Vytvoří `CFindReplaceDialog` objektu.  
  
```  
CFindReplaceDialog();
```  
  
### <a name="remarks"></a>Poznámky  
 Protože `CFindReplaceDialog` objekt nemodální dialogového okna, je nutné ji vytvořit v haldě pomocí `new` operátor.  
  
 Při odstraňování, rozhraní pokusu o provedení `delete this` na ukazatel na dialogové okno. Pokud jste vytvořili dialogových oken v zásobníku, `this` ukazatel neexistuje a může způsobit nedefinované chování.  
  
 Další informace o budování `CFindReplaceDialog` objekty, najdete [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) Přehled. Použití [CFindReplaceDialog::Create](#create) členské funkce k zobrazení dialogového okna.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]  
  
##  <a name="create"></a>  CFindReplaceDialog::Create  
 Vytvoří a zobrazí buď najít, nebo vyhledání a nahrazení objektu dialogového okna pole, v závislosti na hodnotě `bFindDialogOnly`.  
  
```  
virtual BOOL Create(
    BOOL bFindDialogOnly,  
    LPCTSTR lpszFindWhat,  
    LPCTSTR lpszReplaceWith = NULL,  
    DWORD dwFlags = FR_DOWN,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bFindDialogOnly`  
 Tento parametr nastavte na `TRUE` k zobrazení **najít** dialogové okno. Nastavte ji na `FALSE` k zobrazení **vyhledání a nahrazení** dialogové okno.  
  
 `lpszFindWhat`  
 Ukazatel na výchozí řetězec hledání, když se zobrazí dialogové okno. Pokud `NULL`, dialogové okno neobsahuje výchozí hledaný řetězec.  
  
 `lpszReplaceWith`  
 Ukazatel na výchozí náhradní řetězec, když se zobrazí dialogové okno. Pokud `NULL`, dialogové okno neobsahuje výchozí náhradní řetězec.  
  
 `dwFlags`  
 Jeden nebo více příznaky, které můžete použít k přizpůsobení nastavení dialogovém okně spojovat pomocí bitový operátor OR. Výchozí hodnota je `FR_DOWN`, která určuje, že hledání je chcete-li pokračovat v klesající směru. Najdete v článku [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835) struktura ve Windows SDK pro další informace o tyto příznaky.  
  
 `pParentWnd`  
 Ukazatele v dialogovém okně nadřazené nebo vlastníka. Toto je okno, která bude přijímat speciální zpráva označující, že je vyžadován akce vyhledání a nahrazení. Pokud `NULL`, se používá v hlavním okně aplikace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl úspěšně vytvořen pole objektu dialogového okna; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aby nadřazené okno, které mají být informování vyhledání a nahrazení požadavků, musíte použít Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) funkce, jejíž vrácená hodnota je číslo zprávy, která je jedinečné pro instanci aplikace. Oken s rámečkem by měl mít položku mapování zpráv, který deklaruje funkce zpětného volání ( `OnFindReplace` v příkladu, který následuje) registrovaný zpráva, která zpracovává. Následující fragment kódu je příklad toho, jak to udělat pro s názvem třídy oken s rámečkem `CMyRichEditView`:  
  
 [!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]  
  
 [!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]  
  
 V rámci vaší `OnFindReplace` funkce, interpretovat záměry uživatele pomocí [CFindReplaceDialog::FindNext](#findnext) a [CFindReplaceDialog::IsTerminating](#isterminating) metody a vy vytvoříte kód pro vyhledání a nahrazení operace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).  
  
##  <a name="findnext"></a>  CFindReplaceDialog::FindNext  
 Volání této funkce z funkce zpětného volání k určení, jestli uživatel chce najít další výskyt hledaný řetězec.  
  
```  
BOOL FindNext() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud chce uživatel najít další výskyt řetězec pro hledání; jinak 0.  
  
##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString  
 Volání této funkce z funkce zpětného volání k načtení výchozí řetězec k vyhledání.  
  
```  
CString GetFindString() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí řetězec k vyhledání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getnotifier"></a>  CFindReplaceDialog::GetNotifier  
 Volání této funkce načíst ukazatel na aktuální najít dialogové okno Nahradit.  
  
```  
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `lParam`  
 **Lparam** hodnota předaná do okna rámce **OnFindReplace** – členská funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuální dialogových oken.  
  
### <a name="remarks"></a>Poznámky  
 By být používána v rámci funkce zpětného volání přístup aktuální dialogových oken, volání jeho členských funkcí a přístup `m_fr` struktura.  
  
### <a name="example"></a>Příklad  
 V tématu [CFindReplaceDialog::Create](#create) příklad toho, jak zaregistrovat OnFindReplace obslužná rutina pro příjem oznámení z dialogového okna Najít Nahradit.  
  
 [!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString  
 Volání této funkce pro získání aktuálního řetězce nahrazení.  
  
```  
CString GetReplaceString() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí řetězec, ke které má být nalezena řetězce nahrazeny.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFindReplaceDialog::GetFindString](#getfindstring).  
  
##  <a name="isterminating"></a>  CFindReplaceDialog::IsTerminating  
 Volání této funkce v rámci funkce zpětného volání k určení, zda uživatel se rozhodl ukončit dialogové okno.  
  
```  
BOOL IsTerminating() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud uživatel se rozhodl ukončit dialogové okno. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je tato funkce vrátí nenulovou hodnotu, měli byste zavolat `DestroyWindow` – členská funkce aktuální dialogové okno a sadu žádné dialogové proměnné ukazatele na **NULL**. Volitelně můžete také ukládat poslední zadaný text vyhledání a nahrazení a použít pro inicializaci dialogu další vyhledání a nahrazení.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFindReplaceDialog::GetFindString](#getfindstring).  
  
##  <a name="m_fr"></a>  CFindReplaceDialog::m_fr  
 Použít pro přizpůsobení `CFindReplaceDialog` objektu.  
  
```  
FINDREPLACE m_fr;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_fr` je struktura typu [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835). Její členové uložení charakteristiky-dialogové objektu. Po vytváření `CFindReplaceDialog` objekt, můžete použít `m_fr` na různé hodnoty v dialogovém okně Upravit.  
  
 Další informace o tuto strukturu, najdete v článku **FINDREPLACE** struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).  
  
##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase  
 Volání této funkce určete, jestli uživatel chce přesně shodují v případě najít řetězec.  
  
```  
BOOL MatchCase() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud uživatel chce výskytů řetězec pro hledání, které přesně odpovídají malá řetězec pro hledání; jinak 0.  
  
##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord  
 Volání této funkce určete, jestli uživatel chce hledat jenom celá slova.  
  
```  
BOOL MatchWholeWord() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud chce uživatel hledat jenom celá slova řetězec pro hledání; jinak 0.  
  
##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll  
 Volání této funkce určete, jestli uživatel chce, aby všechny výskyty řetězec, který má být nahrazen.  
  
```  
BOOL ReplaceAll() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud uživatel vyžaduje, aby všechny řetězce odpovídající nahraďte řetězec nahradit; jinak 0.  
  
##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent  
 Volání této funkce určete, jestli uživatel chce aktuální slovo, které mají být nahrazeny.  
  
```  
BOOL ReplaceCurrent() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud uživatel požádal, že aktuálně vybraný řetězec nahrazen nahraďte řetězec; jinak 0.  
  
##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown  
 Volání této funkce určete, jestli uživatel chce vyhledávání, chcete-li pokračovat v klesající směru.  
  
```  
BOOL SearchDown() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud uživatel chce, aby se výsledky vyhledávání na pokračovat v sestupný směr; 0, pokud uživatel chce, aby se výsledky vyhledávání na pokračovat směrem vzhůru.  
  
## <a name="see-also"></a>Viz také  
 [CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)  
