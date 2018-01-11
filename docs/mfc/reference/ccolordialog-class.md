---
title: "Třída CColorDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
dev_langs: C++
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38fbca875847e557981c09dc418c8e0ef65bed6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccolordialog-class"></a>CColorDialog – třída
Umožňuje začlenit dialogové okno Výběr barev do vaší aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CColorDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CColorDialog::CColorDialog](#ccolordialog)|Vytvoří `CColorDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CColorDialog::DoModal](#domodal)|Zobrazí dialogové okno barvy a umožní uživateli proveďte výběr.|  
|[CColorDialog::GetColor](#getcolor)|Vrátí **COLORREF** struktura obsahující hodnoty vybrané barvy.|  
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Načte vlastní barvy vytvořený uživatelem.|  
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Aktuální výběr barev zadaná barva vynutí.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CColorDialog::OnColorOK](#oncolorok)|Přepsání nastavení za účelem ověření barvu vloženy do dialogových oken.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CColorDialog::m_cc](#m_cc)|Struktura používaná pro přizpůsobení nastavení dialogové okno.|  
  
## <a name="remarks"></a>Poznámky  
 A `CColorDialog` objektu je dialogové okno se seznamem barev, které jsou definovány pro systém zobrazení. Uživatele můžete vybrat nebo vytvořit konkrétní barvu ze seznamu, která se pak vykazuje zpět do aplikace při ukončí dialogové okno.  
  
 K vytvoření `CColorDialog` objektu, použijte zadaný konstruktor nebo odvodit novou třídu a použijte vlastní vlastní konstruktor.  
  
 Jakmile dialogové okno byl vytvořený, můžete nastavit nebo změnit všechny hodnoty v [m_cc](#m_cc) struktura k chybě při inicializaci hodnoty ovládací prvky dialogových oken. `m_cc` Struktura je typu [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830).  
  
 Po inicializaci ovládací prvky dialogových oken, volání `DoModal` – členská funkce a zobrazit dialogové okno Povolit uživateli vybrat barvu. `DoModal`Vrátí uživatele výběr buď OK dialogových oken ( **IDOK**) nebo zrušit ( **IDCANCEL**) tlačítko.  
  
 Pokud `DoModal` vrátí **IDOK**, můžete použít jednu z `CColorDialog`na členské funkce načíst informace o zadaný uživatelem.  
  
 Můžete použít Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkce k určení, zda došlo k chybě během inicializace dialogových oken a další informace o této chybě.  
  
 `CColorDialog`spoléhá na COMMDLG. Soubor knihovny DLL, která se dodává s verzí systému Windows verze 3.1 nebo novější.  
  
 Chcete-li přizpůsobit dialogové okno, odvození třídy z `CColorDialog`zadejte dialogové okno vlastní šablony a přidat mapy zpráv pro zpracování zprávy s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měla být předána základní třídy.  
  
 Přizpůsobení funkce háku se nevyžaduje.  
  
> [!NOTE]
>  Na některé instalace `CColorDialog` objekt nezobrazí barvou pozadí, pokud jste použili rozhraní aby dalších `CDialog` šedá objekty.  
  
 Další informace o používání `CColorDialog`, najdete v části [společné třídy dialogových oken](../../mfc/common-dialog-classes.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CColorDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="ccolordialog"></a>CColorDialog::CColorDialog  
 Vytvoří `CColorDialog` objektu.  
  
```  
CColorDialog(
    COLORREF clrInit = 0,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *clrInit*  
 Výchozí výběr barev. Pokud není zadaná žádná hodnota, výchozí hodnota je RGB(0,0,0) (černé).  
  
 `dwFlags`  
 Sada příznaky, které funkce a vzhled dialogové okno přizpůsobit. Další informace najdete v tématu [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830) struktura ve Windows SDK.  
  
 `pParentWnd`  
 Ukazatele v dialogovém okně nadřazené nebo vlastníka.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]  
  
##  <a name="domodal"></a>CColorDialog::DoModal  
 Volání této funkce a zobrazit dialogové okno barvy systému Windows běžné uživateli umožní vybrat barvu.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **IDOK** nebo **IDCANCEL**. Pokud **IDCANCEL** je vrácen, volání Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkce k určení, zda došlo k chybě.  
  
 **IDOK** a **IDCANCEL** jsou konstanty, které označuje, zda uživatel vybrané na tlačítko OK nebo Storno.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různé možnosti – dialogové okno barvy nastavením členy [m_cc](#m_cc) struktura, bude třeba provést před voláním `DoModal` , ale po vytvoření objektu sady dialogového.  
  
 Po volání `DoModal`, můžete volat jiné členské funkce načíst nastavení nebo uživatelský vstup informace do dialogových oken.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CColorDialog::CColorDialog](#ccolordialog).  
  
##  <a name="getcolor"></a>CColorDialog::GetColor  
 Volání této funkce po volání `DoModal` k načtení informací o barvu vybraného uživatele.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která obsahuje informace o RGB barvy vybraných v dialogovém okně barvy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]  
  
##  <a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors  
 `CColorDialog`objekty povolit uživatele, kromě výběr barvy, definovat až 16 vlastní barvy.  
  
```  
static COLORREF* PASCAL GetSavedCustomColors();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pole 16 RGB – hodnoty barev, které ukládá vlastních barev vytvořený uživatelem.  
  
### <a name="remarks"></a>Poznámky  
 `GetSavedCustomColors` – Členská funkce poskytuje přístup pro tyto barev. Tyto barvy lze získat po [DoModal](#domodal) vrátí **IDOK**.  
  
 Každý z 16 hodnoty RGB v poli vráceném je inicializováno RGB(255,255,255) (bílé). Vlastní barvy volená uživatelem se uloží jenom mezi dialogové okno pole volání v aplikaci. Pokud chcete uložit tyto barvy mezi volání aplikace, musíte je uložit jiným způsobem, jako třeba v inicializaci (. Soubor INI).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]  
  
##  <a name="m_cc"></a>CColorDialog::m_cc  
 Struktura typu [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830), jejíž členové uložení charakteristiky a hodnot dialogového okna.  
  
```  
CHOOSECOLOR m_cc;  
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření `CColorDialog` objekt, můžete použít `m_cc` nastavit různé aspekty dialogu před voláním [DoModal](#domodal) – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]  
  
##  <a name="oncolorok"></a>CColorDialog::OnColorOK  
 Přepsání nastavení za účelem ověření barvu vloženy do dialogových oken.  
  
```  
virtual BOOL OnColorOK();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud by neměl zavře dialogové okno; jinak 0 tak, aby přijímal barvu, která byla zadána.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce přepsání, pouze v případě, že chcete zadat vlastní ověření barvy, které uživatel vybere v dialogovém okně barvy.  
  
 Uživatele můžete vybrat barvu pomocí jedné z následujících dvou metod:  
  
-   Kliknutím na tlačítko barvy na paletu barev. Hodnoty RGB vybrané barvy se projeví do příslušných polí RGB upravit.  
  
-   Vstup hodnoty RGB textových polí  
  
 Přepsání `OnColorOK` umožňuje odmítnout barvu, která uživatel zadá do běžné dialogové okno barvy z jakéhokoli důvodu specifické pro aplikaci.  
  
 Za normálních okolností není potřeba tuto funkci použít, protože rozhraní framework poskytuje výchozí ověření barvy a zobrazí okno se zprávou, pokud je zadaný neplatný barev.  
  
 Můžete volat [SetCurrentColor](#setcurrentcolor) uvnitř `OnColorOK` vynutit výběr barev. Jednou `OnColorOK` má aktivován (to znamená, že uživatel klikne na **OK** tak, aby přijímal Změna barvy), můžete volat [getcolor –](#getcolor) k získání hodnoty RGB nové barvy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]  
  
##  <a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor  
 Volání této funkce po volání `DoModal` vynutit aktuální výběr barev barva hodnota zadaná v `clr`.  
  
```  
void SetCurrentColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 `clr`  
 Hodnotu barva RGB.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána z v rámci obslužné rutiny zpráv nebo `OnColorOK`. Dialogové okno se automaticky aktualizuje na základě hodnoty z výběru uživatele `clr` parametr.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CColorDialog::OnColorOK](#oncolorok).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDI](../../visual-cpp-samples.md)   
 [Ukázka MFC DRAWCLI](../../visual-cpp-samples.md)   
 [CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

