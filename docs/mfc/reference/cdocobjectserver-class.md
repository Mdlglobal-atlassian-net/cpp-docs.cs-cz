---
title: Cdocobjectserver – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 701cfc2f8a88f57a1c50c9c4310ecd21154ef09a
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337863"
---
# <a name="cdocobjectserver-class"></a>Cdocobjectserver – třída
Implementuje další rozhraní OLE potřebná k normálního `COleDocument` server do úplné zcela DocObject server: `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`, a `IPrint`.  
  
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
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Aktivuje server objekt dokumentu, ale není uveden.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocObjectServer::OnActivateView](#onactivateview)|Zobrazí zobrazení DocObject.|  
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Obnoví stav zobrazení DocObject.|  
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Uloží stav zobrazení DocObject.|  
  
## <a name="remarks"></a>Poznámky  
 `CDocObjectServer` je odvozen z `CCmdTarget` a úzce spolupracuje s `COleServerDoc` vystavit rozhraní.  
  
 Dokument DocObject server může obsahovat [cdocobjectserveritem –](../../mfc/reference/cdocobjectserveritem-class.md) objekty, které představují rozhraní serveru položkám DocObject.  
  
 Pokud chcete přizpůsobit zcela DocObject server, odvodit vlastní třídu z `CDocObjectServer` a přepsat nastavení jeho zobrazení funkce [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate), a [OnSaveViewState ](#onsaveviewstate). Je potřeba zadat novou instanci třídy v reakci na volání rozhraní framework.  
  
 Další informace o DocObjects najdete v tématu [cdocobjectserveritem –](../../mfc/reference/cdocobjectserveritem-class.md) a [colecmdui –](../../mfc/reference/colecmdui-class.md) v *odkaz knihovny MFC*. Viz také [první kroky Internet: aktivní dokumenty](../../mfc/active-documents-on-the-internet.md) a [aktivní dokumenty](../../mfc/active-documents-on-the-internet.md).  
  
 Také naleznete v následujícím článku znalostní báze Knowledge Base:  
  
-   Q247382: PRB: popisky dat pro ovládací prvky ActiveX Dokumentovém serveru jsou skryté kontejnerem dokument ActiveX  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocObjectServer`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdocob.h  
  
##  <a name="activatedocobject"></a>  CDocObjectServer::ActivateDocObject  
 Voláním této funkce pro aktivaci (ale nezobrazovat) objektu serveru dokumentů.  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>Poznámky  
 `ActivateDocObject` volání `IOleDocumentSite`společnosti `ActivateMe` metody, ale nezobrazuje zobrazení, protože se čeká na konkrétní pokyny o tom, jak nastavit a zobrazení, zadaný ve volání [CDocObjectServer::OnActivateView](#onactivateview).  
  
 Společně `ActivateDocObject` a `OnActivateView` aktivovat a zobrazí zobrazení DocObject. Aktivace DocObject se liší od jiných typů OLE – aktivace na místě. Aktivace DocObject obchází zobrazení místní šrafování ohraničení a vylepšení objektu (například úchyty pro změnu velikosti), ignoruje objekt extent funkce a kreslení posuvníků v rámci zobrazení obdélník na rozdíl od kreslení mimo obdélníku (jako normální aktivace na místě).  
  
##  <a name="cdocobjectserver"></a>  CDocObjectServer::CDocObjectServer  
 Vytvoří a inicializuje `CDocObjectServer` objektu.  
  
```  
explicit CDocObjectServer(
    COleServerDoc* pOwner,  
    LPOLEDOCUMENTSITE pDocSite = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pOwner*  
 Ukazatel na dokument lokality klienta, který je klient zcela DocObject server.  
  
 *pDocSite*  
 Ukazatel `IOleDocumentSite` rozhraní implementované kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Při aktivním DocObject klienta lokality rozhraní OLE ( `IOleDocumentSite`) může zcela DocObject server ke komunikaci s jeho klienta (kontejneru). Jestliže zcela DocObject server je aktivován, nejprve ověří, že implementuje kontejneru `IOleDocumentSite` rozhraní. Pokud ano, [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) je volána, pokud chcete zobrazit, pokud kontejner podporuje DocObjects. Ve výchozím nastavení `GetDocObjectServer` vrátí hodnotu NULL. Je nutné přepsat `COleServerDoc::GetDocObjectServer` k vytvoření nového `CDocObjectServer` nebo odvozené objekt vlastní, ukazatelů na `COleServerDoc` kontejneru a jeho `IOleDocumentSite` rozhraní jako argumenty konstruktoru.  
  
##  <a name="onactivateview"></a>  CDocObjectServer::OnActivateView  
 Voláním této funkce zobrazí zobrazení DocObject.  
  
```  
virtual HRESULT OnActivateView();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí chybu nebo upozornění hodnotu. Ve výchozím nastavení, vrátí NOERROR v případě úspěchu; v opačném případě E_FAIL.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vytvoří okno rámečkem na místě, nakreslí posuvníky v rámci zobrazení, nastaví nabídky serveru sdílí s jejím kontejnerem, přidá ovládacích prvků rámce, nastaví aktivní objekt, a nakonec zobrazí okno rámečkem na místě a fokus se nastaví na.  
  
##  <a name="onapplyviewstate"></a>  CDocObjectServer::OnApplyViewState  
 Potlačí tuto funkci, který obnoví stav zobrazení DocObject.  
  
```  
virtual void OnApplyViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 *ar*  
 A `CArchive` objektu, ze kterého se má serializovat stavu zobrazení.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se volá při zobrazení se zobrazí poprvé po jeho vytvoření instance. `OnApplyViewState` dává pokyn inicializoval podle dat v zobrazení `CArchive` s dříve uložený objekt [OnSaveViewState](#onsaveviewstate). Zobrazení musí ověřit data `CArchive` objektu, protože kontejneru nebude pokoušet o interpretovat data stavu zobrazení žádným způsobem.  
  
 Můžete použít `OnSaveViewState` pro ukládání trvalých informace specifické pro zobrazení stavu. Pokud přepíšete `OnSaveViewState` k ukládání informací, se kterou chcete přepsat `OnApplyViewState` čtení těchto informací a použít ji k zobrazení nově při aktivaci.  
  
##  <a name="onsaveviewstate"></a>  CDocObjectServer::OnSaveViewState  
 Potlačí tuto funkci chcete-li uložit informace o zobrazení DocObject. navíc stavu.  
  
```  
virtual void OnSaveViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 *ar*  
 A `CArchive` objektu stav zobrazení je serializována.  
  
### <a name="remarks"></a>Poznámky  
 Stav svého může obsahovat vlastnosti, jako je typ zobrazení, faktor zvětšování, vložení a bod výběru a tak dále. Kontejner volá tuto funkci obvykle před deaktivaci zobrazení. Uložený stav lze později obnovit prostřednictvím [OnApplyViewState](#onapplyviewstate).  
  
 Můžete použít `OnSaveViewState` pro ukládání trvalých informace specifické pro zobrazení stavu. Pokud přepíšete `OnSaveViewState` k ukládání informací, se kterou chcete přepsat `OnApplyViewState` čtení těchto informací a použít ji k zobrazení nově při aktivaci.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDocObjectServerItem – třída](../../mfc/reference/cdocobjectserveritem-class.md)
