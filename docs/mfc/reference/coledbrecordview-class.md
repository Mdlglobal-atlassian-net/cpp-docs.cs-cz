---
title: "COleDBRecordView – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd827d729af5186d6872536cdaa3d8863d1f8d10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="coledbrecordview-class"></a>COleDBRecordView – třída
Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDBRecordView : public CFormView  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|Vytvoří `COleDBRecordView` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Vrátí standardní `HRESULT` hodnotu.|  
|[COleDBRecordView::OnMove](#onmove)|Aktualizace na aktuální záznam (je-li změny) ve zdroji dat a pak se posouvá zadaný záznam (Další, předchozí, první nebo poslední).|  
  
## <a name="remarks"></a>Poznámky  
 Zobrazení je přímo připojený k zobrazení formuláře `CRowset` objektu. Zobrazení je vytvořený z prostředku šablony dialogovém okně a zobrazí pole `CRowset` objektu v ovládacích prvcích šablony dialogového okna. `COleDBRecordView` Objektu používá výměna dialogových dat (DDX) a navigačních funkce součástí `CRowset`, k automatizaci přesun dat mezi ovládacími prvky na formuláři a pole sady řádků. `COleDBRecordView`také poskytuje výchozí implementaci pro přesun na první další, předchozí nebo poslední záznam a rozhraní pro aktualizaci záznamu aktuálně pro zobrazení.  
  
 Můžete použít funkce DDX s **COleDbRecordView** získat data přímo ze záznamů databáze a zobrazit ji v dialogovém okně ovládacího prvku. Byste měli používat **DDX_\***  metody (například `DDX_Text`), nikoli **DDX_Field –\***  funkce (například `DDX_FieldText`) s **COleDbRecordView** . `DDX_FieldText`nebude fungovat se **COleDbRecordView** protože `DDX_FieldText` používá další argument typu **CRecordset\***  (pro `CRecordView`) nebo **CDaoRecordset \***  (pro `CDaoRecordView`).  
  
> [!NOTE]
>  Pokud pracujete s třídy objektů DAO (Data Access), nikoli třídy šablony příjemce technologie OLE DB, použijte třídu [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) místo. Další informace najdete v článku [přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).  
  
 `COleDBRecordView`uchovává informace o pozici uživatele v dané sadě řádků tak, aby zobrazení záznamů můžete aktualizovat uživatelské rozhraní. Pokud se uživatel přesune na obou koncích sady řádků, zobrazení záznamu zakáže objekty uživatelského rozhraní – například položek nabídky nebo tlačítka panelu nástrojů – pro přesun další ve stejném směru.  
  
 Další informace o třídy sady řádků, najdete v článku [pomocí OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md) článku.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [Třídy CFormView](../../mfc/reference/cformview-class.md)  
  
 `COleDBRecordView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxoledb.h  
  
##  <a name="coledbrecordview"></a>COleDBRecordView::COleDBRecordView  
 Vytvoří `COleDBRecordView` objektu.  
  
```  
COleDBRecordView(LPCTSTR lpszTemplateName);  
COleDBRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Obsahuje řetězec ukončené hodnotou null, který je název prostředku šablony dialogového okna.  
  
 `nIDTemplate`  
 Obsahuje číslo ID prostředku šablony dialogového okna.  
  
### <a name="remarks"></a>Poznámky  
 Když vytvoříte objekt typ odvozený z `COleDBRecordView`, vyvolat jeden z konstruktorů vytvořit objekt zobrazení a identifikovat prostředku dialogového okna, na kterých je založena zobrazení. Prostředek můžete identifikovat pomocí názvu (pass řetězec jako argument konstruktoru) nebo pomocí jejího ID (pass celé číslo bez znaménka jako argument).  
  
> [!NOTE]
>  Odvozené třídy *musí* zadat vlastní konstruktor. V konstruktoru, vyvolat konstruktor, `COleDBRecordView::COleDBRecordView`, s názvem prostředků nebo ID jako argument.  
  
##  <a name="ongetrowset"></a>COleDBRecordView::OnGetRowset  
 Vrátí popisovač pro **CRowset <>** objekt přidružený k zobrazení záznamu.  
  
```  
virtual CRowset<>* OnGetRowset() = 0;  
 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci Vytvořit nebo získat objektu sady řádků a vrácení popisovače musí přepsat. Pokud je deklarovat třídě zobrazení záznamu s ClassWizard, zapíše průvodce přepsat výchozí. ClassWizard pro výchozí implementace vrací popisovač řádků uložené v zobrazení záznamů, pokud existuje. Pokud ne, vytvoří objektu sady řádků typu zadán s ClassWizard a volání jeho **otevřete** člen funkce Otevřít v tabulce nebo spustit dotaz a pak vrátí popisovač k objektu.  
  
> [!NOTE]
>  Předchozí MFC 7.0 `OnGetRowset` vrátil ukazatel na `CRowset`. Pokud máte kód, který volá `OnGetRowset`, budete muset změnit návratový typ k třídě šablonou **CRowset <>**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]  
  
 Další informace a příklady naleznete v článku [zobrazení záznamu: použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>COleDBRecordView::OnMove  
 Přesune na jiný záznam v sadě řádků a zobrazení zobrazit jeho polí v ovládacích prvcích záznamu.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDMoveCommand`  
 Jedna z následujících hodnot ID standardních příkazů:  
  
- `ID_RECORD_FIRST`– Přesunout na první záznam v sadě záznamů.  
  
- `ID_RECORD_LAST`– Přesunete na poslední záznam v sadě záznamů.  
  
- `ID_RECORD_NEXT`– Přejděte na další záznam v sadě záznamů.  
  
- `ID_RECORD_PREV`– Přesunout do předchozího záznamu v sadě záznamů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl přesun úspěšný; jinak hodnota 0, pokud žádost o přesunutí byl odepřen.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá odpovídající **přesunout** členské funkce `CRowset` objekt přidružený k zobrazení záznamu.  
  
 Ve výchozím nastavení `OnMove` aktualizuje na aktuální záznam ve zdroji dat, pokud uživatel se změnilo v zobrazení záznamů.  
  
 V Průvodce vytvořením aplikace vytvoří prostředek nabídky k položkám nabídky první záznam, poslední záznam, další záznam a předchozího záznamu. Pokud vyberete možnost lze ukotvit nástrojů, aplikace Průvodce také vytvoří panel nástrojů s tlačítka odpovídající tyto příkazy.  
  
 Pokud přesunete za poslední záznam v sadě záznamů, zobrazení záznamů stále zobrazuje poslední záznam. Pokud přesunete zpátky po první záznam, zobrazení záznamů stále zobrazuje na první záznam.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



