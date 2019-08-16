---
title: Služby modelu běhového objektu
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f8b891467d91d0c945b6c59c90dbc49fd7cbcb30
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491589"
---
# <a name="run-time-object-model-services"></a>Služby modelu běhového objektu

Třídy [CObject](../../mfc/reference/cobject-class.md) a [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) zapouzdřují několik služeb objektů, včetně přístupu k běhovým informacím o třídě, serializaci a vytváření dynamických objektů. Všechny třídy odvozené z `CObject` dědění této funkce.

Přístup k informacím třídy run-time umožňuje určit informace o třídě objektu za běhu. Možnost určit třídu objektu za běhu je užitečná v případě, že potřebujete speciální kontrolu typu argumentů funkce a pokud je nutné napsat kód pro zvláštní účely na základě třídy objektu. Informace o třídě run-time nejsou přímo podporovány C++ jazykem.

Serializace je proces zápisu nebo čtení obsahu objektu do nebo ze souboru. Pomocí serializace můžete uložit obsah objektu i po ukončení aplikace. Objekt lze následně číst ze souboru, když je aplikace restartována. U takových datových objektů se říká "trvalá".

Vytváření dynamických objektů umožňuje vytvořit objekt zadané třídy v době běhu. Například objekty dokumentu, zobrazení a rámce musí podporovat dynamické vytváření, protože rozhraní je musí vytvořit dynamicky.

V následující tabulce jsou uvedena makra knihovny MFC, která podporují informace třídy runtime, serializaci a dynamické vytváření.

Další informace o těchto objektových službách a serializaci modulu runtime naleznete v článku [třída CObject: Přístup k běhovým informacím o](../../mfc/accessing-run-time-class-information.md)třídě.

### <a name="run-time-object-model-services-macros"></a>Makra služeb objektového modelu runtime

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Povolí přístup k běhovým informacím o třídě (musí se použít v deklaraci třídy).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|Povolí dynamické vytvoření a přístup k informacím třídy run-time (musí být použity v deklaraci třídy).|
|[DECLARE_SERIAL](#declare_serial)|Povolí serializaci a přístup k informacím třídy run-time (musí být použity v deklaraci třídy).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Povolí přístup k běhovým informacím o třídě (musí se použít v implementaci třídy).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Povolí dynamické vytváření a přístup k běhovým informacím (musí se použít v implementaci třídy).|
|[IMPLEMENT_SERIAL](#implement_serial)|Povoluje serializaci a přístup k informacím třídy run-time (musí být použity v implementaci třídy).|
|[RUNTIME_CLASS](#runtime_class)|`CRuntimeClass` Vrátí strukturu, která odpovídá pojmenované třídě.|

OLE často vyžaduje dynamické vytváření objektů v době běhu. Například serverová aplikace OLE musí být schopna dynamicky vytvářet položky OLE v reakci na požadavek od klienta. Podobně server Automation musí být schopný vytvářet položky v reakci na požadavky od klientů automatizace.

Knihovna Microsoft Foundation Class poskytuje dvě makra specifická pro OLE.

### <a name="dynamic-creation-of-ole-objects"></a>Dynamické vytváření objektů OLE

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Určuje, zda knihovna běžných ovládacích prvků implementuje zadané rozhraní API.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Určuje, zda knihovna běžných ovládacích prvků implementuje zadané rozhraní API.|
|[DECLARE_OLECREATE](#declare_olecreate)|Umožňuje vytvářet objekty pomocí automatizace OLE.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|`GetUserTypeNameID` Deklaruječlenské`GetMiscStatus` funkce třídy ovládacího prvku.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Deklaruje, že ovládací prvek OLE poskytne seznam stránek vlastností pro zobrazení jeho vlastností.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Povoluje objekty, které mají být vytvořeny systémem OLE.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementuje členské funkce `GetMiscStatus`atřídy ovládacího prvku. `GetUserTypeNameID`|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Toto makro nebo [IMPLEMENT_OLECREATE](#implement_olecreate) se musí nacházet v implementačním souboru pro jakoukoliv třídu, `DECLARE_OLECREATE`která používá. |

## <a name="afx_comctl32_if_exists"></a> AFX_COMCTL32_IF_EXISTS

Určuje, zda knihovna běžných ovládacích prvků implementuje zadané rozhraní API.

### <a name="syntax"></a>Syntaxe

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Parametry

*Proc*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název funkce nebo určuje ordinální hodnotu funkce. Pokud je tento parametr pořadovou hodnotou, musí být ve slově s nižším pořadím. slovo s vysokým pořadím musí být nula. Tento parametr musí být v kódování Unicode.

### <a name="remarks"></a>Poznámky

Pomocí tohoto makra lze určit, zda společné ovládací prvky zavolají funkci určenou funkcí *proc* (místo volání funkce [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Požadavky

afxcomctl32.h, afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a>  AFX_COMCTL32_IF_EXISTS2

Určuje, zda knihovna běžných ovládacích prvků implementuje zadané rozhraní API (Jedná se o verzi Unicode [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Syntaxe

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Parametry

*Proc*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název funkce nebo určuje ordinální hodnotu funkce. Pokud je tento parametr pořadovou hodnotou, musí být ve slově s nižším pořadím. slovo s vysokým pořadím musí být nula. Tento parametr musí být v kódování Unicode.

### <a name="remarks"></a>Poznámky

Pomocí tohoto makra lze určit, zda společné ovládací prvky zavolají funkci určenou funkcí *proc* (místo volání funkce [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress). Toto makro je verze AFX_COMCTL32_IF_EXISTS Unicode.

### <a name="requirements"></a>Požadavky

afxcomctl32.h, afxcomctl32.inl

##  <a name="declare_dynamic"></a>DECLARE_DYNAMIC

Přidává možnost přístupu k běhovým informacím o třídě objektu při odvozování třídy z `CObject`.

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Přidejte makro DECLARE_DYNAMIC do modulu Header (. h) pro třídu a pak tento modul zahrňte do všech modulů. cpp, které potřebují přístup k objektům této třídy.

Použijete-li DECLARE_ dynamická makra a IMPLEMENT_DYNAMIC, jak je popsáno, můžete pomocí makra RUNTIME_CLASS a `CObject::IsKindOf` funkce určit třídu objektů v době běhu.

Pokud je DECLARE_DYNAMIC obsažen v deklaraci třídy, musí být IMPLEMENT_DYNAMIC součástí implementace třídy.

Další informace o makru DECLARE_DYNAMIC naleznete v [tématech třídy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="declare_dyncreate"></a>  DECLARE_DYNCREATE

Povoluje, aby `CObject`objekty odvozené třídy byly dynamicky vytvořeny v době běhu.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Rozhraní používá tuto možnost k dynamickému vytváření nových objektů. Například nové zobrazení vytvořené při otevření nového dokumentu. Třídy dokumentu, zobrazení a rámce by měly podporovat dynamické vytváření, protože rozhraní je musí vytvořit dynamicky.

Přidejte makro DECLARE_DYNCREATE do modulu. h pro třídu a pak tento modul zahrňte do všech modulů. cpp, které potřebují přístup k objektům této třídy.

Pokud je DECLARE_DYNCREATE obsažen v deklaraci třídy, musí být IMPLEMENT_DYNCREATE součástí implementace třídy.

Další informace o makru DECLARE_DYNCREATE naleznete v [tématech třídy CObject](../../mfc/using-cobject.md).

> [!NOTE]
>  Makro DECLARE_DYNCREATE zahrnuje všechny funkce DECLARE_DYNAMIC.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

## <a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

`GetUserTypeNameID` Deklaruječlenské`GetMiscStatus` funkce třídy ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku

### <a name="remarks"></a>Poznámky

`GetUserTypeNameID`a `GetMiscStatus` jsou čistě virtuální funkce deklarované v `COleControl`. Vzhledem k tomu, že tyto funkce jsou čistě virtuální, musí být přepsány ve vaší třídě ovládacího prvku. Kromě DECLARE_OLECTLTYPE je nutné přidat makro IMPLEMENT_OLECTLTYPE do deklarace třídy ovládacího prvku.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXCTL. h

## <a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

Deklaruje, že ovládací prvek OLE poskytne seznam stránek vlastností pro zobrazení jeho vlastností.

### <a name="syntax"></a>Syntaxe

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku, která je vlastníkem stránek vlastností.

### <a name="remarks"></a>Poznámky

`DECLARE_PROPPAGEIDS` Použijte makro na konci deklarace třídy. Poté v souboru. cpp, který definuje členské funkce pro třídu, použijte `BEGIN_PROPPAGEIDS` makro, položky makra pro každou stránku vlastností ovládacího prvku `END_PROPPAGEIDS` a makro k deklaraci konce seznamu stránek vlastností.

Další informace o stránkách vlastností najdete v článku [ovládací prvky ActiveX: Stránky](../mfc-activex-controls-property-pages.md)vlastností.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXCTL. h

##  <a name="declare_serial"></a>DECLARE_SERIAL

Generuje kód C++ hlavičky nezbytný pro `CObject`třídu odvozenou od třídy, která může být serializována.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Serializace je proces zápisu nebo čtení obsahu objektu do a ze souboru.

Použijte makro DECLARE_SERIAL v modulu. h a pak tento modul zahrňte do všech modulů. cpp, které potřebují přístup k objektům této třídy.

Pokud je DECLARE_SERIAL obsažen v deklaraci třídy, musí být IMPLEMENT_SERIAL součástí implementace třídy.

Makro DECLARE_SERIAL zahrnuje všechny funkce DECLARE_DYNAMIC a DECLARE_DYNCREATE.

Makro AFX_API můžete použít k automatickému exportu `CArchive` operátoru extrakce pro třídy, které používají makra DECLARE_SERIAL a IMPLEMENT_SERIAL. V závorce třídy deklarace (umístěné v souboru. h) s následujícím kódem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Další informace o makru DECLARE_SERIAL naleznete v [tématech třídy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

Generuje C++ kód nezbytný pro dynamickou `CObject`odvozenou třídu s přístupem run-time k názvu a pozici třídy v rámci hierarchie.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

*base_class_name*<br/>
Název základní třídy.

### <a name="remarks"></a>Poznámky

Použijte makro IMPLEMENT_DYNAMIC v modulu. cpp a potom propojte výsledný kód objektu pouze jednou.

Další informace naleznete v [tématech třídy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

Umožňuje, aby `CObject`objekty odvozené třídy byly dynamicky vytvořeny v době běhu při použití s DECLARE_DYNCREATE makrem.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

*base_class_name*<br/>
Skutečný název základní třídy.

### <a name="remarks"></a>Poznámky

Rozhraní používá tuto možnost k dynamickému vytváření nových objektů, například při čtení objektu z disku během serializace. Do implementačního souboru třídy přidejte makro IMPLEMENT_DYNCREATE. Další informace naleznete v [tématech třídy CObject](../../mfc/using-cobject.md).

Použijete-li makra DECLARE_DYNCREATE a IMPLEMENT_DYNCREATE, můžete pomocí makra RUNTIME_CLASS a `CObject::IsKindOf` členské funkce určit třídu objektů v době běhu.

Pokud je DECLARE_DYNCREATE obsažen v deklaraci třídy, musí být IMPLEMENT_DYNCREATE součástí implementace třídy.

Všimněte si, že tato definice makra vyvolá výchozí konstruktor pro vaši třídu. Pokud je netriviální konstruktor explicitně implementován třídou, musí také explicitně implementovat i výchozí konstruktor. Výchozí konstruktor lze přidat do oddílů **Private** nebo Protected member třídy , aby bylo zabráněno jeho volání mimo implementaci třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

## <a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

Toto makro nebo [IMPLEMENT_OLECREATE](#implement_olecreate) se musí nacházet v implementačním souboru pro jakoukoliv třídu, která používá DECLARE_OLECREATE.

### <a name="syntax"></a>Syntaxe

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

*external_name*<br/>
Název objektu vystavený ostatním aplikacím (uzavřený v uvozovkách).

*nFlags*<br/>
Obsahuje jeden nebo více následujících příznaků:

   - `afxRegInsertable`Umožňuje ovládacímu prvku zobrazit v dialogovém okně Vložit objekt pro objekty OLE.
   - `afxRegApartmentThreading`Nastaví model vláken v registru na ThreadingModel = Apartment.
   - `afxRegFreeThreading`Nastaví model vláken v registru na ThreadingModel = Free.

         You can combine the two flags `afxRegApartmentThreading` and `afxRegFreeThreading` to set ThreadingModel=Both. See [InprocServer32](/windows/win32/com/inprocserver32) in the Windows SDK for more information on threading model registration.

*l*, *W1*, *W2*, *B1*, *B2*, *B3*, *B4*, *B5*, *B6*, *B7*, *B8* komponenty CLSID třídy.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud používáte IMPLEMENT_OLECREATE_FLAGS, můžete určit, který model vláken váš objekt podporuje, pomocí parametru *nFlags* . Pokud chcete podporovat jenom model s jedním schodišťovém modelem, použijte IMPLEMENT_OLECREATE.

Externí název je identifikátor vystavený ostatním aplikacím. Klientské aplikace používají externí název k vyžádání objektu této třídy ze serveru automatizace.

ID třídy OLE je jedinečný 128 identifikátor pro objekt. Skládá se z jednoho **dlouhého**, dvou **slov**a osmi **bajtů**s, jak je znázorněno v popisu syntaxe v *B8* *l*, *W1*, *W2*a *B1* . Průvodce aplikací a průvodci kódem vytvoří jedinečná ID třídy OLE podle potřeby.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

Implementuje členské funkce `GetMiscStatus`atřídy ovládacího prvku. `GetUserTypeNameID`

### <a name="syntax"></a>Syntaxe

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku

*idsUserTypeName*<br/>
ID prostředku s řetězcem, který obsahuje externí název ovládacího prvku.

*dwOleMisc*<br/>
Výčet obsahující jeden nebo více příznaků. Další informace o tomto výčtu naleznete v tématu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) v Windows SDK.

### <a name="remarks"></a>Poznámky

Kromě IMPLEMENT_OLECTLTYPE je nutné přidat makro DECLARE_OLECTLTYPE do deklarace třídy ovládacího prvku.

`GetUserTypeNameID` Členská funkce vrátí řetězec prostředku, který identifikuje vaši třídu ovládacího prvku. `GetMiscStatus`Vrátí OLEMISC bity pro váš ovládací prvek. Tento výčet Určuje kolekci nastavení popisujících různé charakteristiky vašeho ovládacího prvku. Úplný popis nastavení OLEMISC najdete v tématu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) v Windows SDK.

> [!NOTE]
>  Výchozí nastavení používané ControlWizard ActiveX jsou: OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE a OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXCTL. h

##  <a name="implement_serial"></a>IMPLEMENT_SERIAL

Generuje C++ kód nezbytný pro dynamickou `CObject`odvozenou třídu s přístupem run-time k názvu a pozici třídy v rámci hierarchie.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

*base_class_name*<br/>
Název základní třídy.

*wSchema*<br/>
Číslo verze UINT, které bude kódováno v archivu pro povolení deserializace programu pro identifikaci a zpracování dat vytvořených předchozími verzemi programu. Číslo schématu třídy nesmí být-1.

### <a name="remarks"></a>Poznámky

Použijte makro IMPLEMENT_SERIAL v modulu. cpp; Nakonec propojte výsledný kód objektu pouze jednou.

Makro AFX_API můžete použít k automatickému exportu `CArchive` operátoru extrakce pro třídy, které používají makra DECLARE_SERIAL a IMPLEMENT_SERIAL. V závorce třídy deklarace (umístěné v souboru. h) s následujícím kódem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Další informace najdete v [tématech třídy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="runtime_class"></a>RUNTIME_CLASS

Načte strukturu běhové třídy z názvu C++ třídy.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy (není uzavřen v uvozovkách).

### <a name="remarks"></a>Poznámky

RUNTIME_CLASS vrací ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pro třídu určenou třídou *class_name*. Pouze `CObject`odvozené třídy deklarované s DECLARE_DYNAMIC, DECLARE_DYNCREATE nebo DECLARE_SERIAL vrátí ukazatel `CRuntimeClass` na strukturu.

Další informace naleznete v [tématech třídy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="declare_olecreate"></a>DECLARE_OLECREATE

Povoluje vytváření objektů `CCmdTarget`odvozených tříd prostřednictvím automatizace OLE.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

### <a name="remarks"></a>Poznámky

Toto makro umožňuje ostatním aplikacím podporujícím technologii OLE vytvářet objekty tohoto typu.

Do modulu. h pro třídu přidejte makro DECLARE_OLECREATE a potom tento modul zahrňte do všech modulů. cpp, které potřebují přístup k objektům této třídy.

Pokud je DECLARE_OLECREATE obsažen v deklaraci třídy, musí být IMPLEMENT_OLECREATE součástí implementace třídy. Deklarace třídy pomocí DECLARE_OLECREATE musí také používat DECLARE_DYNCREATE nebo DECLARE_SERIAL.

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp. h

##  <a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

Toto makro nebo [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) se musí nacházet v implementačním souboru pro jakoukoliv třídu, `DECLARE_OLECREATE`která používá.

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Skutečný název třídy.

*external_name*<br/>
Název objektu vystavený ostatním aplikacím (uzavřený v uvozovkách).

*l*, *W1*, *W2*, *B1*, *B2*, *B3*, *B4*, *B5*, *B6*, *B7*, *B8* komponenty CLSID třídy.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud ve výchozím nastavení používáte IMPLEMENT_OLECREATE, budete podporovat jenom jeden model vláken. Pokud používáte IMPLEMENT_OLECREATE_FLAGS, můžete určit, který model vláken váš objekt podporuje, pomocí parametru *nFlags* .

Externí název je identifikátor vystavený ostatním aplikacím. Klientské aplikace používají externí název k vyžádání objektu této třídy ze serveru automatizace.

ID třídy OLE je jedinečný 128 identifikátor pro objekt. Skládá se z jednoho **dlouhého**, dvou **slov**a osmi **bajtů**s, jak je znázorněno v popisu syntaxe v *B8* *l*, *W1*, *W2*a *B1* . Průvodce aplikací a průvodci kódem vytvoří jedinečná ID třídy OLE podle potřeby.

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp. h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[Izolace knihovny běžných ovládacích prvků MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[Klíč CLSID](/windows/win32/com/clsid-key-hklm)
