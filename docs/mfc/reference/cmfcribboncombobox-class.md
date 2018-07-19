---
title: Cmfcribboncombobox – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: a2ccefbc435cac5b48cd2c9509831699dcec70af
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849666"
---
# <a name="cmfcribboncombobox-class"></a>Cmfcribboncombobox – třída
`CMFCRibbonComboBox` Třída implementuje ovládací prvek pole se seznamem, který lze přidat na panel pásu karet, panel pásu karet nebo nabídky pásu karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Vytvoří objekt cmfcribboncombobox –.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonComboBox::AddItem](#additem)|Připojí jedinečný položky pole se seznamem.|  
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Odstraní zadanou položku ze seznamu.|  
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Určuje, zda pole se seznamem můžete změnit velikost, když se rozbalí.|  
|[CMFCRibbonComboBox::FindItem](#finditem)|Vrátí index první položky v seznamu, který se shoduje se zadaným řetězcem.|  
|[CMFCRibbonComboBox::GetCount](#getcount)|Vrátí počet položek v seznamu.|  
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Získá index aktuálně vybrané položky v seznamu.|  
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Získává výšku objektu pole se seznamem, když se rozbalil pole se seznamem.|  
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Jak se zobrazuje v režimu zprostředkující vrátí velikost položky pole se seznamem.|  
|[CMFCRibbonComboBox::GetItem](#getitem)|Vrací řetězec přidružený k položce na zadaném indexu v seznamu.|  
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Vrátí data související s položkou v zadaném indexu v seznamu.|  
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Určuje, zda ovládací prvek obsahuje textové pole.|  
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Určuje, zda můžete změnit velikost pole se seznamem.|  
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Volá se rozhraním, když uživatel vybere položku v seznamu.|  
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Odstraní všechny položky ze seznamu a vymaže pole pro úpravy.|  
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Vybere položku v seznamu.|  
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Výška pole se seznamem nastaví, když se rozbalil.|  
  
## <a name="remarks"></a>Poznámky  
 Pole se seznamem pásu karet se skládá z pole se seznamem v kombinaci se statický popisek nebo popisek, který může být upraven uživatelem. Je nutné zadat typ chcete, aby při vytváření vašeho – pole se seznamem pásu karet.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonComboBox` třídy, přidejte položku do pole se seznamem, vyberte položku v poli se seznamem a přidejte pole se seznamem na panel.  
  
 [!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [Cmfcribbonbutton –](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [Cmfcribbonedit –](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [Cmfcribboncombobox –](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribboncombobox.h  
  
##  <a name="additem"></a>  CMFCRibbonComboBox::AddItem  
 Připojí jedinečný položky pole se seznamem.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszItem*  
 Řetězec položky pro přidání.  
  
 [in] *dwData*  
 Data přidružená k položka k přidání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule připojené položky.  
  
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
 [in] *nID*  
 ID pole se seznamem.  
  
 [in] *bHasEditBox*  
 Hodnota TRUE, pokud chcete, aby do textového pole v ovládacím prvku; FALSE v opačném případě.  
  
 [in] *nWidth*  
 Šířka v pixelech; pole se seznamem nebo -1 pro výchozí šířky.  
  
 [in] *lpszLabel*  
 Zobrazit popisek pole se seznamem.  
  
 [in] *nvybrán Nobrázek*  
 Malý obrázek indexu pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí šířka je 108 pixelů.  
  
##  <a name="deleteitem"></a>  CMFCRibbonComboBox::DeleteItem  
 Odstraní zadanou položku ze seznamu.  
  
```  
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Index založený na nule položka, která má být odstraněna.  
  
 [in] *dwData*  
 Data přidružená k položka, která má být odstraněna.  
  
 [in] *lpszText*  
 Řetězec položky, která má být odstraněna. Pokud existuje více položek s do jednoho řetězce, odstraní se první položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud zadaná položka je Odstraněná; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enabledropdownlistresize"></a>  CMFCRibbonComboBox::EnableDropDownListResize  
 Určuje, zda pole se seznamem můžete změnit velikost, když se rozbalí.  
  
```  
void EnableDropDownListResize(BOOL bEnable=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bEnable*  
 Pokud chcete povolit změnu velikosti; FALSE, pokud chcete zakázat změnu velikosti.  
  
### <a name="remarks"></a>Poznámky  
 Při změně velikosti je povoleno, bude pole se seznamem změnit velikost položkám, které se zobrazí.  
  
##  <a name="finditem"></a>  CMFCRibbonComboBox::FindItem  
 Vrátí index první položky v seznamu, který se shoduje se zadaným řetězcem.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszText*  
 Řetězec položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Z nuly vycházející index položky; nebo -1, pokud položka není nalezena.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcount"></a>  CMFCRibbonComboBox::GetCount  
 Vrátí počet položek v seznamu.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu, nebo 0, pokud neobsahuje žádné položky pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcursel"></a>  CMFCRibbonComboBox::GetCurSel  
 Získá index aktuálně vybrané položky v seznamu.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Z nuly vycházející index aktuálně vybrané položky v seznamu pole. nebo -1, pokud není vybrána žádná položka.  
  
##  <a name="getdropdownheight"></a>  CMFCRibbonComboBox::GetDropDownHeight  
 Získává výšku objektu pole se seznamem, když se rozbalil pole se seznamem.  
  
```  
int GetDropDownHeight();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška v pixelech, pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonComboBox::GetIntermediateSize  
 Jak se zobrazuje v režimu zprostředkující vrátí velikost položky pole se seznamem.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí velikost vychází z velikosti pole se seznamem poznat malé obrázky.  
  
##  <a name="getitem"></a>  CMFCRibbonComboBox::GetItem  
 Vrací řetězec přidružený k položce na zadaném indexu v seznamu.  
  
```  
LPCTSTR GetItem(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Index založený na nule položku v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec, který je přidružený k položce; v opačném případě hodnotu NULL, pokud parametr indexu je neplatný, nebo pokud je parametr indexu -1 a neexistuje žádná položka vybraná v poli se seznamem.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getitemdata"></a>  CMFCRibbonComboBox::GetItemData  
 Vrátí data související s položkou v zadaném indexu v seznamu.  
  
```  
DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Index založený na nule položku v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Data přidružená k položce; nebo 0. Pokud položka buď neexistuje, nebo pokud je parametr indexu -1 a v seznamu není vybrána žádná položka.  
  
##  <a name="haseditbox"></a>  CMFCRibbonComboBox::HasEditBox  
 Určuje, zda ovládací prvek obsahuje textové pole.  
  
```  
BOOL HasEditBox() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud ovládací prvek obsahuje textové pole; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isresizedropdownlist"></a>  CMFCRibbonComboBox::IsResizeDropDownList  
 Určuje, zda můžete změnit velikost pole se seznamem.  
  
```  
BOOL IsResizeDropDownList() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud se dá změnit pole se seznamem; v opačném případě FALSE. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)  
  
### <a name="remarks"></a>Poznámky  
 Můžete povolit seznam změny velikosti pomocí pole [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize) metody.  
  
##  <a name="onselectitem"></a>  CMFCRibbonComboBox::OnSelectItem  
 Volá se rozhraním, když uživatel vybere položku v seznamu.  
  
```  
virtual void OnSelectItem(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nItem*  
 Index vybrané položky.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, pokud chcete zpracovat výběr vstupu uživatele.  
  
##  <a name="removeallitems"></a>  CMFCRibbonComboBox::RemoveAllItems  
 Odstraní všechny položky ze seznamu a vymaže pole pro úpravy.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="selectitem"></a>  CMFCRibbonComboBox::SelectItem  
 Vybere položku v seznamu.  
  
```  
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Index založený na nule položku v seznamu.  
  
 [in] *dwData*  
 Data související s položkou v seznamu.  
  
 [in] *lpszText*  
 Řetězec položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda byla úspěšná. v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setdropdownheight"></a>  CMFCRibbonComboBox::SetDropDownHeight  
 Výška pole se seznamem nastaví, když se rozbalil.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nHeight*  
 Výška v pixelech, pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí výška je 150 pixelů.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonEdit – třída](../../mfc/reference/cmfcribbonedit-class.md)
