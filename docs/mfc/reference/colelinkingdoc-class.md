---
title: Třída COleLinkingDoc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
dev_langs:
- C++
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe37e1a159fa0138c237b58ffbd622292dcba714
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369844"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc – třída
Základní třída pro dokumenty kontejneru OLE, které podporují propojování vložené položky, které obsahují.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleLinkingDoc : public COleDocument  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|Vytvoří `COleLinkingDoc` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleLinkingDoc::Register](#register)|Registruje dokumentu OLE systémové knihovny DLL.|  
|[COleLinkingDoc::Revoke](#revoke)|Odvolá registrace dokumentu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Vyhledá zadané vložené položky.|  
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Vyhledá zadaný propojené položky.|  
  
## <a name="remarks"></a>Poznámky  
 Kontejner aplikace, která podporuje propojování vložené položky se nazývá "kontejner odkaz". [OCLIENT](../../visual-cpp-samples.md) vzorová aplikace je příkladem kontejner odkaz.  
  
 Pokud je zdroj propojené položky položku vložené do jiného dokumentu, musí být načteny dokument obsahující vložený položka k provádění úprav. Z tohoto důvodu musí být odkaz kontejner moci být spuštěn jinou aplikací kontejneru, když chce uživatel upravit zdroj propojené položky. Aplikace také musí použít [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) třídy tak, aby mohl vytvořit dokumenty při spuštění prostřednictvím kódu programu.  
  
 Chcete-li vaše kontejneru kontejner odkaz, odvozena třídě dokumentu z `COleLinkingDoc` místo [COleDocument](../../mfc/reference/coledocument-class.md). Stejně jako u jiných OLE kontejneru, je třeba navrhnout třídě pro ukládání aplikace nativní data a také vložené nebo propojené položky. Také je třeba navrhnout datové struktury pro ukládání dat nativní. Pokud definujete `CDocItem`-odvozené třídy pro vaše aplikace nativní data, můžete použít rozhraní definované `COleDocument` k uložení nativní data a také OLE data.  
  
 Povolit aplikaci do jiného kontejneru být spuštěn prostřednictvím kódu programu, deklarovat `COleTemplateServer` objektu jako člen vaší aplikace `CWinApp`-odvozené třídy:  
  
 [!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]  
  
 V `InitInstance` členské funkce vaše `CWinApp`-odvozené třídy, vytvořit šablonu dokumentu a zadejte vaše `COleLinkingDoc`-odvozené třídy jako třída dokumentu:  
  
 [!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]  
  
 Připojit vaše `COleTemplateServer` objekt, který má vaše šablony dokumentu voláním objektu `ConnectTemplate` – členská funkce a všechny třídy objektů pomocí systému OLE voláním registrace **COleTemplateServer::RegisterAll**:  
  
 [!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]  
  
 Pro ukázku `CWinApp`-odvozené definice třídy a `InitInstance` funkce najdete v tématu OCLIENT. H a OCLIENT. CPP v ukázce MFC [OCLIENT](../../visual-cpp-samples.md).  
  
 Další informace o používání `COleLinkingDoc`, najdete v článcích [kontejnery: Implementace kontejneru](../../mfc/containers-implementing-a-container.md) a [kontejnery: pokročilé funkce](../../mfc/containers-advanced-features.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 `COleLinkingDoc`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="colelinkingdoc"></a>  COleLinkingDoc::COleLinkingDoc  
 Vytvoří `COleLinkingDoc` objektu bez od komunikace se službou OLE systémové knihovny DLL.  
  
```  
COleLinkingDoc();
```  
  
### <a name="remarks"></a>Poznámky  
 Je třeba zavolat `Register` – členská funkce OLE informovat, že dokument je otevřené.  
  
##  <a name="onfindembeddeditem"></a>  COleLinkingDoc::OnFindEmbeddedItem  
 Voláno rámcem k určení, zda dokument obsahuje vložené položky OLE se zadaným názvem.  
  
```  
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszItemName`  
 Ukazatel na název embedded OLE požadovaná položka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zadanou položku; **NULL** Pokud položka není nalezena.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace vyhledá seznam vložených položek pro položku se zadaným názvem (název porovnání se velká a malá písmena). Tato funkce přepsání, pokud máte vlastní metodu ukládání nebo pojmenování vložené položky OLE.  
  
##  <a name="ongetlinkeditem"></a>  COleLinkingDoc::OnGetLinkedItem  
 Voláno rámcem zkontrolujte, zda dokument obsahuje odkazovaný server položku se zadaným názvem.  
  
```  
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszItemName`  
 Ukazatel na název propojené OLE požadovaná položka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zadanou položku; **NULL** Pokud položka není nalezena.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí hodnota `COleLinkingDoc` implementace vždy vrátí **NULL**. Tato funkce je elementem v odvozené třídě `COleServerDoc` k vyhledání seznam položek OLE serveru pro propojené položky se zadaným názvem (název porovnání se velká a malá písmena). Tato funkce přepsání, pokud jste implementovali vlastní metodu ukládání nebo načítání položek odkazovaný server.  
  
##  <a name="register"></a>  COleLinkingDoc::Register  
 Informuje o OLE systémové knihovny DLL, že dokument je otevřené.  
  
```  
BOOL Register(
    COleObjectFactory* pFactory,  
    LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parametry  
 *pFactory*  
 Ukazatele na objekt factory OLE (může být **NULL**).  
  
 `lpszPathName`  
 Ukazatel na plně kvalifikovanou cestu dokument kontejneru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je zaregistrován úspěšně dokumentu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce při vytváření nebo otevírání souboru s názvem k registraci dokumentu systému OLE knihovny DLL. Není nutné pro volání této funkce, pokud dokument představuje vložené položky.  
  
 Pokud používáte `COleTemplateServer` ve vaší aplikaci, `Register` je volána pro vám `COleLinkingDoc`na implementaci `OnNewDocument`, `OnOpenDocument`, a `OnSaveDocument`.  
  
##  <a name="revoke"></a>  COleLinkingDoc::Revoke  
 Informuje o OLE systémové knihovny DLL, že dokument je již otevřený.  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce zrušení registrace dokumentu pomocí OLE systémové knihovny DLL.  
  
 Tato funkce by měly volat, při zavření soubor s názvem, ale obvykle není potřeba volat přímo. `Revoke` je volána pro vám `COleLinkingDoc`na implementaci `OnCloseDocument`, `OnNewDocument`, `OnOpenDocument`, a `OnSaveDocument`.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC OCLIENT](../../visual-cpp-samples.md)   
 [COleDocument – třída](../../mfc/reference/coledocument-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)
