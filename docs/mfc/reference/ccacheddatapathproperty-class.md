---
title: "Třída CCachedDataPathProperty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
dev_langs:
- C++
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2fb62a905d092a347103ea98fcd323e3778ed458
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty – třída
Vlastnost asynchronně přenáší a uložené v mezipaměti v paměti soubor ovládacího prvku implementuje OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Vytvoří `CCachedDataPathProperty` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile`objekt ve kterém data do mezipaměti.|  
  
## <a name="remarks"></a>Poznámky  
 Soubor paměti je uložená v paměti RAM místo na disku a je užitečné pro přenosy prostřednictvím rychlého dočasné.  
  
 Spolu s **CAysncMonikerFile** a `CDataPathProperty`, `CCachedDataPathProperty` poskytuje funkce pro použití asynchronní monikery v ovládací prvky OLE. S `CCachedDataPathProperty` objekty, budete moci asynchronně přenosu dat ze zdroje adresu URL nebo soubor a uložte ho do souboru paměti prostřednictvím `m_Cache` veřejné proměnné. Veškerá data budou uložena v souboru paměti a není nutné přepsat [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) Pokud chcete sledovat pro oznámení a reagovat. Například pokud přenášíte velké. Soubor ve formátu GIF a chcete oznámit vlastního ovládacího prvku, aby byl doručen více dat a ho měli překreslit, přepsání `OnDataAvailable` aby oznámení.  
  
 Třída `CCachedDataPathProperty` je odvozený od `CDataPathProperty`.  
  
 Další informace o tom, jak použít asynchronní monikery a ovládací prvky ActiveX v internetových aplikací najdete v následujících tématech:  
  
- [Internet první kroky: Ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internetu první kroky: Asynchronní Monikery](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
  
##  <a name="ccacheddatapathproperty"></a>CCachedDataPathProperty::CCachedDataPathProperty  
 Vytvoří `CCachedDataPathProperty` objektu.  
  
```  
CCachedDataPathProperty(COleControl* pControl = NULL);

 
CCachedDataPathProperty(
    LPCTSTR lpszPath,  
    COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 Ukazatel na objekt ovládací prvek ActiveX, který má být přidruženy s tímto `CCachedDataPathProperty` objektu.  
  
 `lpszPath`  
 Cesta, která může být absolutní nebo relativní, použít k vytvoření asynchronní přezdívka, který odkazuje na skutečnou absolutní umístění vlastnosti. `CCachedDataPathProperty`adresy URL, ne názvy souborů používá. Pokud chcete `CCachedDataPathProperty` objektu pro soubor, předřazení file:// k cestě.  
  
### <a name="remarks"></a>Poznámky  
 `COleControl` Objektu na kterou odkazuje `pControl` používá [otevřete](../../mfc/reference/cdatapathproperty-class.md#open) a načíst odvozené třídy. Pokud `pControl` je **NULL**, ovládací prvek použít s **otevřete** musí být nastavená s [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Pokud `lpszPath` je **NULL**, můžete předat v cestě prostřednictvím **otevřete** nebo nastavte její [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).  
  
##  <a name="m_cache"></a>CCachedDataPathProperty::m_Cache  
 Obsahuje název třídy paměti souboru, do kterého se data uloží do mezipaměti.  
  
```  
CMemFile m_Cache;  
```  
  
### <a name="remarks"></a>Poznámky  
 Paměť souboru je uložené v paměti RAM místo na disku.  
  
## <a name="see-also"></a>Viz také  
 [CDataPathProperty – třída](../../mfc/reference/cdatapathproperty-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDataPathProperty – třída](../../mfc/reference/cdatapathproperty-class.md)
