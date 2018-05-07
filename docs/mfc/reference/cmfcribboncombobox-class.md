---
title: Třída CMFCRibbonComboBox | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ebe013e8ce674efb0782112cc8cbc8b1462ef24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox – třída
`CMFCRibbonComboBox` Třída implementuje prvek pole se seznamem, který můžete přidat na panel pásu karet, panel pásu karet nebo místní nabídky pásu karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Vytvoří objekt CMFCRibbonComboBox.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonComboBox::AddItem](#additem)|Připojí položku jedinečný pro pole se seznamem.|  
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Odstraní určenou položku z pole se seznamem.|  
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Určuje, zda pole se seznamem můžete změnit velikost, když ho zahodí.|  
|[CMFCRibbonComboBox::FindItem](#finditem)|Vrátí index první položky v seznamu, který odpovídá určeného řetězce.|  
|[CMFCRibbonComboBox::GetCount](#getcount)|Vrátí počet položek v seznamu.|  
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Získá index aktuálně vybrané položky v seznamu.|  
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Získá výšku pole se seznamem při přetažení pole se seznamem.|  
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Vrátí velikost pole se seznamem, jak je uvedeno v zprostředkující režimu.|  
|[CMFCRibbonComboBox::GetItem](#getitem)|Vrátí řetězec přidružený k položku na zadaný index v poli seznamu.|  
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Vrací data související s položku na zadaný index v poli seznamu.|  
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Určuje, zda ovládací prvek obsahuje textové pole.|  
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Určuje, zda pole se seznamem velikost lze změnit.|  
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Voláno rámcem, když uživatel vybere položku v seznamu.|  
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Odstraní všechny položky ze seznamu a vymaže textové pole.|  
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Vyberte položku v seznamu.|  
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Výška pole se seznamem nastaví při umístění.|  
  
## <a name="remarks"></a>Poznámky  
 Pole se seznamem pásu karet se skládá z pole se seznamem kombinaci statických popisek nebo štítek, který může uživatel upravit. Musíte zadat typ, který chcete při vytváření vašeho – pole se seznamem pásu karet.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonComboBox` třídy, přidejte položku do pole se seznamem, vyberte položku v poli se seznamem a přidat pole se seznamem do panelu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribboncombobox.h  
  
##  <a name="additem"></a>  CMFCRibbonComboBox::AddItem  
 Připojí položku jedinečný pro pole se seznamem.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszItem`  
 Řetězec položka k přidání.  
  
 [v] `dwData`  
 Data přidružená k položce přidat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule připojením položky.  
  
##  <a name="cmfcribboncombobox"></a>  CMFCRibbonComboBox::CMFCRibbonComboBox  
 Vytvoří `CMFCRibbonComboBox` objektu.  
  
```  
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
 [v] `nID`  
 ID pole se seznamem.  
  
 [v] `bHasEditBox`  
 `TRUE` Pokud chcete, aby textové pole v rámci prvku; `FALSE` jinak.  
  
 [v] `nWidth`  
 Šířka pole se seznamem v pixelech; nebo -1 pro výchozí šířku.  
  
 [v] `lpszLabel`  
 Zobrazovaný název pole se seznamem.  
  
 [v] `nImage`  
 Malý obrázek indexu pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí šířku je 108 pixelů.  
  
##  <a name="deleteitem"></a>  CMFCRibbonComboBox::DeleteItem  
 Odstraní určenou položku z pole se seznamem.  
  
```  
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iIndex`  
 Index založený na nule položky pro odstranění.  
  
 [v] `dwData`  
 Data související s položka, která má být odstraněna.  
  
 [v] `lpszText`  
 Řetězec položka, která má být odstraněna. Pokud je vybráno více položek se do jednoho řetězce, je první položka odstraněna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud zadaná položka odstraněn. v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enabledropdownlistresize"></a>  CMFCRibbonComboBox::EnableDropDownListResize  
 Určuje, zda pole se seznamem můžete změnit velikost, když ho zahodí.  
  
```  
void EnableDropDownListResize(BOOL bEnable=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnable`  
 `TRUE` Chcete-li povolit změnu velikosti; `FALSE` zakázat, změnu velikosti.  
  
### <a name="remarks"></a>Poznámky  
 Při změně velikosti je povoleno, bude pole se seznamem změnit položky, které se zobrazí přizpůsobit velikost.  
  
##  <a name="finditem"></a>  CMFCRibbonComboBox::FindItem  
 Vrátí index první položky v seznamu, který odpovídá určeného řetězce.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszText`  
 Řetězec, položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule položky; nebo -1, pokud položka není nalezena.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcount"></a>  CMFCRibbonComboBox::GetCount  
 Vrátí počet položek v seznamu.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu, nebo 0, pokud seznam neobsahuje žádné položky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcursel"></a>  CMFCRibbonComboBox::GetCurSel  
 Získá index aktuálně vybrané položky v seznamu.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule aktuálně vybrané položky v seznamu; nebo -1, pokud není vybrána žádná položka.  
  
##  <a name="getdropdownheight"></a>  CMFCRibbonComboBox::GetDropDownHeight  
 Získá výšku pole se seznamem při přetažení pole se seznamem.  
  
```  
int GetDropDownHeight();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška v pixelech pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonComboBox::GetIntermediateSize  
 Vrátí velikost pole se seznamem, jak je uvedeno v zprostředkující režimu.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontext zařízení pro pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Velikost, vrátila je založena na velikosti pole se seznamem, když se zobrazí malé bitové kopie.  
  
##  <a name="getitem"></a>  CMFCRibbonComboBox::GetItem  
 Vrátí řetězec přidružený k položku na zadaný index v poli seznamu.  
  
```  
LPCTSTR GetItem(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iIndex`  
 Index založený na nule položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec, který je přidružená k položce; v opačném `NULL` Pokud parametr indexu je neplatná, nebo pokud je parametr indexu -1 a neexistuje žádná položka vybrané v poli se seznamem.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getitemdata"></a>  CMFCRibbonComboBox::GetItemData  
 Vrací data související s položku na zadaný index v poli seznamu.  
  
```  
DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iIndex`  
 Index založený na nule položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Data přidružená k položce; nebo 0. Pokud položka neexistuje, nebo pokud parametr indexu je -1 a v seznamu není vybrána žádná položka.  
  
##  <a name="haseditbox"></a>  CMFCRibbonComboBox::HasEditBox  
 Určuje, zda ovládací prvek obsahuje textové pole.  
  
```  
BOOL HasEditBox() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud ovládací prvek obsahuje textové pole; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isresizedropdownlist"></a>  CMFCRibbonComboBox::IsResizeDropDownList  
 Určuje, zda pole se seznamem velikost lze změnit.  
  
```  
BOOL IsResizeDropDownList() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud velikost pole se seznamem lze změnit; v opačném případě `FALSE`. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)  
  
### <a name="remarks"></a>Poznámky  
 Můžete povolit změnu velikosti pole seznamu pomocí [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize) metoda.  
  
##  <a name="onselectitem"></a>  CMFCRibbonComboBox::OnSelectItem  
 Voláno rámcem, když uživatel vybere položku v seznamu.  
  
```  
virtual void OnSelectItem(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nItem`  
 Index vybrané položky.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, pokud chcete zpracovat vstupní výběr uživatele.  
  
##  <a name="removeallitems"></a>  CMFCRibbonComboBox::RemoveAllItems  
 Odstraní všechny položky ze seznamu a vymaže textové pole.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="selectitem"></a>  CMFCRibbonComboBox::SelectItem  
 Vyberte položku v seznamu.  
  
```  
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iIndex`  
 Index založený na nule položky v seznamu.  
  
 [v] `dwData`  
 Data přidružená k položce v seznamu.  
  
 [v] `lpszText`  
 Řetězec, položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setdropdownheight"></a>  CMFCRibbonComboBox::SetDropDownHeight  
 Výška pole se seznamem nastaví při umístění.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nHeight`  
 Výška v pixelech pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Výška výchozí je 150 pixelů.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonEdit – třída](../../mfc/reference/cmfcribbonedit-class.md)
