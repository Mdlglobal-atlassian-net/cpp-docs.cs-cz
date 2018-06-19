---
title: Třída COleTemplateServer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
dev_langs:
- C++
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90b24d65dbd6f800dda0b25088288bee6fdcf3c2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374380"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer – třída
Použít pro OLE visual úpravy servery, automatizační servery a kontejnery odkaz (aplikace, které podporují odkazy na vložené části).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleTemplateServer : public COleObjectFactory  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Vytvoří `COleTemplateServer` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Šablona dokumentu se připojuje k základní `COleObjectFactory` objektu.|  
|[COleTemplateServer::Unregister](#unregister)|Zruší registraci šablona přidružené dokumentu.|  
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Zaregistruje typ dokumentu s registrem systému OLE.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je odvozena od třídy [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); obvykle, můžete použít `COleTemplateServer` přímo místo odvození vlastní třídy. `COleTemplateServer` používá [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objekt ke správě dokumentů na serveru. Použití `COleTemplateServer` při implementaci celého serveru, který je server, který lze spustit jako samostatnou aplikaci. Úplné servery jsou obvykle více rozhraní (MDI) – aplikace dokumentů, i když jsou podporovány aplikace (SDI rozhraní) jednotlivý dokument. Jeden `COleTemplateServer` objektu je potřeba pro každý typ dokumentu serveru podporuje aplikace; to znamená, pokud vaše serverová aplikace podporuje listů a grafy, musíte mít dva `COleTemplateServer` objekty.  
  
 `COleTemplateServer` přepsání `OnCreateInstance` – členská funkce definované `COleObjectFactory`. Tento člen funkce je volána rámcem k vytvoření objektu C++ správné typu.  
  
 Další informace o serverech najdete v článku [servery: implementace serveru](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)  
  
 `COleTemplateServer`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
##  <a name="coletemplateserver"></a>  COleTemplateServer::COleTemplateServer  
 Vytvoří `COleTemplateServer` objektu.  
  
```  
COleTemplateServer();
```  
  
### <a name="remarks"></a>Poznámky  
 Stručný popis použití `COleTemplateServer` naleznete [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) přehledu třídy.  
  
##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate  
 Připojí šablona dokumentu, na kterou odkazuje `pDocTemplate` na odpovídající [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) objektu.  
  
```  
void ConnectTemplate(
    REFCLSID clsid,  
    CDocTemplate* pDocTemplate,  
    BOOL bMultiInstance);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 Odkaz na ID třídy OLE, které požadavky šablony.  
  
 `pDocTemplate`  
 Ukazatel na šabloně dokumentu.  
  
 `bMultiInstance`  
 Určuje, zda jednu instanci aplikace může podporovat více instancí. Pokud **TRUE**, pro každý požadavek pro vytvoření objektu je spuštěných víc instancí aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [klíč CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) ve Windows SDK.  
  
##  <a name="unregister"></a>  COleTemplateServer::Unregister  
 Zruší registraci šablona přidružené dokumentu.  
  
```  
BOOL Unregister();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je úspěšné; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 EnterRemarks  
  
##  <a name="updateregistry"></a>  COleTemplateServer::UpdateRegistry  
 Načte typ souboru informace z řetězce šablony dokumentu a umístí tyto informace v registru systému OLE.  
  
```  
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL,  
    BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nAppType`  
 Hodnota z **OLE_APPTYPE** výčtu, která je definována v AFXDISP. H. Může mít jednu z následujících hodnot:  
  
- `OAT_INPLACE_SERVER` Server má celého serveru uživatelského rozhraní.  
  
- `OAT_SERVER` Server podporuje jenom vkládání.  
  
- `OAT_CONTAINER` Kontejner podporuje odkazy na vložené objekty.  
  
- `OAT_DISPATCH_OBJECT` Objekt je `IDispatch`-podporující.  
  
- **OAT_DOC_OBJECT_SERVER** Server podporuje obě vložení a součástí modelu objektu dokumentu.  
  
 `rglpszRegister`  
 Seznam položek, které se zapíše do registru pouze v případě, že neexistují žádné položky.  
  
 `rglpszOverwrite`  
 Seznam položek, které se zapíše do registru bez ohledu na to, zda existují jakékoli předchozí položky.  
  
 `bRegister`  
 Určuje, zda třída je nutné zaregistrovat. Pokud `bRegister` je **TRUE**, třída není zaregistrována systémový registr. V opačném. zrušení registrace třídy.  
  
### <a name="remarks"></a>Poznámky  
 Informace o registraci je načten prostřednictvím volání [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Dílčích řetězců načíst odpovídají identifikovaný indexy **regFileTypeId**, **regFileTypeName**, a **fileNewName**, jak je popsáno v `GetDocString` — Referenční stránky.  
  
 Pokud **regFileTypeId** dílčí řetězec je prázdný nebo pokud volání `GetDocString` selže z jiného důvodu, tato funkce se nezdaří a informací o souboru není zadaný v registru.  
  
 Informace v argumenty `rglpszRegister` a `rglpszOverwrite` je zapsán do registru prostřednictvím volání [afxoleregisterserverclass –](application-control.md#afxoleregisterserverclass). Výchozí informace, která je registrována, pokud jsou dva argumenty **NULL**, je vhodná pro většinu aplikací. Informace o struktuře informace v těchto argumentů najdete v tématu `AfxOleRegisterServerClass`.  
  
 Další informace najdete v tématu [implementace rozhraní IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC HIERSVR](../../visual-cpp-samples.md)   
 [COleObjectFactory – třída](../../mfc/reference/coleobjectfactory-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)   
 [COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)
