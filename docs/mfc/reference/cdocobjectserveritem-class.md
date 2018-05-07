---
title: Třída CDocObjectServerItem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
dev_langs:
- C++
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c6f990a00fb96195a54ee7ed6906068985b052f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem – třída
Implementuje server OLE příkazy speciálně pro DocObject servery.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Vytvoří `CDocObjectServerItem` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocObjectServerItem::GetDocument](#getdocument)|Načte ukazatel na dokument, který obsahuje položku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocObjectServerItem::OnHide](#onhide)|Rozhraní framework se snaží skrýt položku DocObject, vyvolá výjimku.|  
|[CDocObjectServerItem::OnShow](#onshow)|Voláno rámcem, aby DocObject položky místní active. Pokud položka není DocObject, zavolá [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|  
  
## <a name="remarks"></a>Poznámky  
 `CDocObjectServerItem` Definuje přepisovatelné členské funkce: [skrytí](#onhide), [při otevření](http://msdn.microsoft.com/en-us/7a9b1363-6ad8-4732-9959-4e35c07644fd), a [viditelnost](#onshow).  
  
 Použít `CDocObjectServerItem`, zajistil, který [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) potlačení v vaše `COleServerDoc`-odvozené třídě vrátí novou `CDocObjectServerItem` objektu. Pokud potřebujete změnit všechny funkce v dané položce, můžete vytvořit novou instanci třídy vlastní `CDocObjectServerItem`-odvozené třídy.  
  
 Další informace o DocObjects najdete v tématu [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) a [COleCmdUI](../../mfc/reference/colecmdui-class.md) v *odkaz knihovny MFC*. Viz také [první kroky Internet: aktivní dokumenty](../../mfc/active-documents-on-the-internet.md) a [aktivní dokumenty](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdocob.h  
  
##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem  
 Vytvoří `CDocObjectServerItem` objektu.  
  
```  
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parametry  
 `pServerDoc`  
 Ukazatel na dokument, který bude obsahovat nová položka DocObject.  
  
 `bAutoDelete`  
 Určuje, zda lze po vydání odkazu na Odstranit objekt. Argument na **FALSE** Pokud `CDocObjectServerItem` objekt je nedílnou součástí vašeho dokumentu data. Nastavte ji na **TRUE** Pokud se objekt sekundární struktura použít k identifikaci rozsah v datech vašeho dokumentu, který může odstranit rozhraní.  
  
##  <a name="getdocument"></a>  CDocObjectServerItem::GetDocument  
 Načte ukazatel na dokument, který obsahuje položku.  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na dokument, který obsahuje položku; **NULL** Pokud položka není součástí dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje přístup k dokumentu serveru, který můžete předat jako argument k [CDocObjectServerItem](#cdocobjectserveritem) konstruktor.  
  
##  <a name="onhide"></a>  CDocObjectServerItem::OnHide  
 Voláno rámcem skrytí položky.  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace vyvolá výjimku, pokud je položka DocObject. Aktivní DocObject položku nelze skrýt, protože trvá celého zobrazení. Je nutné deaktivovat položce DocObject zmizí. Pokud položka není DocObject, výchozí implementace volá [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).  
  
##  <a name="onshow"></a>  CDocObjectServerItem::OnShow  
 Voláno rámcem dáte pokyn, aby serverová aplikace, aby DocObject položky místní active.  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud položka není DocObject, výchozí implementace volá [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Tato funkce přepsání, pokud chcete provést zvláštní zpracování při otevírání DocObject položky.  
  
## <a name="see-also"></a>Viz také  
 [COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDocObjectServer – třída](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem – třída](../../mfc/reference/coledocobjectitem-class.md)
