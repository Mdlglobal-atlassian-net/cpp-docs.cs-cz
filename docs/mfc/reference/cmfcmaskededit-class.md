---
title: CMFCMaskedEdit – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 26617f10605fe2a8a94adcc477cccab7e2ba4919
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754224"
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit – třída

Třída `CMFCMaskedEdit` podporuje maskovaný ovládací prvek úprav, který ověřuje vstup uživatele proti masce a zobrazuje ověřené výsledky podle šablony.

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
|[CMFCMaskedEdit::DisableMask](#disablemask)|Zakáže ověřování vstupu uživatele.|
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Určuje, zda `GetWindowText` metoda načte pouze maskované znaky.|
|[CMFCMaskedEdit::EnableMask](#enablemask)|Inicializuje maskovaný ovládací prvek úprav.|
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Určuje, zda maskovaný ovládací prvek pro úpravy vybere určité skupiny vstupu uživatele nebo všechny vstupy uživatele.|
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Určuje, zda je text ověřen pouze proti maskovaným znakům nebo proti celé masce.|
|`CMFCMaskedEdit::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Načte ověřený text z maskovaného ovládacího prvku úprav.|
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Určuje řetězec platných znaků, který může uživatel zadat.|
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Zobrazí výzvu v ovládacím prvku maskovaných úprav.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Volat rámci k ověření zadaný znak proti odpovídající znak masky.|

## <a name="remarks"></a>Poznámky

Chcete-li použít ovládací `CMFCMaskedEdit` prvek v aplikaci, postupujte podle následujících kroků:

1. Vložte `CMFCMaskedEdit` objekt do třídy okna.

2. Volání [CMFCMaskedEdit::EnableMask](#enablemask) metoda určit masku.

3. Volání [CMFCMaskedEdit::SetValidChars](#setvalidchars) metoda určit seznam platných znaků.

4. Volání [METODY CMFCMaskedEdit::SetWindowText](#setwindowtext) určete výchozí text pro maskovaný ovládací prvek úprav.

5. Volání [CMFCMaskedEdit::GetWindowText](#getwindowtext) metoda načíst ověřený text.

Pokud nezavoláte jednu nebo více metod pro inicializaci masky, platných znaků a výchozího textu, maskovaný ovládací prvek úprav se chová stejně jako standardní ovládací prvek úprav.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit masku (například telefonní číslo) pomocí `EnableMask` metody k vytvoření masky `SetValidChars` pro maskovaný ovládací prvek úprav, metodu `SetWindowText` pro určení řetězce platných znaků, který může uživatel zadat, a metodu zobrazení výzvy v maskovaném ovládacím prvku úprav. Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CEditovat](../../mfc/reference/cedit-class.md)

[CMFCMaskedEditovat](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmaskededit.h

## <a name="cmfcmaskededitdisablemask"></a><a name="disablemask"></a>CMFCMaskedEdit::DisableMask

Zakáže ověřování vstupu uživatele.

```cpp
void DisableMask();
```

### <a name="remarks"></a>Poznámky

Pokud je ověření vstupu uživatele zakázáno, maskovaný ovládací prvek úprav se chová jako standardní ovládací prvek úprav.

## <a name="cmfcmaskededitenablegetmaskedcharsonly"></a><a name="enablegetmaskedcharsonly"></a>CMFCMaskedEdit::EnableGetMaskedCharsOnly

Určuje, zda `GetWindowText` metoda načte pouze maskované znaky.

```cpp
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE určit, že [CMFCMaskedEdit::GetWindowText](#getwindowtext) metoda načíst pouze maskované znaky; FALSE určit, že metoda načíst celý text. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k povolení načítání maskovaných znaků. Potom vytvořte maskovaný ovládací prvek pro úpravy, který odpovídá telefonnímu číslu, například (425) 555-0187. Pokud zavoláte `GetWindowText` metodu, vrátí "4255550187". Pokud zakážete načítání maskovaných znaků, `GetWindowText` metoda vrátí text, který je zobrazen v ovládacím prvku úprav, například "(425) 555-0187".

## <a name="cmfcmaskededitenablemask"></a><a name="enablemask"></a>CMFCMaskedEdit::EnableMask

Inicializuje maskovaný ovládací prvek úprav.

```cpp
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parametry

*lpszMask*<br/>
[v] Řetězec masky, který určuje typ znaku, který se může objevit na každé pozici v uživatelském vstupu. Délka *lpszInputTemplate* a *lpszMask* parametr řetězce musí být stejné. Další podrobnosti o znacích masky naleznete v části Poznámky.

*lpszInputTemplate*<br/>
[v] Řetězec šablony masky, který určuje literál znaky, které se mohou objevit na každé pozici v vstupu uživatele. Použijte znak podtržítka ('_') jako zástupný symbol znaku. Délka *lpszInputTemplate* a *lpszMask* parametr řetězce musí být stejné.

*chMaskInputTemplate*<br/>
[v] Výchozí znak, který rozhraní nahradí každý neplatný znak v vstupu uživatele. Výchozí hodnota tohoto parametru je podtržítko ('_').

*lpszValid*<br/>
[v] Řetězec, který obsahuje sadu platných znaků. Hodnota NULL označuje, že všechny znaky jsou platné. Výchozí hodnota tohoto parametru je NULL.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k vytvoření masky pro maskovaný ovládací prvek úprav. Odvodit `CMFCMaskedEdit` třídu z třídy a přepsat [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) metoda použít vlastní kód pro vlastní zpracování masky.

V následující tabulce jsou uvedeny výchozí znaky masky:

|Znak masky|Definice|
|--------------------|----------------|
|D|Číslice.|
|d|Číslice nebo mezera.|
|+|Plus ('+'), mínus ('-') nebo mezera.|
|C|Abecední charakter.|
|c|Abecední znak nebo mezera.|
|A|Alfanumerický znak.|
|a|Alfanumerický znak nebo mezera.|
|*|Tisknutelný znak.|

## <a name="cmfcmaskededitenableselectbygroup"></a><a name="enableselectbygroup"></a>CMFCMaskedEdit::EnableSelectByGroup

Určuje, zda maskovaný ovládací prvek úprav umožňuje uživateli vybrat konkrétní vstup skupin nebo všechny vstupy.

```cpp
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] PRAVDA pro výběr pouze skupin; NEPRAVDA pro výběr celého textu. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k určení, zda maskovaný ovládací prvek úprav umožňuje uživateli vybrat podle skupiny nebo celého textu.

Ve výchozím nastavení je výběr podle skupin povolen. V tomto případě může uživatel vybrat pouze souvislé skupiny platných znaků.

Můžete například použít následující maskovaný ovládací prvek pro úpravy k ověření telefonního čísla:

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

Pokud je povolen výběr podle skupiny, uživatel může načíst pouze skupiny řetězců "425", "555" nebo "0187". Pokud je výběr skupiny zakázán, může uživatel načíst celý text telefonního čísla: "(425) 555-0187".

## <a name="cmfcmaskededitenablesetmaskedcharsonly"></a><a name="enablesetmaskedcharsonly"></a>CMFCMaskedEdit::EnableSetMaskedCharsOnly

Určuje, zda je text ověřen pouze proti maskovaným znakům nebo proti celé masce.

```cpp
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE pro ověření vstupu uživatele pouze proti maskovaným znakům; FALSE ověřit proti celé masky. Výchozí hodnota je TRUE.

## <a name="cmfcmaskededitgetwindowtext"></a><a name="getwindowtext"></a>CMFCMaskedEdit::GetWindowText

Načte ověřený text z maskovaného ovládacího prvku úprav.

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>Parametry

*lpszStringBuf*<br/>
[out] Ukazatel na vyrovnávací paměť, která obdrží text z ovládacího prvku upravit.

*nMaxCount*<br/>
[v] Maximální počet znaků, které mají být přijímat.

*rstrString*<br/>
[out] Odkaz na objekt řetězce, který přijímá text z ovládacího prvku upravit.

### <a name="return-value"></a>Návratová hodnota

První metoda přetížení vrátí počet bajtů řetězce, který je zkopírován do vyrovnávací paměti parametru *lpszStringBuf;* 0, pokud maskovaný ovládací prvek úprav nemá žádný text.

### <a name="remarks"></a>Poznámky

Tato metoda zkopíruje text z maskovaného ovládacího prvku pro úpravy do vyrovnávací paměti *lpszStringBuf* nebo řetězce *rstrString.*

Tato metoda předefinuje [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).

## <a name="cmfcmaskededitismaskedchar"></a><a name="ismaskedchar"></a>CMFCMaskedEdit::IsMaskedChar

Volat rámci k ověření zadaný znak proti odpovídající znak masky.

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>Parametry

*chChar*<br/>
[v] Znak, který má být ověřen.

*chMaskChar*<br/>
[v] Odpovídající znak z řetězce masky.

### <a name="return-value"></a>Návratová hodnota

TRUE Pokud je parametr *chChar* typ znaku povolený parametrem *chMaskChar;* jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu ověřit vstupní znaky na vlastní pěst. Další informace o znacích masky naleznete v metodě [CMFCMaskedEdit::EnableMask.](#enablemask)

## <a name="cmfcmaskededitsetvalidchars"></a><a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars

Určuje řetězec platných znaků, který může uživatel zadat.

```cpp
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parametry

*lpszValid*<br/>
[v] Řetězec, který obsahuje sadu platných vstupních znaků. Null znamená, že všechny znaky jsou platné. Výchozí hodnota tohoto parametru je NULL.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k definování seznamu platných znaků. Pokud vstupní znak není v tomto seznamu, maskovaný ovládací prvek úprav jej nepřijme.

Následující příklad kódu přijímá pouze šestnáctková čísla.

```cpp
//Mask: 0xFFFF
m_wndMaskEdit.EnableMask(
    _T(" AAAA"),                // The mask string.
    _T("0x____"),               // The literal template string.
    _T('_'));                   // The default character that
                                // replaces the backspace character.
// Valid string characters
m_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));
```

## <a name="cmfcmaskededitsetwindowtext"></a><a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText

Zobrazí výzvu v ovládacím prvku maskovaných úprav.

```cpp
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
[v] Odkazuje na řetězec ukončený hodnotou null, který bude použit jako výzva.

### <a name="remarks"></a>Poznámky

Tato metoda nastaví text ovládacího prvku.

Tato metoda předefinuje [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)
