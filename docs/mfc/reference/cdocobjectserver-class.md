---
title: "Třída CDocObjectServer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
dev_langs:
- C++
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 912262c4f1ba85c181bb30ee5d6f38a0defe5d5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer – třída
Implementuje rozhraní OLE další potřebné ke změně normální `COleDocument` serveru do celého serveru DocObject: `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`, a `IPrint`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDocObjectServer : public CCmdTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|Vytvoří `CDocObjectServer` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Aktivuje server objektu dokumentu, ale nejsou zobrazeny.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocObjectServer::OnActivateView](#onactivateview)|Zobrazí DocObject zobrazení.|  
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Obnoví stav DocObject zobrazení.|  
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Uloží stav DocObject zobrazení.|  
  
## <a name="remarks"></a>Poznámky  
 `CDocObjectServer`je odvozený od `CCmdTarget` a úzce spolupracuje s `COleServerDoc` vystavit rozhraní.  
  
 Dokument DocObject serveru může obsahovat [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) objekty, které představují rozhraní serveru DocObject položek.  
  
 Chcete-li přizpůsobit DocObject serveru, odvodit vlastní třídu z `CDocObjectServer` a přepsat její instalaci funkce zobrazení, [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate), a [OnSaveViewState ](#onsaveviewstate). Musíte zadat novou instanci třídy třídě v reakci na framework volání.  
  
 Další informace o DocObjects najdete v tématu [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) a [COleCmdUI](../../mfc/reference/colecmdui-class.md) v *odkaz knihovny MFC*. Viz také [první kroky Internet: aktivní dokumenty](../../mfc/active-documents-on-the-internet.md) a [aktivní dokumenty](../../mfc/active-documents-on-the-internet.md).  
  
 Také najdete v následujícím článku znalostní báze Knowledge Base:  
  
-   Q247382: PRB: popisy pro ovládací prvky ActiveX dokumentu serveru jsou skryt kontejneru ActiveX dokumentu  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocObjectServer`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdocob.h  
  
##  <a name="activatedocobject"></a>CDocObjectServer::ActivateDocObject  
 Volání této funkce můžete aktivovat (ale nezobrazovat) serveru objektu dokumentu.  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>Poznámky  
 `ActivateDocObject`volání `IOleDocumentSite`na **ActivateMe** metoda, ale nezobrazuje zobrazení, protože se čeká na konkrétní pokyny o tom, jak nastavit a zobrazit, zadaný ve volání [CDocObjectServer::OnActivateView](#onactivateview).  
  
 Společně `ActivateDocObject` a `OnActivateView` aktivovat a zobrazit DocObject. Aktivace DocObject se liší od jiných druhů OLE – aktivace na místě. Aktivace DocObject obchází zobrazení ohraničení šrafování na místě a vylepšení objektu (například úchyty), ignoruje objektu rozsah funkcí a nevykresluje posuvníky v rámci obdélník zobrazení a kreslení je mimo obdélníku (jako normální aktivace na místě).  
  
##  <a name="cdocobjectserver"></a>CDocObjectServer::CDocObjectServer  
 Vytvoří a inicializuje `CDocObjectServer` objektu.  
  
```  
explicit CDocObjectServer(
    COleServerDoc* pOwner,  
    LPOLEDOCUMENTSITE pDocSite = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pOwner*  
 Ukazatel na dokument lokality klienta, který je klient operačních systémů DocObject serveru.  
  
 `pDocSite`  
 Ukazatel `IOleDocumentSite` rozhraní implementované kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Když je aktivní DocObject, klient lokality rozhraní OLE ( `IOleDocumentSite`) je co umožňuje serveru DocObject ke komunikaci s svého klienta (kontejner). Při aktivaci serveru DocObject nejdřív zkontroluje, že kontejner implementuje `IOleDocumentSite` rozhraní. Pokud ano, [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) je volána, pokud kontejner podporuje DocObjects. Ve výchozím nastavení `GetDocObjectServer` vrátí **NULL**. Je nutné přepsat `COleServerDoc::GetDocObjectServer` vytvořit novou `CDocObjectServer` objekt nebo objekt odvozené vlastní, ukazatele na `COleServerDoc` kontejner a jeho `IOleDocumentSite` rozhraní jako argumenty pro konstruktor.  
  
##  <a name="onactivateview"></a>CDocObjectServer::OnActivateView  
 Volání této funkce Zobrazit DocObject.  
  
```  
virtual HRESULT OnActivateView();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí chyba nebo hodnotu pro upozornění. Ve výchozím nastavení, vrátí **NOERROR** Pokud úspěšné, jinak **E_FAIL**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vytvoří okno s rámečkem na místě, nevykresluje posuvníky v rámci zobrazení, nastaví nabídky serveru sdílí s jeho kontejneru, přidá rámce ovládací prvky, nastaví objekt aktivní, pak nakonec zobrazuje okně s rámečkem na místě a nastaví fokus.  
  
##  <a name="onapplyviewstate"></a>CDocObjectServer::OnApplyViewState  
 Funkci k obnovení stavu zobrazení DocObject přepište.  
  
```  
virtual void OnApplyViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 `ar`  
 A `CArchive` objekt, ze kterého k serializaci stav zobrazení.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána, když se zobrazuje zobrazení poprvé po jeho vytvoření instance. `OnApplyViewState`dá pokyn zobrazení znovu inicializovat samotné podle dat v `CArchive` objekt dříve uložit s [OnSaveViewState](#onsaveviewstate). Zobrazení musí ověřit data v `CArchive` objekt, protože kontejneru nebude pokoušet o interpretovat data o stavu zobrazit libovolným způsobem.  
  
 Můžete použít `OnSaveViewState` k uložení trvalé informace specifické pro vaše zobrazení stavu. Pokud přepíšete `OnSaveViewState` k ukládání informací, můžete přepsat `OnApplyViewState` a přečtěte si tyto informace platí pro zobrazení, když je nově aktivován.  
  
##  <a name="onsaveviewstate"></a>CDocObjectServer::OnSaveViewState  
 Přepsání této funkci můžete uložit informace o zobrazení DocObject navíc stavu.  
  
```  
virtual void OnSaveViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 `ar`  
 A `CArchive` do stavu zobrazení je serializováno objektu.  
  
### <a name="remarks"></a>Poznámky  
 Vašemu stavu může obsahovat vlastnosti, například typ zobrazení, faktor zvětšování, vložení a výběr bodu a tak dále. Kontejner obvykle volá tuto funkci před deaktivací zobrazení. Uložený stav může být obnovena novější prostřednictvím [OnApplyViewState](#onapplyviewstate).  
  
 Můžete použít `OnSaveViewState` k uložení trvalé informace specifické pro vaše zobrazení stavu. Pokud přepíšete `OnSaveViewState` k ukládání informací, můžete přepsat `OnApplyViewState` a přečtěte si tyto informace platí pro zobrazení, když je nově aktivován.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDocObjectServerItem – třída](../../mfc/reference/cdocobjectserveritem-class.md)
