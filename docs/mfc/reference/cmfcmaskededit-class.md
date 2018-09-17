---
title: Cmfcmaskededit – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0bb29fdaff72370ec197fc9b3f651b5ff574c32
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717428"
---
# <a name="cmfcmaskededit-class"></a>Cmfcmaskededit – třída
`CMFCMaskedEdit` Třída podporuje maskovaného ovládacího prvku, který ověřuje vstup uživatele v porovnání s maskou a zobrazí ověřené výsledky podle šablony.  
  
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
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Určuje, zda `GetWindowText` metoda načte pouze maskované znaků.|  
|[CMFCMaskedEdit::EnableMask](#enablemask)|Inicializuje maskované ovládacích prvků pro úpravy.|  
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Určuje, zda maskované textové pole vybere konkrétní skupiny uživatelský vstup nebo vstup všechny uživatele.|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Určuje, zda text je ověřen vůči jen maskované znaků, nebo proti celý masky.|  
|`CMFCMaskedEdit::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|  
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Načte ověřit text z maskované textové pole.|  
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Určuje řetězec platné znaky, které může uživatel zadat.|  
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Zobrazí příkazový řádek v maskované textové pole.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Volá se rozhraním pro ověření zadaného znaku podle odpovídajícího znaku masky.|  
  
## <a name="remarks"></a>Poznámky  
 Proveďte následující kroky a použít `CMFCMaskedEdit` ovládací prvek ve vaší aplikaci:  
  
 1. Vložit `CMFCMaskedEdit` objektu do vaší třídy okna.  
  
 2. Volání [CMFCMaskedEdit::EnableMask](#enablemask) metody zadejte masku.  
  
 3. Volání [CMFCMaskedEdit::SetValidChars](#setvalidchars) metoda určení seznamu platné znaky.  
  
 4. Volání [CMFCMaskedEdit::SetWindowText](#setwindowtext) metodu pro určení výchozí text maskovaný ovládací prvek textové pole.  
  
 5. Volání [CMFCMaskedEdit::GetWindowText](#getwindowtext) metody k získání ověřeného text.  
  
 Pokud nebude volat jednu nebo více metod se inicializovat maska, platné znaky a výchozí text, maskované textové pole se chová stejně jako standardní textovém poli se chová.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit masku (například telefonní číslo) pomocí `EnableMask` metodu pro vytvoření maska pro maskované upravit ovládací prvek, `SetValidChars` metoda zadat řetězec platné znaky, které může uživatel zadat a `SetWindowText` metodu pro zobrazení výzvy v maskovaný ovládací prvek textové pole. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cedit –](../../mfc/reference/cedit-class.md)  
  
 [Cmfcmaskededit –](../../mfc/reference/cmfcmaskededit-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmaskededit.h  
  
##  <a name="disablemask"></a>  CMFCMaskedEdit::DisableMask  
 Zakáže ověřování uživatelského vstupu.  
  
```  
void DisableMask();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je zakázané ověřování uživatelského vstupu, maskované textové pole se chová jako standardní ovládací prvek textové pole.  
  
##  <a name="enablegetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableGetMaskedCharsOnly  
 Určuje, zda `GetWindowText` metoda načte pouze maskované znaků.  
  
```  
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bEnable*<br/>
[in] PRAVDA, pokud chcete určit, že [CMFCMaskedEdit::GetWindowText](#getwindowtext) metodu načtení pouze maskované znaků. FALSE, pokud chcete určit, že metodu načtení celého textu. Výchozí hodnota je TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete povolit načítání maskované znaků. Pak vytvořte maskované textové pole, která odpovídá telefonní číslo, například (425) 555-0187. Při volání `GetWindowText` metody, vrátí "4255550187". Pokud zakážete načítání maskované znaků `GetWindowText` metoda vrací text, který se zobrazí v textovém poli, například "(425) 555-0187".  
  
##  <a name="enablemask"></a>  CMFCMaskedEdit::EnableMask  
 Inicializuje maskované ovládacích prvků pro úpravy.  
  
```  
void EnableMask(
    LPCTSTR lpszMask,  
    LPCTSTR lpszInputTemplate,  
    TCHAR chMaskInputTemplate=_T('_'),  
    LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Parametry  
*lpszMask*<br/>
[in] Maska řetězec, který určuje typ znaku, který se může zobrazit na každou pozici v vstupu uživatele. Délka *lpszInputTemplate* a *lpszMask* parametr řetězce musí být stejné. Další podrobnosti o znaky masky v části poznámky.  
  
*lpszInputTemplate*<br/>
[in] Řetězec masky šablony, která určuje, že je literál znaků, které se může zobrazit na každé pozici ve vstupu uživatele. Použijte znak podtržítka ("_") jako zástupný znak. Délka *lpszInputTemplate* a *lpszMask* parametr řetězce musí být stejné.  
  
*chMaskInputTemplate*<br/>
[in] Výchozí znak, který rozhraní provede nahrazení pro každý neplatný znak v vstupu uživatele. Výchozí hodnota tohoto parametru je podtržítko (_).  
  
*lpszValid*<br/>
[in] Řetězec, který obsahuje sadu platných znaků. Hodnota NULL označuje, že jsou všechny znaky platné. Výchozí hodnota tohoto parametru je NULL.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete vytvořit maska maskované textové pole. Odvodit třídu z `CMFCMaskedEdit` třídy a přepsat [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) metodu použít vlastní kód pro zpracování vlastní masku.  
  
 V následující tabulce seznamu výchozích maska znaků:  
  
|Znak masky|Definice|  
|--------------------|----------------|  
|D|Číslice.|  
|d|Číslice nebo mezera.|  
|+|Plus ('+ '), minus ("-"), nebo místo.|  
|C|Abecední znak.|  
|c|Abecední znak nebo znak.|  
|OBJEKT|Alfanumerický znak.|  
|a|Alfanumerický znak nebo znak.|  
|*|Tisknutelný znak.|  
  
##  <a name="enableselectbygroup"></a>  CMFCMaskedEdit::EnableSelectByGroup  
 Určuje, zda maskované textové pole umožňuje uživateli vybrat konkrétní skupiny vstup nebo všechny vstupy.  
  
```  
void EnableSelectByGroup(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bEnable*<br/>
[in] TRUE, pokud chcete vybrat jenom skupiny. FALSE, pokud chcete vybrat celý text. Výchozí hodnota je TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci použijte k určení, zda maskované textové pole umožňuje uživateli vybrat podle skupiny nebo celého textu.  
  
 Ve výchozím nastavení je povolen výběr podle skupiny. V tomto případě může uživatel vybrat pouze průběžné skupiny platné znaky.  
  
 Například můžete použít následující maskované textové pole pro ověření telefonní číslo:  
  
 `m_wndMaskEdit.EnableMask(`  
  
 `_T(" ddd  ddd dddd"),// Mask string`  
  
 `_T("(___) ___-____"),// Template string`  
  
 `_T(' '));// Default char`  
  
 `m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.`  
  
 `m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt`  
  
 Pokud je povolen výběr podle skupiny, uživatel může načíst pouze "425", "555" nebo "0187" řetězec skupiny. Pokud je výběr skupiny zakázaný uživatel může načíst celý text telefonní číslo: "(425) 555-0187".  
  
##  <a name="enablesetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableSetMaskedCharsOnly  
 Určuje, zda text ověření před pouze maskované znaků, nebo celé masky.  
  
```  
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bEnable*<br/>
[in] TRUE, pokud chcete ověřit uživatele zadejte proti jen maskované znaků. FALSE, pokud chcete ověřovat proti celý masky. Výchozí hodnota je TRUE.  
  
##  <a name="getwindowtext"></a>  CMFCMaskedEdit::GetWindowText  
 Načte ověřit text z maskované textové pole.  
  
```  
int GetWindowText(
    LPTSTR lpszStringBuf,  
    int nMaxCount) const;  
  
void GetWindowText(CString& rstrString) const;  
```  
  
### <a name="parameters"></a>Parametry  
*lpszStringBuf*<br/>
[out] Ukazatel do vyrovnávací paměti, která přijímá text z ovládacího prvku pro úpravy.  
  
*nMaxCount*<br/>
[in] Maximální počet znaků pro příjem.  
  
*rstrString*<br/>
[out] Odkaz na objekt řetězce, která přijímá text z ovládacího prvku pro úpravy.  
  
### <a name="return-value"></a>Návratová hodnota  
 První přetížení metody vrátí počet bajtů na řetězec, který se zkopíruje do *lpszStringBuf* parametr vyrovnávací paměti; 0, pokud maskované textové pole nemá žádný text.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda kopíruje text z maskované textové pole na *lpszStringBuf* vyrovnávací paměti nebo *rstrString* řetězec.  
  
 Tato metoda předefinuje [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).  
  
##  <a name="ismaskedchar"></a>  CMFCMaskedEdit::IsMaskedChar  
 Volá se rozhraním pro ověření zadaného znaku podle odpovídajícího znaku masky.  
  
```  
virtual BOOL IsMaskedChar(
    TCHAR chChar,  
    TCHAR chMaskChar) const;  
```  
  
### <a name="parameters"></a>Parametry  
*chChar*<br/>
[in] Znak, který má být ověřen.  
  
*chMaskChar*<br/>
[in] Na odpovídající znak z řetězec masky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud *chChar* je parametr typu znak povoleném *chMaskChar* parametr; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu za účelem ověření vstupních znaků vlastními silami. Další informace o znacích maska, najdete v článku [CMFCMaskedEdit::EnableMask](#enablemask) metody.  
  
##  <a name="setvalidchars"></a>  CMFCMaskedEdit::SetValidChars  
 Určuje řetězec platné znaky, které může uživatel zadat.  
  
```  
void SetValidChars(LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Parametry  
*lpszValid*<br/>
[in] Řetězec, který obsahuje sadu platných vstupních znaků. Hodnota NULL znamená, že jsou všechny znaky platné. Výchozí hodnota tohoto parametru je NULL.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete definovat seznam platné znaky. Pokud vstupní znak není v tomto seznamu, ovládacího prvku pro editování nepřijme.  
  
 Následující příklad kódu přijímá pouze šestnáctkové číslice.  
  
 `//Mask: 0xFFFFm_wndMaskEdit.EnableMask( _T(" AAAA"),                // The mask string. _T("0x____"),               // The literal template string. _T('_'));                   // The default character that replaces the backspace character.// Valid string charactersm_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));`  
  
##  <a name="setwindowtext"></a>  CMFCMaskedEdit::SetWindowText  
 Zobrazí příkazový řádek v maskované textové pole.  
  
```  
void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
*lpszString*<br/>
[in] Odkazuje na řetězec zakončený hodnotou null, který se použije příkazovém řádku.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví text ovládacího prvku.  
  
 Tato metoda předefinuje [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)
