---
title: Třída CRichEditCntrItem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0b4c038389810fcc6a847cdbf7837568b3007b6
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078605"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem – třída
S [cricheditview –](../../mfc/reference/cricheditview-class.md) a [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), poskytuje funkce ovládacího prvku RichEdit v kontextu zobrazení architektury MFC na dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CRichEditCntrItem : public COleClientItem  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|Vytvoří `CRichEditCntrItem` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Aktivuje jako jiný typ položky.|  
  
## <a name="remarks"></a>Poznámky  
 "RichEdit řízení" je okno, ve kterém může uživatel zadat a upravit text. Text se dá přiřadit znak a formátování odstavce a může obsahovat vložené objekty OLE. Ovládací prvky Rich edit zadejte programovací rozhraní pro formátování textu. Aplikace musí implementovat však potřeba zpřístupnit operací formátování uživateli žádné uživatelské rozhraní komponenty.  
  
 `CRichEditView` udržuje textu a formátování vlastnosti textu. `CRichEditDoc` udržuje seznam položek OLE klienta, které jsou v zobrazení. `CRichEditCntrItem` poskytuje kontejner straně přístup k položce OLE klienta.  
  
 Tento ovládací prvek Windows běžné (a proto [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Příklad použití RichEdit kontejner položek v aplikaci MFC, najdete v článku [WORDPAD](../../visual-cpp-samples.md) ukázkové aplikace.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `CRichEditCntrItem`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrich.h  
  
##  <a name="cricheditcntritem"></a>  CRichEditCntrItem::CRichEditCntrItem  
 Volání této funkce můžete vytvořit `CRichEditCntrItem` objektu a přidat jej do dokumentu kontejneru.  
  
```  
CRichEditCntrItem(
    REOBJECT* preo = NULL,  
    CRichEditDoc* pContainer = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *preo*  
 Ukazatel na [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) struktura, která popisuje položky OLE. Nové `CRichEditCntrItem` objektu je postavena na tuto položku OLE. Pokud *preo* je **NULL**, položka klienta je prázdná.  
  
 *pContainer*  
 Ukazatel na dokument kontejneru, který bude obsahovat tuto položku. Pokud *pContainer* je **NULL**, musíte explicitně volat [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) na tuto položku klienta přidat do dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nebude provádět všechny inicializace OLE.  
  
 Další informace najdete v tématu [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) struktura ve Windows SDK.  
  
##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject  
 Volání této funkce synchronizovat zařízení aspekt, [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318), tohoto `CRichEditCntrltem` na které *Znov*.  
  
```  
void SyncToRichEditObject(REOBJECT& reo);
```  
  
### <a name="parameters"></a>Parametry  
 *Znov*  
 Odkaz na [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) struktura, která popisuje položky OLE.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC WORDPAD](../../visual-cpp-samples.md)   
 [COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc – třída](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
