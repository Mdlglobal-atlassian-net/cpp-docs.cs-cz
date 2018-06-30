---
title: Třída CVSListBox | Microsoft Docs
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
ms.openlocfilehash: 582ddd1340dd94f367d5401d517e9335d370b634
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122634"
---
# <a name="cvslistbox-class"></a>CVSListBox – třída
`CVSListBox` Třída podporuje ovládací prvek seznamu upravovat.  
  
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
|[CVSListBox::AddItem](#additem)|Přidá řetězec do ovládacího prvku seznam. (Přepisuje `CVSListBoxBase::AddItem`.)|  
|[CVSListBox::EditItem](#edititem)|Spustí operace upravit na text položky ovládací prvek seznamu. (Přepisuje `CVSListBoxBase::EditItem`.)|  
|[CVSListBox::GetCount](#getcount)|Načte počet řetězců v ovládacím prvku seznamu upravovat. (Přepisuje `CVSListBoxBase::GetCount`.)|  
|[CVSListBox::GetItemData](#getitemdata)|Načte hodnotu 32-bit specifické pro aplikaci, která je přidružená položce řízení upravitelné seznamu. (Přepisuje `CVSListBoxBase::GetItemData`.)|  
|[CVSListBox::GetItemText](#getitemtext)|Načte text položky ovládacího prvku seznam upravovat. (Přepisuje `CVSListBoxBase::GetItemText`.)|  
|[CVSListBox::GetSelItem](#getselitem)|Načte index založený na nule aktuálně vybrané položky v ovládacím prvku seznamu upravovat. (Přepisuje `CVSListBoxBase::GetSelItem`.)|  
|`CVSListBox::PreTranslateMessage`|Přeloží zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. Další informace a syntaxe využívající metody najdete v tématu [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Přepisuje `CVSListBoxBase::PreTranslateMessage`.)|  
|[CVSListBox::RemoveItem](#removeitem)|Odebere položku z ovládacího prvku seznam upravovat. (Přepisuje `CVSListBoxBase::RemoveItem`.)|  
|[CVSListBox::SelectItem](#selectitem)|Vybere řetězec Přehled ovládacího prvku. (Přepisuje `CVSListBoxBase::SelectItem`.)|  
|[CVSListBox::SetItemData](#setitemdata)|Přidruží hodnotu 32-bit specifické pro aplikaci položku ovládacího prvku seznam upravovat. (Přepisuje `CVSListBoxBase::SetItemData`.)|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CVSListBox::GetListHwnd](#getlisthwnd)|Vrátí popisovač do ovládacího prvku zobrazení aktuální vloženým seznamem.|  
  
## <a name="remarks"></a>Poznámky  
 `CVSListBox` Třída poskytuje sadu tlačítka Upravit, který uživateli umožňuje vytvořit, upravit, odstranit nebo změnit pořadí položek v ovládacím prvku seznamu.  
  
 Zde je snímek ovládacího prvku seznam upravovat. Na druhou položku seznamu, která je s názvem "Item2", je vybrána pro úpravy.  
  
 ![Ovládací prvek CVSListBox](../../mfc/reference/media/cvslistbox.png "cvslistbox")  
  
 Pokud používáte editoru prostředků pro přidání ovládacího prvku seznam upravovat, Všimněte si, že **sada nástrojů** podokně editoru neposkytuje ovládacího prvku předdefinovaného seznamu upravovat. Místo toho přidat statické ovládací prvek, jako **skupinový rámeček** ovládacího prvku. Rozhraní používá statické ovládací prvek jako zástupný znak zadat velikost a umístění ovládacího prvku seznam upravovat.  
  
 V poli šablony dialogového okna použít ovládací prvek seznamu upravovat, deklarovat `CVSListBox` proměnné ve vaší třídy dialogového okna. Pro podporu výměny dat mezi proměnnou a ovládací prvek, definujte `DDX_Control` makro položku v `DoDataExchange` metoda dialogového okna. Ve výchozím nastavení je ovládacího prvku upravovat seznam vytvořen bez tlačítka Upravit. Pomocí této metody zděděné CVSListBoxBase::SetStandardButtons povolit tlačítka Upravit.  
  
 Další informace najdete v tématu adresáři ukázky `New Controls` ukázkové soubory Page3.cpp a Page3.h.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CStatic](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox](../../mfc/reference/cvslistbox-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxvslistbox.h  
  
##  <a name="additem"></a>  CVSListBox::AddItem  
 Přidá řetězec do ovládacího prvku seznam.  
  
```  
virtual int AddItem(
    const CString& strIext,  
    DWORD_PTR dwData=0,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *strIext*  
 Odkaz na řetězec.  
  
 [v] *dwData*  
 32bitovou hodnotu specifické pro aplikaci, která souvisí s řetězcem. Výchozí hodnota je 0.  
  
 [v] *iIndex*  
 Index založený na nule pozice, který bude obsahovat řetězec. Pokud *iIndex* parametr hodnotu -1, řetězec se přidá na konec seznamu. Výchozí hodnota je -1.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule pozice řetězce v ovládacím prvku seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CVSListBox::GetItemData](#getitemdata) metoda se načíst hodnotu, která je zadána *dwData* parametr. Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na další data.  
  
##  <a name="cvslistbox"></a>  CVSListBox::CVSListBox  
 Vytvoří `CVSListBox` objektu.  
  
```  
CVSListBox();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="edititem"></a>  CVSListBox::EditItem  
 Spustí operace upravit na text položky ovládací prvek seznamu.  
  
```  
virtual BOOL EditItem(int iIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *iIndex*  
 Index položky ovládací prvek seznamu nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud operace upravování spustí úspěšně; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Uživatel spustí operace úpravy poklepáním na popisek položky nebo stisknutím klávesy **F2** nebo **MEZERNÍK** klávesy, když se položky je aktivní.  
  
##  <a name="getcount"></a>  CVSListBox::GetCount  
 Načte počet řetězců v ovládacím prvku seznamu upravovat.  
  
```  
virtual int GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v ovládacím prvku seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že počet je jeden znak větší než hodnota indexu poslední položky, protože index není počítaný od nuly.  
  
##  <a name="getitemdata"></a>  CVSListBox::GetItemData  
 Načte hodnotu 32-bit specifické pro aplikaci, která je přidružená položce řízení upravitelné seznamu.  
  
```  
virtual DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] *iIndex*  
 Index založený na nule položky ovládacího prvku seznam upravovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 32-bit hodnotu, která je přidružená k zadané položce.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CVSListBox::SetItemData](#setitemdata) nebo [CVSListBox::AddItem](#additem) metoda přidružení 32bitovou hodnotu k položce seznamu ovládacího prvku. Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na další data.  
  
##  <a name="getitemtext"></a>  CVSListBox::GetItemText  
 Načte text položky ovládacího prvku seznam upravovat.  
  
```  
virtual CString GetItemText(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iIndex`  
 Index založený na nule položky ovládacího prvku seznam upravovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje text zadané položky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getlisthwnd"></a>  CVSListBox::GetListHwnd  
 Vrátí popisovač do ovládacího prvku zobrazení aktuální vloženým seznamem.  
  
```  
virtual HWND GetListHwnd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro ovládací prvek zobrazení vloženým seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k načtení popisovače do ovládacího prvku zobrazení vloženým seznamem, který podporuje `CVSListBox` třídy.  
  
##  <a name="getselitem"></a>  CVSListBox::GetSelItem  
 Načte index založený na nule aktuálně vybrané položky v ovládacím prvku seznamu upravovat.  
  
```  
virtual int GetSelItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud tato metoda je úspěšné, index založený na nule aktuálně vybrané položky; jinak hodnota -1.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removeitem"></a>  CVSListBox::RemoveItem  
 Odebere položku z ovládacího prvku seznam upravovat.  
  
```  
virtual BOOL RemoveItem(int iIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *iIndex*  
 Index založený na nule položky ovládacího prvku seznam upravovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud zadaná položka je odebrána; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="selectitem"></a>  CVSListBox::SelectItem  
 Vybere řetězec Přehled ovládacího prvku.  
  
```  
virtual BOOL SelectItem(int iItem);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *položky*  
 Index založený na nule položky ovládacího prvku seznam upravovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tato metoda je úspěšná. jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vybere zadanou položku a v případě potřeby, posune položky do zobrazení.  
  
##  <a name="setitemdata"></a>  CVSListBox::SetItemData  
 Přidruží hodnotu 32-bit specifické pro aplikaci položku ovládacího prvku seznam upravovat.  
  
```  
virtual void SetItemData(
    int iIndex,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *iIndex*  
 Index založený na nule položky ovládacího prvku seznam upravovat.  
  
 [v] *dwData*  
 32bitová hodnota. Tato hodnota může být celé číslo specifické pro aplikaci nebo ukazatel na další data.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
