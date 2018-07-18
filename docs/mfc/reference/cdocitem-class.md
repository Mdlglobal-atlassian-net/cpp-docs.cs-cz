---
title: Cdocitem – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
dev_langs:
- C++
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88c30418f886cd791a7119367c5ddbccc19003fa
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335578"
---
# <a name="cdocitem-class"></a>Cdocitem – třída
Základní třída pro položky dokumentu, které jsou součástí dat dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDocItem : public CCmdTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocItem::GetDocument](#getdocument)|Vrátí dokument, který obsahuje položku.|  
|[CDocItem::IsBlank](#isblank)|Určuje, zda položka obsahuje všechny informace.|  
  
## <a name="remarks"></a>Poznámky  
 `CDocItem` objekty se používají pro reprezentaci položky OLE v dokumentech klienta i serveru.  
  
 Další informace najdete v článku [kontejnery: Implementace kontejneru](../../mfc/containers-implementing-a-container.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="getdocument"></a>  CDocItem::GetDocument  
 Voláním této funkce získáte dokumentu, který obsahuje položku.  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na dokument, který obsahuje položky; Hodnota NULL, pokud položka není součástí dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je v odvozených třídách přepsána [COleClientItem](../../mfc/reference/coleclientitem-class.md) a [odvozenou třídu COleServerItem](../../mfc/reference/coleserveritem-class.md), vrací ukazatel na buď [coledocument –](../../mfc/reference/coledocument-class.md), [ Colelinkingdoc –](../../mfc/reference/colelinkingdoc-class.md), nebo [coleserverdoc –](../../mfc/reference/coleserverdoc-class.md) objektu.  
  
##  <a name="isblank"></a>  CDocItem::IsBlank  
 Volá se rozhraním, když dojde k výchozí serializace.  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud položka neobsahuje žádné informace o; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `CDocItem` objekty nejsou prázdné. [COleClientItem](../../mfc/reference/coleclientitem-class.md) objekty jsou prázdné někdy, protože vyplývají přímo ze `CDocItem`. Ale [odvozenou třídu COleServerItem](../../mfc/reference/coleserveritem-class.md) objekty jsou vždy prázdná. Ve výchozím nastavení, OLE – aplikace, který obsahuje `COleClientItem` objekty, které mají žádné x nebo y rozsahu se serializují. To se provádí tak, že vrací hodnotu TRUE z přepsání `IsBlank` Pokud položka neobsahuje žádné x nebo y rozsahu.  
  
 Tato funkce přepište, pokud chcete provádět další akce během serializace.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Coledocument – třída](../../mfc/reference/coledocument-class.md)   
 [Coleserveritem – třída](../../mfc/reference/coleserveritem-class.md)   
 [COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)
