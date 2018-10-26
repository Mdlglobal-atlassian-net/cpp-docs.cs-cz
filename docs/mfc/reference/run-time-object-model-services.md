---
title: Služby modelu běhového objektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5979fcb76dc688bffd9ad8076f123927439e3840
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064561"
---
# <a name="run-time-object-model-services"></a>Služby modelu běhového objektu

Třídy [CObject](../../mfc/reference/cobject-class.md) a [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) zapouzdření několik objektů služeb, včetně přístupu k informacím o třídě za běhu, serializace a vytváření dynamických objektů. Všechny třídy odvozené z `CObject` dědí tuto funkci.

Přístup k informacím o třídě za běhu umožňuje určit informace o třídě objektu v době běhu. Schopnost určit třídu objektu v době běhu je užitečné, když budete potřebovat další kontroly typů argumentů funkce a je nutné napsat kód zvláštní účely na základě třídy objektu. Informace o třídě za běhu se nepodporuje přímo v jazyce C++.

Serializace je proces zápisu nebo čtení objektu obsah do nebo ze souboru. Serializace slouží k uložení objektu obsahu i po ukončení aplikace. Objekt lze poté číst ze souboru se aplikace restartuje. Tyto datové objekty se označují jako "trvalé."

Vytváření dynamických objektů můžete vytvořit objekt z dané třídy v době běhu. Například musí podporovat dokumentu, zobrazení a rámečku objekty dynamické vytváření vzhledem k tomu potřeba dynamicky vytvořit rozhraní framework.

Následující tabulka uvádí, které podporují run-time třída informace, serializace a dynamické vytváření makra MFC.

Další informace o těchto služeb run-time objekt a serializaci, najdete v článku [CObject – třída: přístup k informacím o třídě Run-Time](../../mfc/accessing-run-time-class-information.md).

### <a name="run-time-object-model-services-macros"></a>Makra služeb modelu běhového objektu

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Umožňuje přístup k informacím o třídě za běhu (musí se použít v deklaraci třídy).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|Umožňuje dynamické vytváření a přístup k informacím o třídě za běhu (musí se použít v deklaraci třídy).|
|[DECLARE_SERIAL](#declare_serial)|Umožňuje serializace a přístup k informacím o třídě za běhu (musí se použít v deklaraci třídy).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Umožňuje přístup k informacím o třídě za běhu (musí být použitý v implementaci třídy).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Umožňuje dynamické vytváření a přístup k informacím o za běhu (musí být použitý v implementaci třídy).|
|[IMPLEMENT_SERIAL](#implement_serial)|Povolení serializace a přístup k informacím o třídě za běhu (musí být použitý v implementaci třídy).|
|[RUNTIME_CLASS](#runtime_class)|Vrátí `CRuntimeClass` struktura, která odpovídá definované třídě.|

OLE – často vyžaduje dynamické vytváření objektů za běhu. Aplikace serveru OLE musí být například schopné dynamicky vytvořit položky OLE v reakci na požadavek od klienta. Podobně automatizační server musí být schopen vytvořit položky v reakci na požadavky klientů automatizace.

Knihovny Microsoft Foundation Class poskytuje dvě makra, které jsou specifické pro OLE.

### <a name="dynamic-creation-of-ole-objects"></a>Dynamické vytváření objekty OLE

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Určuje, zda knihovny běžných ovládacích prvků implementuje zadané rozhraní API.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Určuje, zda knihovny běžných ovládacích prvků implementuje zadané rozhraní API.|
|[DECLARE_OLECREATE](#declare_olecreate)|Umožňuje objekty být vytvořeny prostřednictvím automatizace OLE.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Deklaruje `GetUserTypeNameID` a `GetMiscStatus` členské funkce třídy vašeho ovládacího prvku.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Deklaruje, že ovládací prvek OLE obsahuje seznam stránek vlastností zobrazíte jeho vlastnosti.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Umožňuje objektů OLE systému.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementuje `GetUserTypeNameID` a `GetMiscStatus` členské funkce třídy vašeho ovládacího prvku.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Buď toto makro nebo [IMPLEMENT_OLECREATE](#implement_olecreate) musí být uvedena v souboru implementace pro třídy, které používá `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a> AFX_COMCTL32_IF_EXISTS

Určuje, zda knihovny běžných ovládacích prvků implementuje zadané rozhraní API.

### <a name="syntax"></a>Syntaxe

  ```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Parametry

*proc*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název funkce nebo určuje pořadové číslo funkce. Pokud tento parametr je pořadové číslo, musí být v nižší řád slova; vyšší řád slova musí být nula. Tento parametr musí být v kódování Unicode.

### <a name="remarks"></a>Poznámky

Použijte toto makro k určení, zda knihovny běžných ovládacích prvků funkci určené *proc* (namísto volání metody [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Požadavky

afxcomctl32.h, afxcomctl32.inl

### <a name="see-also"></a>Viz také

[Izolace knihovny běžných ovládacích prvků MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)

## <a name="afx_comctl32_if_exists2"></a>  AFX_COMCTL32_IF_EXISTS2

Určuje, zda knihovny běžných ovládacích prvků implementuje zadané rozhraní API (Toto je verze Unicode [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Syntaxe

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Parametry

*proc*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název funkce nebo určuje pořadové číslo funkce. Pokud tento parametr je pořadové číslo, musí být v nižší řád slova; vyšší řád slova musí být nula. Tento parametr musí být v kódování Unicode.

### <a name="remarks"></a>Poznámky

Použijte toto makro k určení, zda knihovny běžných ovládacích prvků funkci určené *proc* (namísto volání metody [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress). Toto makro je verzi AFX_COMCTL32_IF_EXISTS kódování Unicode.

### <a name="requirements"></a>Požadavky

afxcomctl32.h, afxcomctl32.inl

### <a name="see-also"></a>Viz také

[Izolace knihovny běžných ovládacích prvků MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)

##  <a name="declare_dynamic"></a>  DECLARE_DYNAMIC

Přidá schopnost přístupu k běhových informací o třídě objektu při odvození třídy z `CObject`.

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Přidejte DECLARE_DYNAMIC – makro do modulu hlaviček (.h) pro třídu, pak zahrnutí tohoto modulu ve všech modulech .cpp, které potřebují přístup k objektům této třídy.

Pokud používáte DECLARE_ dynamické a IMPLEMENT_DYNAMIC makra, jak je popsáno, můžete pak použít makra RUNTIME_CLASS a `CObject::IsKindOf` funkce určit třídu objektů za běhu.

DECLARE_DYNAMIC je zahrnuta v deklaraci třídy, musí IMPLEMENT_DYNAMIC zahrnuta v implementaci třídy.

Další informace o DECLARE_DYNAMIC – makro najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="declare_dyncreate"></a>  DECLARE_DYNCREATE

Umožňuje objekty `CObject`-odvozené třídy, které se dají vytvářet dynamicky za běhu.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Rozhraní používá tuto možnost k vytváření nových objektů dynamicky. Například nové zobrazení vytvořené po otevření nový dokument. Dokumentu, zobrazení a rámečku třídy by měly podporovat dynamické vytváření, protože rozhraní je potřeba dynamicky vytvořit.

DECLARE_DYNCREATE – makro modulu .h třídy, přidejte do tohoto modulu zahrnout všechny moduly .cpp, které potřebují přístup k objektům této třídy.

DECLARE_DYNCREATE je zahrnuta v deklaraci třídy, musí IMPLEMENT_DYNCREATE zahrnuta v implementaci třídy.

Další informace o DECLARE_DYNCREATE – makro najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).

> [!NOTE]
>  DECLARE_DYNCREATE – makro zahrnuje všechny funkce, které jsou součástí DECLARE_DYNAMIC.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="declareolectltype"></a>DECLARE_OLECTLTYPE

Deklaruje `GetUserTypeNameID` a `GetMiscStatus` členské funkce třídy vašeho ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Název třídy ovládacího prvku.

### <a name="remarks"></a>Poznámky

`GetUserTypeNameID` a `GetMiscStatus` jsou čistě virtuální funkce, deklarované v `COleControl`. Protože tyto funkce jsou čistě virtuální, že se musí přepsat ve třídě ovládacího prvku. Kromě DECLARE_OLECTLTYPE musíte přidat IMPLEMENT_OLECTLTYPE – makro do deklarace třídy ovládacího prvku.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

### <a name="see-also"></a>Viz také

[IMPLEMENT_OLECTLTYPE](#implement_olectltype)

## <a name="declareproppageids"></a>DECLARE_PROPPAGEIDS

Deklaruje, že ovládací prvek OLE obsahuje seznam stránek vlastností zobrazíte jeho vlastnosti.

### <a name="syntax"></a>Syntaxe

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Název třídy ovládacího prvku, který vlastní stránky vlastností.

### <a name="remarks"></a>Poznámky

Použití `DECLARE_PROPPAGEIDS` – makro na konci deklaraci vaší třídy. Potom v souboru .cpp, který definuje členské funkce třídy, použijte `BEGIN_PROPPAGEIDS` – makro, makro položky pro všechny stránky vlastností ovládacího prvku a `END_PROPPAGEIDS` – makro, chcete-li deklarovat konec stránky seznamu vlastností.

Další informace na stránkách vlastností, najdete v článku [ovládací prvky ActiveX: stránky vlastností](../mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

### <a name="see-also"></a>Viz také

[BEGIN_PROPPAGEIDS](#begin_proppageids)<br/>
[END_PROPPAGEIDS](#end_proppageids)

##  <a name="declare_serial"></a>  DECLARE_SERIAL

Generuje záhlaví kódu jazyka C++, které jsou nezbytné pro `CObject`-odvozené třídy, který lze serializovat.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Serializace je proces zápisu nebo čtení obsahu objektu do a ze souboru.

Použít v modulu .h DECLARE_SERIAL – makro a potom vložte Tenhle modul ve všech modulech .cpp, které potřebují přístup k objektům této třídy.

DECLARE_SERIAL je zahrnuta v deklaraci třídy, musí IMPLEMENT_SERIAL zahrnuta v implementaci třídy.

DECLARE_SERIAL – makro zahrnuje všechny funkce DECLARE_DYNAMIC a DECLARE_DYNCREATE.

Můžete použít makra AFX_API automaticky export `CArchive` operátor extrakce pro třídy, které používají DECLARE_SERIAL a IMPLEMENT_SERIAL makra. Párování deklarace tříd (umístěný v souboru .h) následujícím kódem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Další informace o DECLARE_SERIAL – makro najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="implement_dynamic"></a>  IMPLEMENT_DYNAMIC

Generuje kód C++ pro dynamickou `CObject`-odvozené třídy za běhu přístup k názvu třídy a pozici v rámci hierarchie.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Skutečný název třídy.

*BASE_CLASS_NAME*<br/>
Název základní třídy.

### <a name="remarks"></a>Poznámky

V modulu .cpp použít IMPLEMENT_DYNAMIC – makro a propojit kód výsledný objekt pouze jednou.

Další informace najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="implement_dyncreate"></a>  IMPLEMENT_DYNCREATE

Umožňuje objekty `CObject`-odvozené třídy, které se dají vytvářet dynamicky za běhu času při použití s DECLARE_DYNCREATE – makro.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Skutečný název třídy.

*BASE_CLASS_NAME*<br/>
Skutečný název základní třídy.

### <a name="remarks"></a>Poznámky

Rozhraní používá tuto možnost k vytváření nových objektů dynamicky, například když načte objekt z disku během serializace. Přidání IMPLEMENT_DYNCREATE – makro v souboru implementace třídy. Další informace najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).

Pokud používáte makra DECLARE_DYNCREATE a IMPLEMENT_DYNCREATE, pak můžete použít makra RUNTIME_CLASS a `CObject::IsKindOf` členské funkce určit třídu objektů za běhu.

DECLARE_DYNCREATE je zahrnuta v deklaraci třídy, musí IMPLEMENT_DYNCREATE zahrnuta v implementaci třídy.

Všimněte si, že tato definice makra vyvolají výchozí konstruktor pro třídu. Pokud nejsou v netriviálních konstruktor explicitně implementované třídou, musí také explicitně implementovat výchozí konstruktor. Výchozího konstruktoru mohou být přidány do třídy **privátní** nebo **chráněné** člen části tak, aby volaný ze mimo implementaci třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="implement_olecreate_flags"></a>  IMPLEMENT_OLECREATE_FLAGS

Buď toto makro nebo [IMPLEMENT_OLECREATE](#implement_olecreate) musí být uvedena v souboru implementace pro třídy, které používá DECLARE_OLECREATE.

### <a name="syntax"></a>Syntaxe

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)

```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Skutečný název třídy.

*external_name*<br/>
Název objektu, zpřístupnit jiným aplikacím (uzavřena v uvozovkách).

*nFlags*<br/>
Obsahuje jeden nebo více z následujících příznaků:

   - `afxRegInsertable` Umožňuje ovládacímu prvku se zobrazí v dialogovém okně Vložit objekt pro objekty OLE.
   - `afxRegApartmentThreading` Nastaví model vláken v registru ThreadingModel = objektu Apartment.
   - `afxRegFreeThreading` Nastaví model vláken v registru ThreadingModel = Free.

         You can combine the two flags `afxRegApartmentThreading` and `afxRegFreeThreading` to set ThreadingModel=Both. See [InprocServer32](/windows/desktop/com/inprocserver32) in the Windows SDK for more information on threading model registration.

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4* , *b5*, *b6*, *b7*, *b8* součástí CLSID pro třídu.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud používáte IMPLEMENT_OLECREATE_FLAGS, které model vláken pomocí podporovány vašim objektem můžete zadat *nFlags* parametru. Pokud chcete zajistit podporu pouze jedné chůze model, použijte IMPLEMENT_OLECREATE.

Externí název je identifikátor, zpřístupnit jiným aplikacím. Klientské aplikace použít externí název pro žádost o objekt této třídy ze serveru automatizace.

ID třídy OLE je jedinečný identifikátor 128 bitů pro objekt. Se skládá z jednoho **dlouhé**, dva **slovo**s a osm **BAJTŮ**s reprezentovaná *l*, *w1*, *w2*, a *b1* prostřednictvím *b8* v popisu syntaxe. Průvodci Průvodce aplikací a kódu vytvořit jedinečný ID tříd OLE podle potřeby.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

### <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[DECLARE_OLECREATE](#declare_olecreate)<br/>
[Klíč CLSID](/windows/desktop/com/clsid-key-hklm)

## <a name="implement_olecreate"></a> IMPLEMENT_OLECTLTYPE

Implementuje `GetUserTypeNameID` a `GetMiscStatus` členské funkce třídy vašeho ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Název třídy ovládacího prvku.

*idsUserTypeName*<br/>
ID prostředku řetězce obsahující externí název ovládacího prvku.

*dwOleMisc*<br/>
Výčet obsahující jeden nebo více příznaků. Další informace o tomto výčtu, naleznete v tématu [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Kromě IMPLEMENT_OLECTLTYPE musíte přidat DECLARE_OLECTLTYPE – makro do deklarace třídy ovládacího prvku.

`GetUserTypeNameID` Členská funkce vrátí řetězec prostředku, který identifikuje třídy vašeho ovládacího prvku. `GetMiscStatus` Vrátí OLEMISC bity ovládacího prvku. Tento výčet Určuje soubor nastavení popisující různé vlastnosti ovládacího prvku. Úplný popis OLEMISC nastavení najdete v tématu [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) v sadě Windows SDK.

> [!NOTE]
>  Výchozí nastavení používané ActiveX ControlWizard: OLEMISC_ACTIVATEWHENVISIBLE OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE a OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

### <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[DECLARE_OLECTLTYPE](#declare_olectltype)

##  <a name="implement_serial"></a>  IMPLEMENT_SERIAL

Generuje kód C++ pro dynamickou `CObject`-odvozené třídy za běhu přístup k názvu třídy a pozici v rámci hierarchie.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Skutečný název třídy.

*BASE_CLASS_NAME*<br/>
Název základní třídy.

*wSchema*<br/>
UINT "číslo verze", který bude zakódován v archivní úrovni umožňuje deserializaci programu pro identifikaci a zpracovat data vytvořená programu starší verze. Číslo schéma třídy nesmí být -1.

### <a name="remarks"></a>Poznámky

V modulu .cpp; použít IMPLEMENT_SERIAL – makro potom propojte výsledný kód objektu pouze jednou.

Můžete použít makra AFX_API automaticky export `CArchive` operátor extrakce pro třídy, které používají DECLARE_SERIAL a IMPLEMENT_SERIAL makra. Párování deklarace tříd (umístěný v souboru .h) následujícím kódem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Další informace najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="runtime_class"></a>  RUNTIME_CLASS

Získá strukturu run-time třída od názvu třídy jazyka C++.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Skutečný název třídy (není uzavřená v uvozovkách).

### <a name="remarks"></a>Poznámky

RUNTIME_CLASS vrací ukazatel na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) strukturu pro třída určená typem *$class_name*. Pouze `CObject`-odvozené třídy deklarované s DECLARE_DYNAMIC, DECLARE_DYNCREATE nebo DECLARE_SERIAL vrátí ukazatele na `CRuntimeClass` struktury.

Další informace najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="declare_olecreate"></a>  DECLARE_OLECREATE

Umožňuje objekty `CCmdTarget`-odvozené třídy, který se má vytvořit pomocí automatizace OLE.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Toto makro umožňuje jiným aplikacím technologii OLE vytvářet objekty tohoto typu.

V modulu .h třídy přidat DECLARE_OLECREATE – makro a potom vložte Tenhle modul ve všech modulech .cpp, které potřebují přístup k objektům této třídy.

DECLARE_OLECREATE je zahrnuta v deklaraci třídy, musí IMPLEMENT_OLECREATE zahrnuta v implementaci třídy. Deklarace třídy pomocí DECLARE_OLECREATE musíte použít také DECLARE_DYNCREATE nebo DECLARE_SERIAL.

### <a name="requirements"></a>Požadavky

**Hlavička**: afxdisp.h

##  <a name="implement_olecreate"></a>  IMPLEMENT_OLECREATE

Buď toto makro nebo [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) musí být uvedena v souboru implementace pro třídy, které používá `DECLARE_OLECREATE`.

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Skutečný název třídy.

*external_name*<br/>
Název objektu, zpřístupnit jiným aplikacím (uzavřena v uvozovkách).

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4* , *b5*, *b6*, *b7*, *b8* součástí CLSID pro třídu.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud používáte IMPLEMENT_OLECREATE, ve výchozím nastavení, podporují pouze jeden model vláken. Pokud používáte IMPLEMENT_OLECREATE_FLAGS, které model vláken pomocí podporovány vašim objektem můžete zadat *nFlags* parametru.

Externí název je identifikátor, zpřístupnit jiným aplikacím. Klientské aplikace použít externí název pro žádost o objekt této třídy ze serveru automatizace.

ID třídy OLE je jedinečný identifikátor 128 bitů pro objekt. Se skládá z jednoho **dlouhé**, dva **slovo**s a osm **BAJTŮ**s reprezentovaná *l*, *w1*, *w2*, a *b1* prostřednictvím *b8* v popisu syntaxe. Průvodci Průvodce aplikací a kódu vytvořit jedinečný ID tříd OLE podle potřeby.

### <a name="requirements"></a>Požadavky

**Hlavička**: afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)

