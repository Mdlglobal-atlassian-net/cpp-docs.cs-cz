---
title: Třída COleLinkingDoc
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
ms.openlocfilehash: 1fad986b7e7304075cacb0b5ced9feeb8af4664f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753850"
---
# <a name="colelinkingdoc-class"></a>Třída COleLinkingDoc

Základní třída pro dokumenty kontejneru OLE, které podporují propojení s vložené položky, které obsahují.

## <a name="syntax"></a>Syntaxe

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|Vytvoří `COleLinkingDoc` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleLinkingDoc::Registrovat](#register)|Zaregistruje dokument u knihoven DLL systému OLE.|
|[COleLinkingDoc::Odvolat](#revoke)|Odvolá registraci dokumentu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Najde zadanou vloženou položku.|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Vyhledá zadanou propojenou položku.|

## <a name="remarks"></a>Poznámky

Kontejner aplikace, která podporuje propojení na vložené položky se nazývá "kontejner propojení." Ukázková aplikace [OCLIENT](../../overview/visual-cpp-samples.md) je příkladem kontejneru propojení.

Pokud je zdrojem propojené položky vložená položka v jiném dokumentu, musí být tato položka obsahující dokument načtena, aby mohla být vložená položka upravena. Z tohoto důvodu musí být kontejner propojení možné spustit jinou aplikací kontejneru, když uživatel chce upravit zdroj propojené položky. Aplikace musí také použít [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) třídy tak, aby bylo možné vytvářet dokumenty při spuštění programově.

Chcete-li, aby váš kontejner propojení `COleLinkingDoc` kontejneru, odvodit třídu dokumentu z místo [COleDocument](../../mfc/reference/coledocument-class.md). Stejně jako u jiných kontejnerů OLE, musíte navrhnout třídu pro ukládání nativních dat aplikace, stejně jako vložené nebo propojené položky. Je také nutné navrhnout datové struktury pro ukládání nativních dat. Pokud definujete `CDocItem`-derived třídy pro nativní data vaší aplikace, `COleDocument` můžete použít rozhraní definované k ukládání nativní data, stejně jako data OLE.

Chcete-li povolit programové spuštění aplikace jiným `COleTemplateServer` kontejnerem, deklarujte `CWinApp`objekt jako člen odvozené třídy aplikace:

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

V `InitInstance` členské funkci `CWinApp`vaší odvozené třídy vytvořte šablonu dokumentu a zadejte `COleLinkingDoc`odvozenou třídu jako třídu dokumentu:

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

Připojte `COleTemplateServer` objekt k šablonám dokumentů voláním `ConnectTemplate` členské funkce objektu a zaregistrujte všechny `COleTemplateServer::RegisterAll`objekty třídy se systémem OLE voláním :

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

Ukázka `CWinApp`definice a `InitInstance` funkce odvozené třídy naleznete v tématu OCLIENT. H a OCLIENT. CPP ve vzorku Knihovny [MFC OCLIENT](../../overview/visual-cpp-samples.md).

Další informace o `COleLinkingDoc`použití naleznete v článcích [Kontejnery: Implementace kontejneru](../../mfc/containers-implementing-a-container.md) a [kontejnerů: Rozšířené funkce](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[CDokument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="colelinkingdoccolelinkingdoc"></a><a name="colelinkingdoc"></a>COleLinkingDoc::COleLinkingDoc

Vytvoří `COleLinkingDoc` objekt bez zahájení komunikace se systémovými knihovnami OLE.

```
COleLinkingDoc();
```

### <a name="remarks"></a>Poznámky

Je nutné `Register` volat členskou funkci informovat OLE, že dokument je otevřen.

## <a name="colelinkingdoconfindembeddeditem"></a><a name="onfindembeddeditem"></a>COleLinkingDoc::OnFindEmbeddedItem

Volat rámci k určení, zda dokument obsahuje vložené položky OLE se zadaným názvem.

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Ukazatel na název požadované vložené položky OLE.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zadanou položku; Null, pokud položka nebyla nalezena.

### <a name="remarks"></a>Poznámky

Výchozí implementace prohledá seznam vložených položek pro položku se zadaným názvem (porovnání názvů rozlišuje malá a velká písmena). Přepsat tuto funkci, pokud máte vlastní metodu ukládání nebo pojmenování vložené položky OLE.

## <a name="colelinkingdocongetlinkeditem"></a><a name="ongetlinkeditem"></a>COleLinkingDoc::OnGetLinkedItem

Volat rámci ke kontrole, zda dokument obsahuje položku propojeného serveru se zadaným názvem.

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Ukazatel na název požadované propojené položky OLE.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zadanou položku; Null, pokud položka nebyla nalezena.

### <a name="remarks"></a>Poznámky

Výchozí `COleLinkingDoc` implementace vždy vrátí hodnotu NULL. Tato funkce je přepsána v `COleServerDoc` odvozené třídě a vyhledává v seznamu položek serveru OLE propojené položky se zadaným názvem (porovnání názvů rozlišuje malá a velká písmena). Tuto funkci přepište, pokud jste implementovali vlastní metodu ukládání nebo načítání propojených položek serveru.

## <a name="colelinkingdocregister"></a><a name="register"></a>COleLinkingDoc::Registrovat

Informuje knihovny DLL systému OLE, že dokument je otevřen.

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*pFactory*<br/>
Ukazatel na objekt objektu objektu objektu objektu objektu objektu ole (může být NULL).

*lpszPathName*<br/>
Ukazatel na plně kvalifikovanou cestu dokumentu kontejneru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je dokument úspěšně zaregistrován; jinak 0.

### <a name="remarks"></a>Poznámky

Tuto funkci volání při vytváření nebo otevírání pojmenovaného souboru pro registraci dokumentu u knihoven DLL systému OLE. Není nutné volat tuto funkci, pokud dokument představuje vloženou položku.

Pokud používáte `COleTemplateServer` ve své `Register` aplikaci, `COleLinkingDoc`je volána `OnNewDocument` `OnOpenDocument`pro `OnSaveDocument`vás 's provádění , a .

## <a name="colelinkingdocrevoke"></a><a name="revoke"></a>COleLinkingDoc::Odvolat

Informuje knihovny DLL systému OLE, že dokument již není otevřen.

```cpp
void Revoke();
```

### <a name="remarks"></a>Poznámky

Volánítéto funkce odvolat registraci dokumentu s knihovnami DLL systému OLE.

Tuto funkci byste měli volat při zavírání pojmenovaného souboru, ale obvykle ji nemusíte volat přímo. `Revoke`je pro vás `COleLinkingDoc`volána `OnCloseDocument`implementací , `OnNewDocument`, `OnOpenDocument`a `OnSaveDocument`.

## <a name="see-also"></a>Viz také

[OKLIENT ukázkový příklad knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[Třída COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CDocTemplate](../../mfc/reference/cdoctemplate-class.md)
