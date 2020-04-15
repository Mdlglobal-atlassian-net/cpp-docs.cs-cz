---
title: Třída CMFCRibbonComboBox
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
ms.openlocfilehash: 5846b1c5590a756f0a0820583af3d0b159968ea2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375230"
---
# <a name="cmfcribboncombobox-class"></a>Třída CMFCRibbonComboBox

Třída `CMFCRibbonComboBox` implementuje ovládací prvek pole se seznamem, který můžete přidat na panel pásu karet, panel pásu karet nebo místní nabídku pásu karet.

## <a name="syntax"></a>Syntaxe

```cpp
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Vytvoří objekt CMFCRibbonComboBox.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonComboBox::Přidatpoložku](#additem)|Připojí jedinečnou položku do seznamu.|
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Odstraní zadanou položku ze seznamu.|
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Určuje, zda může seznam změnit velikost, když klesne dolů.|
|[CMFCRibbonComboBox::FindItem](#finditem)|Vrátí index první položky v seznamu, který odpovídá zadanému řetězci.|
|[CMFCRibbonComboBox::GetCount](#getcount)|Vrátí počet položek v seznamu.|
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Získá index aktuálně vybrané položky v seznamu.|
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Získá výšku seznamu při seznamu je spadl dolů.|
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Vrátí velikost pole se seznamem zobrazenou v mezilehlém režimu.|
|[CMFCRibbonComboBox::GetItem](#getitem)|Vrátí řetězec přidružený k položce v zadaném indexu v seznamu.|
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Vrátí data přidružená k položce v zadaném indexu v seznamu.|
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Označuje, zda ovládací prvek obsahuje textové pole.|
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Označuje, zda lze velikost seznamu velikost i v seznamu.|
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Volat rámci při uživatel vybere položku v seznamu.|
|[CMFCRibbonComboBox::Odstranitvšechny položky](#removeallitems)|Odstraní všechny položky ze seznamu a vymaže pole pro úpravy.|
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Vybere položku v seznamu.|
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Nastaví výšku seznamu, když je spadl dolů.|

## <a name="remarks"></a>Poznámky

Pole se seznamem na pásu karet se skládá ze seznamu v kombinaci se statickým popiskem nebo popiskem, který může uživatel upravovat. Při vytváření pole se seznamem na pásu karet je nutné určit, který typ chcete zadat.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonComboBox` třídy, přidat položku do pole se seznamem, vybrat položku v poli se seznamem a přidat pole se seznamem do panelu.

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbon](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribboncombobox.h

## <a name="cmfcribboncomboboxadditem"></a><a name="additem"></a>CMFCRibbonComboBox::Přidatpoložku

Připojí jedinečnou položku do seznamu.

```cpp
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszPoložka*<br/>
[v] Řetězec položky, kterou chcete přidat.

*dwData*<br/>
[v] Data přidružená k položce, kterou chcete přidat.

### <a name="return-value"></a>Návratová hodnota

Nulový index připojené položky.

## <a name="cmfcribboncomboboxcmfcribboncombobox"></a><a name="cmfcribboncombobox"></a>CMFCRibbonComboBox::CMFCRibbonComboBox

Vytvoří `CMFCRibbonComboBox` objekt.

```cpp
public:
CMFCRibbonComboBox(
    UINT nID,
    BOOL bHasEditBox=TRUE,
    Int nWidth=-1,
    LPCTSTR lpszLabel=NULL,
    Int nImage=-1);

protected:
CMFCRibbonComboBox();
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] ID pole se seznamem.

*bHasEditBox*<br/>
[v] TRUE, pokud chcete upravit pole v ovládacím prvku; FALSE jinak.

*nŠířka*<br/>
[v] Šířka pole se seznamem v pixelech; nebo -1 pro výchozí šířku.

*popisek lpsz*<br/>
[v] Popisek displeje pole se seznamem.

*nObrázek*<br/>
[v] Malý index obrázku pole se seznamem.

### <a name="remarks"></a>Poznámky

Výchozí šířka je 108 pixelů.

## <a name="cmfcribboncomboboxdeleteitem"></a><a name="deleteitem"></a>CMFCRibbonComboBox::DeleteItem

Odstraní zadanou položku ze seznamu.

```cpp
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Index na základě nuly položky, která má být odstraněna.

*dwData*<br/>
[v] Data přidružená k položce, která má být odstraněna.

*lpszText*<br/>
[v] Řetězec položky, která má být odstraněna. Pokud existuje více položek se stejným řetězcem, první položka je odstraněna.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla zadaná položka odstraněna; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncomboboxenabledropdownlistresize"></a><a name="enabledropdownlistresize"></a>CMFCRibbonComboBox::EnableDropDownListResize

Určuje, zda může seznam změnit velikost, když klesne dolů.

```cpp
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE pro povolení změna velikosti; NEPRAVDA pro zakázání velikosti.

### <a name="remarks"></a>Poznámky

Pokud je změna velikosti povolena, změní se v seznamu velikost tak, aby odpovídala zobrazené položkám.

## <a name="cmfcribboncomboboxfinditem"></a><a name="finditem"></a>CMFCRibbonComboBox::FindItem

Vrátí index první položky v seznamu, který odpovídá zadanému řetězci.

```cpp
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[v] Řetězec položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Index na základě nuly položky; nebo -1, pokud položka není nalezena.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncomboboxgetcount"></a><a name="getcount"></a>CMFCRibbonComboBox::GetCount

Vrátí počet položek v seznamu.

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu nebo 0, pokud seznam neobsahuje žádné položky.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncomboboxgetcursel"></a><a name="getcursel"></a>CMFCRibbonComboBox::GetCurSel

Získá index aktuálně vybrané položky v seznamu.

```cpp
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Nulový index aktuálně vybrané položky v seznamu; nebo -1, pokud není vybrána žádná položka.

## <a name="cmfcribboncomboboxgetdropdownheight"></a><a name="getdropdownheight"></a>CMFCRibbonComboBox::GetDropDownHeight

Získá výšku seznamu při seznamu je spadl dolů.

```cpp
int GetDropDownHeight();
```

### <a name="return-value"></a>Návratová hodnota

Výška v pixelech seznamu.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncomboboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonComboBox::GetIntermediateSize

Vrátí velikost pole se seznamem zobrazenou v mezilehlém režimu.

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení pro pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Velikost pole se seznamem.

### <a name="remarks"></a>Poznámky

Vrácená velikost je založena na velikosti pole se seznamem, když zobrazuje malé obrázky.

## <a name="cmfcribboncomboboxgetitem"></a><a name="getitem"></a>CMFCRibbonComboBox::GetItem

Vrátí řetězec přidružený k položce v zadaném indexu v seznamu.

```cpp
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Nulový index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který je přidružen k položce; v opačném případě null, pokud je parametr indexu neplatný, nebo pokud je parametr indexu -1 a v poli se seznamem není vybrána žádná položka.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncomboboxgetitemdata"></a><a name="getitemdata"></a>CMFCRibbonComboBox::GetItemData

Vrátí data přidružená k položce v zadaném indexu v seznamu.

```cpp
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Nulový index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Data přidružená k položce; nebo 0, pokud položka neexistuje, nebo pokud je parametr indexu -1 a v seznamu není žádná vybraná položka.

## <a name="cmfcribboncomboboxhaseditbox"></a><a name="haseditbox"></a>CMFCRibbonComboBox::HasEditBox

Označuje, zda ovládací prvek obsahuje textové pole.

```cpp
BOOL HasEditBox() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud ovládací prvek obsahuje textové pole; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncomboboxisresizedropdownlist"></a><a name="isresizedropdownlist"></a>CMFCRibbonComboBox::IsResizeDropDownList

Označuje, zda lze velikost seznamu velikost i v seznamu.

```cpp
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud lze velikost seznamu velikost i v případě, že se velikost seznamu: jinak FALSE. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>Poznámky

Změna velikosti seznamu můžete povolit pomocí metody [CMFCRibbonComboBox::EnableDropDownListResize.](#enabledropdownlistresize)

## <a name="cmfcribboncomboboxonselectitem"></a><a name="onselectitem"></a>CMFCRibbonComboBox::OnSelectItem

Volat rámci při uživatel vybere položku v seznamu.

```cpp
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
[v] Index vybrané položky.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu, pokud chcete zpracovat výběr vstupu uživatele.

## <a name="cmfcribboncomboboxremoveallitems"></a><a name="removeallitems"></a>CMFCRibbonComboBox::Odstranitvšechny položky

Odstraní všechny položky ze seznamu a vymaže pole pro úpravy.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncomboboxselectitem"></a><a name="selectitem"></a>CMFCRibbonComboBox::SelectItem

Vybere položku v seznamu.

```cpp
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Nulový index položky v seznamu.

*dwData*<br/>
[v] Data přidružená k položce v seznamu.

*lpszText*<br/>
[v] Řetězec položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncomboboxsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCRibbonComboBox::SetDropDownHeight

Nastaví výšku seznamu, když je spadl dolů.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parametry

*nVýška*<br/>
[v] Výška v pixelech seznamu.

### <a name="remarks"></a>Poznámky

Výchozí výška je 150 pixelů.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CmFC, stuha na pásu karet](../../mfc/reference/cmfcribbonedit-class.md)
