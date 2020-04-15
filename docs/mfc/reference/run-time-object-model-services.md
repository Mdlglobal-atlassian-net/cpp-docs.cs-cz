---
title: Služby modelu běhového objektu
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f1cefdad368ebcd006dcb4ecf653247147f36d03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372941"
---
# <a name="run-time-object-model-services"></a>Služby modelu běhového objektu

Třídy [CObject](../../mfc/reference/cobject-class.md) a [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) zapouzdřují několik objektových služeb, včetně přístupu k informacím o třídě za běhu, serializace a vytváření dynamického objektu. Všechny třídy `CObject` odvozené z dědí tuto funkci.

Přístup k informacím o třídě za běhu umožňuje určit informace o třídě objektu za běhu. Schopnost určit třídu objektu za běhu je užitečná, když potřebujete další kontrolu typu argumentů funkce a když je nutné napsat speciální kód založený na třídě objektu. Informace o třídě za běhu nejsou podporovány přímo jazykem Jazyka C++.

Serializace je proces zápisu nebo čtení obsahu objektu do nebo ze souboru. Serializace můžete použít k uložení obsahu objektu i po ukončení aplikace. Objekt pak lze číst ze souboru při restartování aplikace. Takové datové objekty jsou prý "trvalé".

Vytvoření dynamického objektu umožňuje vytvořit objekt zadané třídy za běhu. Například objekty dokumentu, zobrazení a rámečku musí podporovat dynamické vytváření, protože je třeba vytvořit dynamicky.

V následující tabulce jsou uvedena makra knihovny MFC, která podporují informace o třídě za běhu, serializaci a dynamické vytváření.

Další informace o těchto službách objektů za běhu a serializaci naleznete v článku [CObject Class: Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).

### <a name="run-time-object-model-services-macros"></a>Makra služby Object Model Services za běhu

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Umožňuje přístup k informacím o třídě za běhu (musí být použit v deklaraci třídy).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|Umožňuje dynamické vytváření a přístup k informacím o třídě za běhu (musí být použit v deklaraci třídy).|
|[DECLARE_SERIAL](#declare_serial)|Umožňuje serializaci a přístup k informacím o třídě za běhu (musí být použit v deklaraci třídy).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Umožňuje přístup k informacím o třídě za běhu (musí být použit v implementaci třídy).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Umožňuje dynamické vytváření a přístup k informacím za běhu (musí být použit v implementaci třídy).|
|[IMPLEMENT_SERIAL](#implement_serial)|Umožňuje serializaci a přístup k informacím o třídě za běhu (musí být použit v implementaci třídy).|
|[RUNTIME_CLASS](#runtime_class)|Vrátí `CRuntimeClass` strukturu, která odpovídá pojmenované třídě.|

Ole často vyžaduje dynamické vytváření objektů za běhu. Například aplikace serveru OLE musí být schopen vytvářet položky OLE dynamicky v reakci na požadavek od klienta. Podobně musí být automatizační server schopen vytvářet položky v reakci na požadavky od klientů automatizace.

Knihovna tříd Microsoft Foundation poskytuje dvě makra specifická pro OLE.

### <a name="dynamic-creation-of-ole-objects"></a>Dynamické vytváření objektů OLE

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Určuje, zda knihovna Common Controls implementuje zadané rozhraní API.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Určuje, zda knihovna Common Controls implementuje zadané rozhraní API.|
|[DECLARE_OLECREATE](#declare_olecreate)|Umožňuje objekty, které mají být vytvořeny prostřednictvím automatizace OLE.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Deklaruje `GetUserTypeNameID` a `GetMiscStatus` členské funkce třídy ovládacího prvku.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Deklaruje, že ovládací prvek OLE poskytuje seznam stránek vlastností pro zobrazení jeho vlastností.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Umožňuje vytvářet objekty systémem OLE.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementuje `GetUserTypeNameID` `GetMiscStatus` a členské funkce třídy řízení.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Toto makro nebo [IMPLEMENT_OLECREATE](#implement_olecreate) se musí zobrazit v `DECLARE_OLECREATE`souboru implementace pro všechny třídy, které používají . |

## <a name="afx_comctl32_if_exists"></a><a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

Určuje, zda knihovna Common Controls implementuje zadané rozhraní API.

### <a name="syntax"></a>Syntaxe

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Parametry

*Proc*<br/>
Ukazatel na řetězec s nulovým ukončením obsahující název funkce nebo určuje hodnotu ordinal funkce. Pokud je tento parametr řadovou hodnotou, musí být ve slově nižšího řádu; slovo nejvyššího řádu musí být nulové. Tento parametr musí být v Unicode.

### <a name="remarks"></a>Poznámky

Toto makro slouží k určení, zda knihovna Common Controls je součástí funkce určené *proc* (namísto volání [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Požadavky

afxcomctl32.h, afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a><a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

Určuje, zda knihovna Common Controls implementuje zadané rozhraní API (toto je verze [Unicode AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Syntaxe

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Parametry

*Proc*<br/>
Ukazatel na řetězec s nulovým ukončením obsahující název funkce nebo určuje hodnotu ordinal funkce. Pokud je tento parametr řadovou hodnotou, musí být ve slově nižšího řádu; slovo nejvyššího řádu musí být nulové. Tento parametr musí být v Unicode.

### <a name="remarks"></a>Poznámky

Toto makro slouží k určení, zda knihovna Common Controls je součástí funkce určené *proc* (namísto volání [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress). Toto makro je verze unicode AFX_COMCTL32_IF_EXISTS.

### <a name="requirements"></a>Požadavky

afxcomctl32.h, afxcomctl32.inl

## <a name="declare_dynamic"></a><a name="declare_dynamic"></a>DECLARE_DYNAMIC

Přidá možnost přístupu k informacím za běhu o třídě objektu `CObject`při odvození třídy z aplikace .

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Přidejte DECLARE_DYNAMIC makro do modulu záhlaví (.h) pro třídu a zahrňte tento modul do všech modulů CPP, které potřebují přístup k objektům této třídy.

Pokud použijete makra DECLARE_ DYNAMIC a IMPLEMENT_DYNAMIC, jak je popsáno, můžete použít makro RUNTIME_CLASS a `CObject::IsKindOf` funkci k určení třídy objektů za běhu.

Pokud DECLARE_DYNAMIC je součástí deklarace třídy, pak IMPLEMENT_DYNAMIC musí být zahrnuty do implementace třídy.

Další informace o makru DECLARE_DYNAMIC naleznete v tématu [CObject Class Topics](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="declare_dyncreate"></a><a name="declare_dyncreate"></a>DECLARE_DYNCREATE

Umožňuje objekty odvozené `CObject`třídy, které mají být vytvořeny dynamicky za běhu.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Rozhraní framework používá tuto schopnost vytvářet nové objekty dynamicky. Například nové zobrazení vytvořené při otevření nového dokumentu. Třídy dokumentů, zobrazení a rámců by měly podporovat dynamické vytváření, protože je třeba je vytvořit dynamicky.

Přidejte makro DECLARE_DYNCREATE do modulu H pro třídu a zahrňte tento modul do všech modulů CPP, které potřebují přístup k objektům této třídy.

Pokud DECLARE_DYNCREATE je součástí deklarace třídy, musí být IMPLEMENT_DYNCREATE zahrnuty do implementace třídy.

Další informace o makru DECLARE_DYNCREATE naleznete v tématu [CObject Class Topics](../../mfc/using-cobject.md).

> [!NOTE]
> Makro DECLARE_DYNCREATE obsahuje všechny funkce DECLARE_DYNAMIC.

### <a name="example"></a>Příklad

Viz příklad pro [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="declare_olectltype"></a><a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

Deklaruje `GetUserTypeNameID` a `GetMiscStatus` členské funkce třídy ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku.

### <a name="remarks"></a>Poznámky

`GetUserTypeNameID`a `GetMiscStatus` jsou čistě virtuální `COleControl`funkce, deklarované v . Vzhledem k tomu, že tyto funkce jsou čistě virtuální, musí být přepsány ve vaší třídě řízení. Kromě DECLARE_OLECTLTYPE je nutné přidat makro IMPLEMENT_OLECTLTYPE do deklarace třídy ovládacího prvku.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="declare_proppageids"></a><a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

Deklaruje, že ovládací prvek OLE poskytuje seznam stránek vlastností pro zobrazení jeho vlastností.

### <a name="syntax"></a>Syntaxe

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku, která vlastní stránky vlastností.

### <a name="remarks"></a>Poznámky

Použijte `DECLARE_PROPPAGEIDS` makro na konci deklarace třídy. Potom v souboru CPP, který definuje členské funkce pro `BEGIN_PROPPAGEIDS` třídu, použijte makro, položky maker pro `END_PROPPAGEIDS` každou ze stránek vlastností ovládacího prvku a makro deklarovat konec seznamu stránek vlastností.

Další informace o stránkách vlastností naleznete v článku [Ovládací prvky ActiveX: Stránky vlastností](../mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="declare_serial"></a><a name="declare_serial"></a>DECLARE_SERIAL

Generuje kód hlavičky C++ `CObject`nezbytný pro odvozenou třídu, kterou lze serializovat.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Serializace je proces zápisu nebo čtení obsahu objektu do a ze souboru.

Použijte makro DECLARE_SERIAL v modulu H a zahrňte tento modul do všech modulů CPP, které potřebují přístup k objektům této třídy.

Pokud DECLARE_SERIAL je zahrnuta v deklaraci třídy, pak IMPLEMENT_SERIAL musí být zahrnuty do implementace třídy.

Makro DECLARE_SERIAL obsahuje všechny funkce DECLARE_DYNAMIC a DECLARE_DYNCREATE.

Pomocí AFX_API makra můžete `CArchive` automaticky exportovat operátor extrakce pro třídy, které používají DECLARE_SERIAL a IMPLEMENT_SERIAL makra. Bracket deklarace třídy (umístěné v souboru H) s následujícím kódem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Další informace o DECLARE_SERIAL makru naleznete v tématu [CObject Class Topics](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="implement_dynamic"></a><a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

Generuje kód Jazyka C++ nezbytný `CObject`pro dynamickou odvozenou třídu s přístupem za běhu k názvu třídy a pozici v hierarchii.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

*base_class_name*<br/>
Název základní třídy.

### <a name="remarks"></a>Poznámky

Použijte IMPLEMENT_DYNAMIC makro v modulu CPP a potom výsledný objektový kód propojte pouze jednou.

Další informace naleznete v [tématu CObject Class Topics](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="implement_dyncreate"></a><a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

Umožňuje objekty odvozených `CObject`tříd, které mají být vytvořeny dynamicky za běhu při použití s DECLARE_DYNCREATE makro.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

*base_class_name*<br/>
Skutečný název základní třídy.

### <a name="remarks"></a>Poznámky

Rozhraní framework používá tuto schopnost vytvářet nové objekty dynamicky, například při čtení objektu z disku během serializace. Přidejte makro IMPLEMENT_DYNCREATE do souboru implementace třídy. Další informace naleznete v [tématu CObject Class Topics](../../mfc/using-cobject.md).

Pokud používáte makra DECLARE_DYNCREATE a IMPLEMENT_DYNCREATE, můžete pomocí `CObject::IsKindOf` RUNTIME_CLASS makra a členské funkce určit třídu objektů za běhu.

Pokud DECLARE_DYNCREATE je součástí deklarace třídy, musí být IMPLEMENT_DYNCREATE zahrnuty do implementace třídy.

Všimněte si, že tato definice makra vyvolá výchozí konstruktor pro vaši třídu. Pokud netriviální konstruktor je explicitně implementována třídy, musí také explicitně implementovat výchozí konstruktor také. Výchozí konstruktor lze přidat do **oddílů soukromého** nebo **chráněného** člena třídy, aby se zabránilo jeho volání z implementace mimo třídu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="implement_olecreate_flags"></a><a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

Toto makro nebo [IMPLEMENT_OLECREATE](#implement_olecreate) se musí zobrazit v souboru implementace pro všechny třídy, které používá DECLARE_OLECREATE.

### <a name="syntax"></a>Syntaxe

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

*external_name*<br/>
Název objektu vystavený jiným aplikacím (uzavřený v uvozovkách).

*nPříznaky*<br/>
Obsahuje jeden nebo více z následujících příznaků:

- `afxRegInsertable`Umožňuje, aby se ovládací prvek zobrazil v dialogovém okně Vložit objekt pro objekty OLE.
- `afxRegApartmentThreading`Nastaví model podprocesu v registru na ThreadingModel=Apartment.
- `afxRegFreeThreading`Nastaví model podprocesu v registru na ThreadingModel=Free.

Můžete kombinovat dva `afxRegApartmentThreading` příznaky `afxRegFreeThreading` a nastavit ThreadingModel=Both. Další informace o registraci modelu vlákna naleznete v části [InprocServer32](/windows/win32/com/inprocserver32) v sadě Windows SDK.

*l*, *w1*, *w2*, *b1,* *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* Součásti třídy CLSID.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Pokud použijete IMPLEMENT_OLECREATE_FLAGS, můžete určit, který model vláken objekt podporuje pomocí parametru *nFlags.* Pokud chcete podporovat pouze model s jedním šlapáním, použijte IMPLEMENT_OLECREATE.

Externí název je identifikátor vystavený jiným aplikacím. Klientské aplikace používají externí název k vyžádání objektu této třídy z automatizačního serveru.

ID třídy OLE je jedinečný 128bitový identifikátor objektu. Skládá se z jednoho **dlouhého**, dvou **WORD**s a osmi **BAJTů,** reprezentovaného *l*, *w1*, *w2*a *b1* až *b8* v popisu syntaxe. Průvodce aplikací a průvodci kódem pro vás podle potřeby vytvoří jedinečné ID třídy OLE.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="implement_olectltype"></a><a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

Implementuje `GetUserTypeNameID` `GetMiscStatus` a členské funkce třídy řízení.

### <a name="syntax"></a>Syntaxe

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku.

*idsUserTypeName*<br/>
ID prostředku řetězce obsahujícího externí název ovládacího prvku.

*dwOleMisc*<br/>
Výčet obsahující jeden nebo více příznaků. Další informace o tomto výčtu naleznete v [tématu OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Kromě IMPLEMENT_OLECTLTYPE je nutné přidat makro DECLARE_OLECTLTYPE do deklarace třídy ovládacího prvku.

Členská `GetUserTypeNameID` funkce vrátí řetězec prostředků, který identifikuje třídu ovládacího prvku. `GetMiscStatus`vrátí bity OLEMISC pro vaši kontrolu. Tento výčet určuje kolekci nastavení popisující různé charakteristiky ovládacího prvku. Úplný popis nastavení OLEMISC naleznete v [části OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) v sadě Windows SDK.

> [!NOTE]
> Výchozí nastavení používaná Průvodcem ovládacím prvkem ActiveX jsou: OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE a OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="implement_serial"></a><a name="implement_serial"></a>IMPLEMENT_SERIAL

Generuje kód Jazyka C++ nezbytný `CObject`pro dynamickou odvozenou třídu s přístupem za běhu k názvu třídy a pozici v hierarchii.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

*base_class_name*<br/>
Název základní třídy.

*wSchema*<br/>
UINT "číslo verze", které bude zakódováno v archivu, aby mohl rekonstruovaný program identifikovat a zpracovávat data vytvořená staršími verzemi programu. Číslo schématu třídy nesmí být -1.

### <a name="remarks"></a>Poznámky

Použijte IMPLEMENT_SERIAL makro v modulu CPP. pak propojte výsledný objektový kód pouze jednou.

Pomocí AFX_API makra můžete `CArchive` automaticky exportovat operátor extrakce pro třídy, které používají DECLARE_SERIAL a IMPLEMENT_SERIAL makra. Bracket deklarace třídy (umístěné v souboru H) s následujícím kódem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Další informace naleznete v tématu [CObject Class Topics](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="runtime_class"></a><a name="runtime_class"></a>RUNTIME_CLASS

Získá strukturu třídy run-time z názvu třídy C++.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy (není uzavřen v uvozovkách).

### <a name="remarks"></a>Poznámky

RUNTIME_CLASS vrátí ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pro třídu určenou *class_name*. Pouze `CObject`odvozené třídy deklarované s DECLARE_DYNAMIC, DECLARE_DYNCREATE `CRuntimeClass` nebo DECLARE_SERIAL vrátí ukazatele do struktury.

Další informace naleznete v [tématu CObject Class Topics](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="declare_olecreate"></a><a name="declare_olecreate"></a>DECLARE_OLECREATE

Umožňuje objekty odvozené `CCmdTarget`třídy, které mají být vytvořeny prostřednictvím automatizace OLE.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Toto makro umožňuje jiným aplikacím s podporou TECHNOLOGIE OLE vytvářet objekty tohoto typu.

Přidejte makro DECLARE_OLECREATE do modulu H pro třídu a zahrňte tento modul do všech modulů CPP, které potřebují přístup k objektům této třídy.

Pokud DECLARE_OLECREATE je součástí deklarace třídy, pak IMPLEMENT_OLECREATE musí být zahrnuty do implementace třídy. Deklarace třídy používající DECLARE_OLECREATE musí také používat DECLARE_DYNCREATE nebo DECLARE_SERIAL.

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp.h

## <a name="implement_olecreate"></a><a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

Toto makro nebo [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) se musí zobrazit v `DECLARE_OLECREATE`souboru implementace pro všechny třídy, které používají .

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

*external_name*<br/>
Název objektu vystavený jiným aplikacím (uzavřený v uvozovkách).

*l*, *w1*, *w2*, *b1,* *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* Součásti třídy CLSID.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Pokud používáte IMPLEMENT_OLECREATE, ve výchozím nastavení podporujete pouze jeden model podprocesu. Pokud použijete IMPLEMENT_OLECREATE_FLAGS, můžete určit, který model vláken objekt podporuje pomocí parametru *nFlags.*

Externí název je identifikátor vystavený jiným aplikacím. Klientské aplikace používají externí název k vyžádání objektu této třídy z automatizačního serveru.

ID třídy OLE je jedinečný 128bitový identifikátor objektu. Skládá se z jednoho **dlouhého**, dvou **WORD**s a osmi **BAJTů,** reprezentovaného *l*, *w1*, *w2*a *b1* až *b8* v popisu syntaxe. Průvodce aplikací a průvodci kódem pro vás podle potřeby vytvoří jedinečné ID třídy OLE.

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)<br/>
[Izolace knihovny běžných ovládacích prvků MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[Klíč CLSID](/windows/win32/com/clsid-key-hklm)
