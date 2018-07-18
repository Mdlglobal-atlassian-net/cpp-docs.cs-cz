---
title: Cdocobjectserveritem – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: dc498b96dad089276b248fbb2e420dde3c0bc514
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027135"
---
# <a name="cdocobjectserveritem-class"></a>Cdocobjectserveritem – třída
Příkazy Implements OLE servere speciálně pro servery DocObject.  
  
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
|[CDocObjectServerItem::OnHide](#onhide)|Vyvolá výjimku, pokud framework se snaží skrýt položku DocObject.|  
|[CDocObjectServerItem::OnShow](#onshow)|Volá se rozhraním, aby vytisknout položky na místě aktivní. Pokud položka není DocObject, zavolá [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|  
  
## <a name="remarks"></a>Poznámky  
 `CDocObjectServerItem` Definuje přepisovatelné členské funkce: [skrytí](#onhide), [při otevření](http://msdn.microsoft.com/7a9b1363-6ad8-4732-9959-4e35c07644fd), a [viditelnost](#onshow).  
  
 Použití `CDocObjectServerItem`, bylo zaručeno, že [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) přepsat v vaše `COleServerDoc`-odvozené třídě vrátí nový `CDocObjectServerItem` objektu. Pokud potřebujete změnit všechny funkce v vaši položku, můžete vytvořit novou instanci třídy vlastní `CDocObjectServerItem`-odvozené třídy.  
  
 Další informace o DocObjects najdete v tématu [cdocobjectserver –](../../mfc/reference/cdocobjectserver-class.md) a [colecmdui –](../../mfc/reference/colecmdui-class.md) v *odkaz knihovny MFC*. Viz také [první kroky Internet: aktivní dokumenty](../../mfc/active-documents-on-the-internet.md) a [aktivní dokumenty](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [Cdocitem –](../../mfc/reference/cdocitem-class.md)  
  
 [Coleserveritem –](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdocob.h  
  
##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem  
 Vytvoří `CDocObjectServerItem` objektu.  
  
```  
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parametry  
 *pServerDoc*  
 Ukazatel na dokument, který bude obsahovat nová položka DocObject.  
  
 *bAutoDelete*  
 Určuje, jestli objekt může odstranit při odkazu na vydání. Nastavte na hodnotu FALSE, pokud argument `CDocObjectServerItem` objektu je nedílnou součástí dat dokumentu. Nastavte na hodnotu TRUE, pokud je objekt sekundární struktura používaná k identifikaci oblast v dokumentu, a data, která je možné odstranit v rámci rozhraní.  
  
##  <a name="getdocument"></a>  CDocObjectServerItem::GetDocument  
 Načte ukazatel na dokument, který obsahuje položku.  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na dokument, který obsahuje položky; Hodnota NULL, pokud položka není součástí dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje přístup k dokumentu na serveru, který je předán jako argument [cdocobjectserveritem –](#cdocobjectserveritem) konstruktoru.  
  
##  <a name="onhide"></a>  CDocObjectServerItem::OnHide  
 Volá se rozhraním skryjete položky.  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace vyvolá výjimku, pokud je položka DocObject. Aktivní položky DocObject nelze skrýt, protože trvá celého zobrazení. Je nutné deaktivovat položku DocObject, zmizí. Pokud položka není DocObject, výchozí implementace volá [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).  
  
##  <a name="onshow"></a>  CDocObjectServerItem::OnShow  
 Volá se rozhraním, dáte pokyn, aby se serverová aplikace mohla provést vytisknout položky místní aktivní.  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud položka není DocObject, výchozí implementace volá [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Tato funkce přepište, pokud chcete provést zvláštní zpracování při otevření položky DocObject.  
  
## <a name="see-also"></a>Viz také  
 [Coleserveritem – třída](../../mfc/reference/coleserveritem-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cdocobjectserver – třída](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem – třída](../../mfc/reference/coledocobjectitem-class.md)
