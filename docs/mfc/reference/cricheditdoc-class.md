---
title: CRichEditDoc – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
dev_langs:
- C++
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28b84747a694a62139546f3105f84c9e799b292a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cricheditdoc-class"></a>CRichEditDoc – třída
S [cricheditview –](../../mfc/reference/cricheditview-class.md) a [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), poskytuje funkce ovládacího prvku RichEdit v kontextu zobrazení architektury MFC na dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CRichEditDoc : public COleServerDoc  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRichEditDoc::CreateClientItem](#createclientitem)|Volá se kvůli provedení čištění dokumentu.|  
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Určuje, zda datový proud vstup a výstup by měla obsahovat informace o formátování.|  
|[CRichEditDoc::GetView](#getview)|Načte asssociated [cricheditview –](../../mfc/reference/cricheditview-class.md) objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CRichEditDoc::m_bRTF](#m_brtf)|Určuje, zda by měla obsahovat datový proud vstupně-výstupních operací formátování.|  
  
## <a name="remarks"></a>Poznámky  
 "RichEdit řízení" je okno, ve kterém může uživatel zadat a upravit text. Text se dá přiřadit znak a formátování odstavce a může obsahovat vložené objekty OLE. Ovládací prvky Rich edit zadejte programovací rozhraní pro formátování textu. Aplikace musí implementovat však potřeba zpřístupnit operací formátování uživateli žádné uživatelské rozhraní komponenty.  
  
 `CRichEditView` udržuje textu a formátování vlastnosti textu. `CRichEditDoc` udržuje seznam klientské položky, které jsou v zobrazení. `CRichEditCntrItem` poskytuje kontejner straně přístup k položkám klienta OLE.  
  
 Tento ovládací prvek Windows běžné (a proto [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Příklad použití bohaté úpravy dokumentu v aplikaci MFC, najdete v článku [WORDPAD](../../visual-cpp-samples.md) ukázkové aplikace.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)  
  
 `CRichEditDoc`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrich.h  
  
##  <a name="createclientitem"></a>  CRichEditDoc::CreateClientItem  
 Volání této funkce můžete vytvořit `CRichEditCntrItem` objektu a přidejte ji do tohoto dokumentu.  
  
```  
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *preo*  
 Ukazatel na [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) struktura, která popisuje položky OLE. Nové `CRichEditCntrItem` objektu je postavena na tuto položku OLE. Pokud *preo* je **NULL**, nová položka klienta je prázdná.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na novou [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objekt, který byl přidán do tohoto dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nebude provádět všechny inicializace OLE.  
  
 Další informace najdete v tématu [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) struktura ve Windows SDK.  
  
##  <a name="getstreamformat"></a>  CRichEditDoc::GetStreamFormat  
 Volání této funkce můžete určit, v textovém formátu pro streamování obsah bohaté úpravy.  
  
```  
int GetStreamFormat() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících příznaků:  
  
- `SF_TEXT` Označuje, že prvku RichEdit neumožňuje spravovat informace o formátování.  
  
- `SF_RTF` Označuje, že prvku RichEdit Udržovat informace o formátování.  
  
### <a name="remarks"></a>Poznámky  
 Návratová hodnota je založena na [m_bRTF](#m_brtf) – datový člen. Funkce vrátí hodnotu `SF_RTF` Pokud `m_bRTF` je **TRUE**, jinak hodnota `SF_TEXT`.  
  
##  <a name="getview"></a>  CRichEditDoc::GetView  
 Volání této funkce pro přístup [cricheditview –](../../mfc/reference/cricheditview-class.md) objekt přidružený k tomuto `CRichEditDoc` objektu.  
  
```  
virtual CRichEditView* GetView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CRichEditView` objekt přidružený k dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Text a informace o formátování, které jsou obsaženy v rámci `CRichEditView` objektu. `CRichEditDoc` Objekt udržuje položky OLE pro serializaci. Měla by existovat pouze jedna `CRichEditView` pro každou `CRichEditDoc`.  
  
##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF  
 Když **TRUE**, znamená, že [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) a [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) měli uložit odstavce a formátování znaků vlastnosti.  
  
```  
BOOL m_bRTF;  
```  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC WORDPAD](../../visual-cpp-samples.md)   
 [COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cricheditview – třída](../../mfc/reference/cricheditview-class.md)   
 [CRichEditCntrItem – třída](../../mfc/reference/cricheditcntritem-class.md)   
 [COleDocument – třída](../../mfc/reference/coledocument-class.md)   
 [CRichEditCtrl – třída](../../mfc/reference/cricheditctrl-class.md)
