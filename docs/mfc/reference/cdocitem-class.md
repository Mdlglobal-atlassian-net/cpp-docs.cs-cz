---
title: "Třída CDocItem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a4987554965674612eaf8d9aa78c659f7f28b75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdocitem-class"></a>CDocItem – třída
Základní třída pro položky dokumentů, které jsou součástí data dokumentu.  
  
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
 `CDocItem`objekty se používají k vyjádření OLE – položky v dokumentech klient i server.  
  
 Další informace najdete v článku [kontejnery: Implementace kontejneru](../../mfc/containers-implementing-a-container.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="getdocument"></a>CDocItem::GetDocument  
 Volání této funkce můžete získat dokument, který obsahuje položku.  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na dokument, který obsahuje položku; **NULL**, pokud položka není součástí dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je přepsání v odvozené třídy [COleClientItem](../../mfc/reference/coleclientitem-class.md) a [COleServerItem](../../mfc/reference/coleserveritem-class.md), ukazatel vrácením buď [COleDocument](../../mfc/reference/coledocument-class.md), [ COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md), nebo [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) objektu.  
  
##  <a name="isblank"></a>CDocItem::IsBlank  
 Voláno rámcem, když dojde k výchozí serializace.  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud položka neobsahuje informace o; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `CDocItem` objekty nejsou prázdné. [COleClientItem](../../mfc/reference/coleclientitem-class.md) objekty jsou prázdné někdy protože vyplývají přímo ze `CDocItem`. Ale [COleServerItem](../../mfc/reference/coleserveritem-class.md) objekty jsou vždy prázdná. Ve výchozím nastavení aplikace rozhraní OLE obsahující `COleClientItem` objekty, které nemají žádné x nebo y rozsah se serializují. K tomu je potřeba vrácení **TRUE** z přepsání `IsBlank` Pokud položka neobsahuje žádné x nebo y rozsah.  
  
 Tato funkce přepsání, pokud chcete implementovat dalších akcí během serializace.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDocument – třída](../../mfc/reference/coledocument-class.md)   
 [COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)   
 [COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)
