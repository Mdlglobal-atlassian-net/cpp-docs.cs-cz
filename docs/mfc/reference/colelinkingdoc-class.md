---
title: COleLinkingDoc Class
ms.date: 11/04/2016
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
ms.openlocfilehash: c5076ceef0c6626fac0232fadf6818edd78b4ccf
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773551"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc Class

Základní třída pro kontejnerové dokumenty OLE, které podporují propojování na vložené položky, které obsahují.

## <a name="syntax"></a>Syntaxe

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|Vytvoří `COleLinkingDoc` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleLinkingDoc::Register](#register)|Registruje dokumentu OLE systémové knihovny DLL.|
|[COleLinkingDoc::Revoke](#revoke)|Odvolá registrace dokumentu.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Vyhledá určitou vloženou položku.|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Vyhledá určitou propojenou položku.|

## <a name="remarks"></a>Poznámky

Aplikace typu kontejner, který podporuje propojování vložené položky se nazývá "kontejner propojení". [OCLIENT](../../overview/visual-cpp-samples.md) ukázkové aplikace je příkladem kontejner odkaz.

Pokud je zdrojem propojená položka vložená položka v jiném dokumentu, obsahující dokumentu musí být načten v pořadí pro vloženou položku upravit. Z tohoto důvodu musí být schopni spustit jinou aplikací kontejneru, když chce uživatel upravit zdroj propojená položka kontejner odkaz. Aplikaci musíte taky použít [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) třídy tak, že může vytvářet dokumenty při spuštění prostřednictvím kódu programu.

Chcete-li váš kontejner kontejner odkaz, odvodit vaše dokumentové třídy z `COleLinkingDoc` místo [coledocument –](../../mfc/reference/coledocument-class.md). Stejně jako u jiných kontejneru OLE je třeba navrhnout vaše třída pro ukládání aplikace nativní dat stejně jako vložené nebo propojené položky. Kromě toho je třeba navrhnout datové struktury pro ukládání dat nativní. Při definování `CDocItem`-odvozené třídy pro aplikace nativní data, můžete použít rozhraní definované `COleDocument` k uložení nativní data i OLE data.

Chcete-li, aby vaše aplikace spustí jiný kontejner prostřednictvím kódu programu, deklarujte `COleTemplateServer` objektu jako člen vaší aplikace `CWinApp`-odvozené třídy:

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

V `InitInstance` členskou funkci vaše `CWinApp`-odvozené třídy, vytvořit šablonu dokumentu a zadejte vaše `COleLinkingDoc`-odvozené třídy jako třída dokumentu:

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

Připojení vaší `COleTemplateServer` objektu do dokumentu šablon voláním objektu `ConnectTemplate` členské funkce a zaregistrujte všechny třídy objektů OLE systému voláním `COleTemplateServer::RegisterAll`:

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

Pro ukázku `CWinApp`-odvozené třídy definice a `InitInstance` funkce naleznete v tématu OCLIENT. H a OCLIENT. CPP v ukázce MFC [OCLIENT](../../overview/visual-cpp-samples.md).

Další informace o používání `COleLinkingDoc`, najdete v článcích [kontejnerů: Implementace kontejneru](../../mfc/containers-implementing-a-container.md) a [kontejnerů: Pokročilé funkce](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="colelinkingdoc"></a>  COleLinkingDoc::COleLinkingDoc

Vytvoří `COleLinkingDoc` objekt bez zahájení komunikace se službou OLE systémové knihovny DLL.

```
COleLinkingDoc();
```

### <a name="remarks"></a>Poznámky

Je třeba zavolat `Register` členskou funkci OLE informovat, že dokument je otevřen.

##  <a name="onfindembeddeditem"></a>  COleLinkingDoc::OnFindEmbeddedItem

Volá se rozhraním, aby určilo, jestli dokument obsahuje vložené položky OLE se zadaným názvem.

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Ukazatel na název vložený požadované položky OLE.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na určenou položku; Hodnota NULL, pokud položka není nalezena.

### <a name="remarks"></a>Poznámky

Výchozí implementace vyhledá seznam vložených položek pro položku se zadaným názvem (název porovnání je velká a malá písmena). Tato funkce přepište, pokud máte vlastní způsob ukládání nebo pojmenování vložené položky OLE.

##  <a name="ongetlinkeditem"></a>  COleLinkingDoc::OnGetLinkedItem

Volá se rozhraním, chcete-li zkontrolovat, jestli dokument obsahuje odkazovaný server položku se zadaným názvem.

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Ukazatel na název propojené požadované položky OLE.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na určenou položku; Hodnota NULL, pokud položka není nalezena.

### <a name="remarks"></a>Poznámky

Výchozí hodnota `COleLinkingDoc` implementace vždy vrátí hodnotu NULL. Tato funkce je přepsat v odvozené třídě `COleServerDoc` pro prohledání seznamu položek serveru OLE pro propojenou položku se zadaným názvem (název porovnání je velká a malá písmena). Tato funkce přepište, pokud jste implementovali vlastní způsob ukládání nebo načítání položek odkazovaný server.

##  <a name="register"></a>  COleLinkingDoc::Register

Informuje o OLE systémové knihovny DLL, že dokument je otevřen.

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*pFactory*<br/>
Ukazatel na objekt factory OLE (může mít hodnotu NULL).

*lpszPathName*<br/>
Ukazatel na plně kvalifikovanou cestu dokumentu kontejneru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dokument je úspěšně zaregistrovaný; jinak 0.

### <a name="remarks"></a>Poznámky

Voláním této funkce při vytváření nebo otevírání souboru s názvem k registraci dokumentu OLE systému knihovny DLL. Není nutné volat tuto funkci, pokud dokument představuje vloženou položku.

Pokud používáte `COleTemplateServer` ve vaší aplikaci `Register` nazývá aplikací `COleLinkingDoc`vaší implementace `OnNewDocument`, `OnOpenDocument`, a `OnSaveDocument`.

##  <a name="revoke"></a>  COleLinkingDoc::Revoke

Informuje o OLE systémové knihovny DLL, že dokument je už otevřené.

```
void Revoke();
```

### <a name="remarks"></a>Poznámky

Voláním této funkce zrušení registrace dokumentu OLE systémové knihovny DLL.

Při zavírání souboru s názvem byste měli volat tuto funkci, ale obvykle není potřeba volat přímo. `Revoke` volá se pro vás od `COleLinkingDoc`vaší implementace `OnCloseDocument`, `OnNewDocument`, `OnOpenDocument`, a `OnSaveDocument`.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument – třída](../../mfc/reference/coledocument-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)
