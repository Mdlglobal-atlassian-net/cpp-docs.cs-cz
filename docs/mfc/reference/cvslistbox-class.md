---
title: CVSListBox – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
dev_langs:
- C++
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 946c82d4f558974d548a40af0b14e63f7ccebf4e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680577"
---
# <a name="cvslistbox-class"></a>CVSListBox – třída
`CVSListBox` Třída podporuje ovládací prvek upravovat seznam.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CVSListBox : public CVSListBoxBase  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CVSListBox::CVSListBox](#cvslistbox)|Vytvoří `CVSListBox` objektu.|  
|`CVSListBox::~CVSListBox`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CVSListBox::AddItem](#additem)|Přidá řetězec do ovládacího prvku seznamu. (Přepíše `CVSListBoxBase::AddItem`.)|  
|[CVSListBox::EditItem](#edititem)|Spustí operaci úprav na text ovládacího prvku položky seznamu. (Přepíše `CVSListBoxBase::EditItem`.)|  
|[CVSListBox::GetCount](#getcount)|Získá počet řetězců v ovládacím prvku upravovat seznam. (Přepíše `CVSListBoxBase::GetCount`.)|  
|[CVSListBox::GetItemData](#getitemdata)|Načte hodnotu 32-bit specifické pro aplikaci, která souvisí s položkou Přehled ovládacího prvku. (Přepíše `CVSListBoxBase::GetItemData`.)|  
|[CVSListBox::GetItemText](#getitemtext)|Načte text položky ovládacího prvku seznam upravovat. (Přepíše `CVSListBoxBase::GetItemText`.)|  
|[CVSListBox::GetSelItem](#getselitem)|Načte z nuly vycházející index aktuálně vybrané položky v ovládacím prvku upravovat seznam. (Přepíše `CVSListBoxBase::GetSelItem`.)|  
|`CVSListBox::PreTranslateMessage`|Přeloží okno zprávy před odesláním do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkce Windows. Další informace a syntaxe využívající metody, naleznete v tématu [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Přepíše `CVSListBoxBase::PreTranslateMessage`.)|  
|[CVSListBox::RemoveItem](#removeitem)|Odebere položku z ovládacího prvku seznam upravovat. (Přepíše `CVSListBoxBase::RemoveItem`.)|  
|[CVSListBox::SelectItem](#selectitem)|Vybere řetězci Přehled ovládacího prvku. (Přepíše `CVSListBoxBase::SelectItem`.)|  
|[CVSListBox::SetItemData](#setitemdata)|Přehled ovládacího prvku položky přidruží hodnotu 32-bit specifické pro aplikaci. (Přepíše `CVSListBoxBase::SetItemData`.)|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CVSListBox::GetListHwnd](#getlisthwnd)|Vrátí popisovač do aktuální ovládací prvek zobrazení seznamu embedded.|  
  
## <a name="remarks"></a>Poznámky  
 `CVSListBox` Třída poskytuje sadu tlačítek úpravy, který uživateli umožňuje vytvořit, upravit, odstranit nebo změnit pořadí položek v ovládacím prvku seznamu.  
  
 Níže je obrázek ovládacího prvku seznam upravovat. Druhá položka seznamu, který má název "Item2 –", je vybrán pro úpravy.  
  
 ![Ovládací prvek CVSListBox](../../mfc/reference/media/cvslistbox.png "CVSListBox –")  
  
 Pokud používáte editor prostředků Chcete-li přidat ovládací prvek upravovat seznam, Všimněte si, že **nástrojů** podokna editoru neposkytuje předem definovaného seznamu upravitelný ovládací prvek. Místo toho přidejte statický ovládací prvek, jako **skupinový rámeček** ovládacího prvku. Rozhraní používá statický ovládací prvek jako zástupný znak k určení velikosti a pozice ovládacího prvku seznam upravovat.  
  
 Chcete-li použít ovládací prvek upravovat seznam v šabloně dialogu pole, deklarujte `CVSListBox` proměnné ve vaší třídy dialogového okna. Pro podporu výměny dat mezi proměnné a ovládací prvek, definujte `DDX_Control` – makro položky v `DoDataExchange` metoda dialogového okna. Ve výchozím nastavení se vytvoří ovládací prvek upravovat seznam bez tlačítka Upravit. Pomocí této metody zděděné CVSListBoxBase::SetStandardButtons povolení tlačítka Upravit.  
  
 Další informace najdete v tématu adresáři ukázky `New Controls` ukázkový Page3.cpp a Page3.h soubory.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cstatic –](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox –](../../mfc/reference/cvslistbox-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxvslistbox.h  
  
##  <a name="additem"></a>  CVSListBox::AddItem  
 Přidá řetězec do ovládacího prvku seznamu.  
  
```  
virtual int AddItem(
    const CString& strIext,  
    DWORD_PTR dwData=0,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strIext*  
 Odkaz na řetězec.  
  
 [in] *dwData*  
 Hodnota 32-bit specifické pro aplikaci, která souvisí s řetězcem. Výchozí hodnota je 0.  
  
 [in] *iIndex*  
 Z nuly vycházející index pozice, který bude obsahovat řetězec. Pokud *iIndex* -1 je parametr, řetězec je přidán na konec seznamu. Výchozí hodnota je -1.  
  
### <a name="return-value"></a>Návratová hodnota  
 Z nuly vycházející index pozice tohoto řetězce v ovládacím prvku seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CVSListBox::GetItemData](#getitemdata) metody k načtení hodnoty, která je zadána *dwData* parametru. Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na další data.  
  
##  <a name="cvslistbox"></a>  CVSListBox::CVSListBox  
 Vytvoří `CVSListBox` objektu.  
  
```  
CVSListBox();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="edititem"></a>  CVSListBox::EditItem  
 Spustí operaci úprav na text ovládacího prvku položky seznamu.  
  
```  
virtual BOOL EditItem(int iIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Z nuly vycházející index položky ovládacího prvku seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud úspěšně; spustí operaci úprav v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Uživatel spustí operaci úprav dvojitým kliknutím na popisek položky nebo stisknutím klávesy **F2** nebo **MEZERNÍK** klíč, když je položka fokus.  
  
##  <a name="getcount"></a>  CVSListBox::GetCount  
 Získá počet řetězců v ovládacím prvku upravovat seznam.  
  
```  
virtual int GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v ovládacím prvku seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že počet je větší než hodnota indexu poslední položky, protože index je založený na nule.  
  
##  <a name="getitemdata"></a>  CVSListBox::GetItemData  
 Načte hodnotu 32-bit specifické pro aplikaci, která souvisí s položkou Přehled ovládacího prvku.  
  
```  
virtual DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Index založený na nule položky ovládacího prvku seznam upravovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota 32-bit, který je spojen se zadanou položku.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CVSListBox::SetItemData](#setitemdata) nebo [CVSListBox::AddItem](#additem) metoda 32bitová hodnota přidružit položku ovládacího prvku seznamu. Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na další data.  
  
##  <a name="getitemtext"></a>  CVSListBox::GetItemText  
 Načte text položky ovládacího prvku seznam upravovat.  
  
```  
virtual CString GetItemText(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iIndex`  
 Index založený na nule položky ovládacího prvku seznam upravovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje text zadané položky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getlisthwnd"></a>  CVSListBox::GetListHwnd  
 Vrátí popisovač do aktuální ovládací prvek zobrazení seznamu embedded.  
  
```  
virtual HWND GetListHwnd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro ovládací prvek vložený seznam zobrazení.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete načíst popisovač pro ovládací prvek zobrazení vložený seznam, který podporuje `CVSListBox` třídy.  
  
##  <a name="getselitem"></a>  CVSListBox::GetSelItem  
 Načte z nuly vycházející index aktuálně vybrané položky v ovládacím prvku upravovat seznam.  
  
```  
virtual int GetSelItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud tato metoda je úspěšná, z nuly vycházející index aktuálně vybrané položce. jinak -1.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removeitem"></a>  CVSListBox::RemoveItem  
 Odebere položku z ovládacího prvku seznam upravovat.  
  
```  
virtual BOOL RemoveItem(int iIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Index založený na nule položky ovládacího prvku seznam upravovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud zadaná položka se odebere; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="selectitem"></a>  CVSListBox::SelectItem  
 Vybere řetězci Přehled ovládacího prvku.  
  
```  
virtual BOOL SelectItem(int iItem);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *položky*  
 Index založený na nule položky ovládacího prvku seznam upravovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vybere zadanou položku a je-li vyžadován, zobrazení se posune položku do zobrazení.  
  
##  <a name="setitemdata"></a>  CVSListBox::SetItemData  
 Přehled ovládacího prvku položky přidruží hodnotu 32-bit specifické pro aplikaci.  
  
```  
virtual void SetItemData(
    int iIndex,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Index založený na nule položky ovládacího prvku seznam upravovat.  
  
 [in] *dwData*  
 32bitová hodnota. Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na další data.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
