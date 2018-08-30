---
title: Cricheditcntritem – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 17f50f5e4fb8b9330a09d4964aa99fbf01f4b34d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206968"
---
# <a name="cricheditcntritem-class"></a>Cricheditcntritem – třída
S [cricheditview –](../../mfc/reference/cricheditview-class.md) a [cricheditdoc –](../../mfc/reference/cricheditdoc-class.md), poskytuje funkce pro ovládací prvek RTF v rámci kontextu architektury zobrazení dokumentu MFC.  
  
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
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Aktivuje položku jako jiného typu.|  
  
## <a name="remarks"></a>Poznámky  
 "Ovládacího prvku rich edit" je okno, ve kterém můžete uživatele zadat a upravit text. Text je možné přiřadit formátování znaků a odstavců a může obsahovat vložené objekty OLE. Bohaté ovládacích prvcích pro úpravy poskytují programovací rozhraní pro formátování textu. Však musí aplikace implementovat součásti potřebné k zajištění operací formátování pro uživatele k dispozici žádné uživatelského rozhraní.  
  
 `CRichEditView` udržuje textu a formátování vlastnosti textu. `CRichEditDoc` udržuje seznam klientské položky OLE, které jsou v zobrazení. `CRichEditCntrItem` poskytuje kontejner straně přístup k klientskou položku OLE.  
  
 Tento ovládací prvek Windows běžné (a tedy [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.  
  
 Příklad použití RichEdit kontejner položek v aplikaci knihovny MFC, najdete v článku [WORDPAD](../../visual-cpp-samples.md) ukázkovou aplikaci.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [Cdocitem –](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `CRichEditCntrItem`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrich.h  
  
##  <a name="cricheditcntritem"></a>  CRichEditCntrItem::CRichEditCntrItem  
 Volání této funkce můžete vytvořit `CRichEditCntrItem` objektu a přidejte ji do dokumentu kontejneru.  
  
```  
CRichEditCntrItem(
    REOBJECT* preo = NULL,  
    CRichEditDoc* pContainer = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *preo*  
 Ukazatel [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktura, která popisuje položky OLE. Nové `CRichEditCntrItem` objektu je postavena na tuto položku OLE. Pokud *preo* má hodnotu NULL, položka klienta je prázdná.  
  
 *pContainer*  
 Ukazatel na dokument kontejneru, který bude obsahovat této položky. Pokud *pContainer* má hodnotu NULL, je nutné explicitně volat [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) na tuto položku klienta přidat do dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce není udělat všechny inicializace technologie OLE.  
  
 Další informace najdete v tématu [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktura v sadě Windows SDK.  
  
##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject  
 Voláním této funkce synchronizovat zařízení aspekt [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), to `CRichEditCntrltem` na klíči určenému *Znov*.  
  
```  
void SyncToRichEditObject(REOBJECT& reo);
```  
  
### <a name="parameters"></a>Parametry  
 *Znov*  
 Odkaz [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktura, která popisuje položky OLE.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC WORDPAD](../../visual-cpp-samples.md)   
 [Coleclientitem – třída](../../mfc/reference/coleclientitem-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cricheditdoc – třída](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
