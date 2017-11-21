---
title: "Třída CMFCMaskedEdit | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
dev_langs: C++
helpviewer_keywords:
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5b0a00db89d930555b083d57a9d1ed54daf0564c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit – třída
`CMFCMaskedEdit` Třída podporuje ovládací prvek maskované pole, která ověří vstup uživatele s maskou a zobrazí výsledky ověřené podle šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCMaskedEdit : public CEdit  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCMaskedEdit::CMFCMaskedEdit`|Výchozí konstruktor.|  
|`CMFCMaskedEdit::~CMFCMaskedEdit`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCMaskedEdit::DisableMask](#disablemask)|Zakáže ověřování uživatelského vstupu.|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Určuje, zda `GetWindowText` metoda načte pouze maskované znaky.|  
|[CMFCMaskedEdit::EnableMask](#enablemask)|Inicializuje maskované ovládacích prvků pro úpravy.|  
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Určuje, zda ovládací prvek maskované pole vybere konkrétní skupiny vstup uživatele nebo zadání od všechny uživatele.|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Určuje, zda text bude ověřeno jen maskovat znaků, nebo pro celý maska.|  
|`CMFCMaskedEdit::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Načte ověřit text z maskované textové pole.|  
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Určuje řetězec platné znaky, které může uživatel zadat.|  
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Zobrazí výzvu v maskované textové pole.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Voláno rámcem k ověření je zadaný znak proti odpovídající znak masky.|  
  
## <a name="remarks"></a>Poznámky  
 Proveďte následující kroky a použít `CMFCMaskedEdit` ovládacího prvku ve vaší aplikaci:  
  
 1. Vložení `CMFCMaskedEdit` objektu do vaší třídy oken.  
  
 2. Volání [CMFCMaskedEdit::EnableMask](#enablemask) metoda k určení maska.  
  
 3. Volání [CMFCMaskedEdit::SetValidChars](#setvalidchars) metoda zadat seznam platné znaky.  
  
 4. Volání [CMFCMaskedEdit::SetWindowText](#setwindowtext) metodu zadat výchozí text maskované ovládacích prvků pro úpravy.  
  
 5. Volání [CMFCMaskedEdit::GetWindowText](#getwindowtext) metodu za účelem načtení ověřené textu.  
  
 Pokud Nevolejte jedné nebo několika metod k chybě při inicializaci maska, platné znaky a výchozí text, ovládací prvek maskované pole se chová stejně jako chová standardní textové pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit masku (například telefonní číslo) pomocí `EnableMask` metodu pro vytvoření maska pro maskovaný ovládací prvky, upravovat `SetValidChars` zadat řetězec platné znaky, které můžete zadat uživatele a –Metoda`SetWindowText` metodu pro zobrazení na řádku v maskované ovládacích prvků pro úpravy. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmaskededit.h  
  
##  <a name="disablemask"></a>CMFCMaskedEdit::DisableMask  
 Zakáže ověřování uživatelského vstupu.  
  
```  
void DisableMask();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je zakázáno ověřování vstupu uživatele, se chová jako standardní ovládacích prvků pro úpravy maskované textové pole.  
  
##  <a name="enablegetmaskedcharsonly"></a>CMFCMaskedEdit::EnableGetMaskedCharsOnly  
 Určuje, zda `GetWindowText` metoda načte pouze maskované znaky.  
  
```  
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`Chcete-li určit, že [CMFCMaskedEdit::GetWindowText](#getwindowtext) metoda načíst pouze maskovat znaků; `FALSE` k určení, že metoda načíst celý text. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li povolit načítání maskované znaků. Pak vytvořte maskované textové pole, která odpovídá telefonní číslo, například (425) 555-0187. Když zavoláte `GetWindowText` metoda, vrátí "4255550187". Pokud zakážete načítání maskované znaky, `GetWindowText` metoda vrátí text, který se zobrazí v ovládacím prvku upravit, například "(425) 555-0187".  
  
##  <a name="enablemask"></a>CMFCMaskedEdit::EnableMask  
 Inicializuje maskované ovládacích prvků pro úpravy.  
  
```  
void EnableMask(
    LPCTSTR lpszMask,  
    LPCTSTR lpszInputTemplate,  
    TCHAR chMaskInputTemplate=_T('_'),  
    LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszMask`  
 Maska řetězec, který určuje typ znak, který může vyskytovat na každý pozici v vstupu uživatele. Délka `lpszInputTemplate` a `lpszMask` parametr řetězce musí být stejné. Najdete v části poznámky pro více podrobností o maska znaků.  
  
 [v]`lpszInputTemplate`  
 Řetězec masky šablony, která určuje, že je literál znaků, který se může zobrazit na každý pozici v vstupu uživatele. Použijte znak podtržítka (_) jako zástupný znak. Délka `lpszInputTemplate` a `lpszMask` parametr řetězce musí být stejné.  
  
 [v]`chMaskInputTemplate`  
 Výchozí znak, který nahradí název rozhraní pro každý neplatný znak v vstupu uživatele. Výchozí hodnota tohoto parametru je podtržítko (_).  
  
 [v]`lpszValid`  
 Řetězec, který obsahuje sadu platné znaky. `NULL`Určuje, zda jsou všechny znaky platné. Výchozí hodnota tohoto parametru je `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k vytvoření masky pro ovládací prvek maskované pole. Odvození třídy z `CMFCMaskedEdit` třídy a přepsat [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) metody vlastní kód pro zpracování vlastní masky.  
  
 V následující tabulce je seznam výchozích maska znaků:  
  
|Znak masky|Definice|  
|--------------------|----------------|  
|D|Číslice.|  
|d|Číslice nebo mezera.|  
|+|Plus ('+ '), minus ('-'), nebo místo.|  
|C|Znak abecedy.|  
|c|Znak abecedy nebo místa.|  
|OBJEKT|Alfanumerický znak.|  
|A|Alfanumerický znak nebo místa.|  
|*|Tisknutelná znak.|  
  
##  <a name="enableselectbygroup"></a>CMFCMaskedEdit::EnableSelectByGroup  
 Určuje, zda ovládací prvek maskované pole umožňuje uživateli vyberte konkrétní skupiny vstup nebo všechny vstupy.  
  
```  
void EnableSelectByGroup(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`Chcete-li vybrat jenom skupiny; `FALSE` vyberte celý text. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete určit, zda ovládací prvek maskované pole umožňuje uživateli vybrat podle skupiny nebo celý text.  
  
 Ve výchozím nastavení je povolen výběr skupinou. V takovém případě může uživatel vybrat pouze souvislé skupiny platné znaky.  
  
 Například můžete použít následující ovládací prvek maskované pole ověření telefonní číslo:  
  
 `m_wndMaskEdit.EnableMask(`  
  
 `_T(" ddd  ddd dddd"),// Mask string`  
  
 `_T("(___) ___-____"),// Template string`  
  
 `_T(' '));// Default char`  
  
 `m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.`  
  
 `m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt`  
  
 Pokud je povolen výběr skupinou, uživatel může načíst jenom "425", "555" nebo "0187" řetězec skupiny. Pokud je zakázána výběr skupiny uživatele můžete načíst celý text telefonní číslo: "(425) 555-0187".  
  
##  <a name="enablesetmaskedcharsonly"></a>CMFCMaskedEdit::EnableSetMaskedCharsOnly  
 Určuje, zda je text ověřit před pouze maskované znaky, nebo celý maska.  
  
```  
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`k ověření uživatele vstup podle dokumentu pouze maskovat znaků; `FALSE` ověření oproti celou maska. Výchozí hodnota je `TRUE`.  
  
##  <a name="getwindowtext"></a>CMFCMaskedEdit::GetWindowText  
 Načte ověřit text z maskované textové pole.  
  
```  
int GetWindowText(
    LPTSTR lpszStringBuf,  
    int nMaxCount) const;  
  
void GetWindowText(CString& rstrString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`lpszStringBuf`  
 Ukazatel na vyrovnávací paměť, která obdrží text z ovládacího prvku úprav.  
  
 [v]`nMaxCount`  
 Maximální počet znaků pro příjem.  
  
 [out]`rstrString`  
 Odkaz na objekt řetězce, který přijme text z ovládacího prvku úprav.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet bajtů řetězce, který se zkopíruje na první přetížení metody `lpszStringBuf` parametr vyrovnávací paměti; 0, pokud má ovládací prvek maskované pole žádný text.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zkopíruje text z maskované textové pole na `lpszStringBuf` vyrovnávací paměti nebo `rstrString` řetězec.  
  
 Tato metoda znovu definuje [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).  
  
##  <a name="ismaskedchar"></a>CMFCMaskedEdit::IsMaskedChar  
 Voláno rámcem k ověření je zadaný znak proti odpovídající znak masky.  
  
```  
virtual BOOL IsMaskedChar(
    TCHAR chChar,  
    TCHAR chMaskChar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`chChar`  
 Znak, který má být ověřen.  
  
 [v]`chMaskChar`  
 Odpovídající znak z řetězec masky.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud `chChar` parametr je typ znaku povoleného `chMaskChar` parametr, jinak hodnota `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu pro ověření vstupu znaků sami. Další informace o znaky masky najdete v tématu [CMFCMaskedEdit::EnableMask](#enablemask) metoda.  
  
##  <a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars  
 Určuje řetězec platné znaky, které může uživatel zadat.  
  
```  
void SetValidChars(LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszValid`  
 Řetězec, který obsahuje sadu platné vstupní znaky. `NULL`znamená, že jsou platné všechny znaky. Výchozí hodnota tohoto parametru je `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k definování seznam platné znaky. Pokud vstupní znak není v tomto seznamu, nebudou jejich přijetí maskované textové pole.  
  
 Následující příklad kódu je možné zadat pouze hexadecimální číslice.  
  
 `//Mask: 0xFFFFm_wndMaskEdit.EnableMask( _T(" AAAA"),                // The mask string. _T("0x____"),               // The literal template string. _T('_'));                   // The default character that replaces the backspace character.// Valid string charactersm_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));`  
  
##  <a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText  
 Zobrazí výzvu v maskované textové pole.  
  
```  
void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszString`  
 Odkazuje na řetězec ukončené hodnotou null, který se použije jako výzvu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví ovládací prvek text.  
  
 Tato metoda znovu definuje [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)
