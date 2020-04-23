---
title: CObject – třída
ms.date: 11/04/2016
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
ms.openlocfilehash: 66d76e0062d13b2bd5a16d9b07f99db9e989805a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753990"
---
# <a name="cobject-class"></a>CObject – třída

Hlavní základní třída pro knihovnu tříd Microsoft Foundation.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CObject::CObject](#cobject)|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CObject::AssertValid](#assertvalid)|Ověří integritu tohoto objektu.|
|[CObject::Dump](#dump)|Vytvoří diagnostický výpis tohoto objektu.|
|[CObject::GetRuntimeClass](#getruntimeclass)|Vrátí `CRuntimeClass` strukturu odpovídající třídě tohoto objektu.|
|[CObjekt::IskindOf](#iskindof)|Testuje vztah tohoto objektu k dané třídě.|
|[CObject::Lze serializovat](#isserializable)|Testy chcete-li zjistit, zda tento objekt lze serializovat.|
|[CObject::Serializovat](#serialize)|Načte nebo uloží objekt z/do archivu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CObject::odstranění operátoru](#operator_delete)|Zvláštní **operátor odstranění.**|
|[CObject::operátor new](#operator_new)|Speciální **nový** operátor.|

## <a name="remarks"></a>Poznámky

Slouží jako kořen nejen pro třídy `CFile` `CObList`knihovny, jako je například a , ale také pro třídy, které píšete. `CObject`poskytuje základní služby, včetně

- Podpora serializace

- Informace o třídě za běhu

- Výstup diagnostiky objektů

- Kompatibilita s třídami kolekce

Všimněte `CObject` si, že nepodporuje více dědičnosti. Odvozené třídy mohou `CObject` mít pouze jednu základní třídu a které `CObject` musí být nejvíce vlevo v hierarchii. Je však přípustné mít struktury a neodvozené `CObject`třídy v pravostranných větvích s více násobnými dědictvími.

Budete realizovat hlavní `CObject` výhody z odvození, pokud použijete některé volitelné makra v implementaci třídy a deklarace.

Makra první [úrovně, DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) a [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), umožňují přístup k názvu třídy a jejímu umístění v hierarchii za běhu. To zase umožňuje smysluplné diagnostické dumping.

Makra druhé úrovně, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), zahrnují všechny funkce maker první úrovně a umožňují serializovat objekt do a z "archivu".

Informace o odvození tříd Microsoft Foundation a tříd jazyka `CObject`C++ obecně a použití naleznete v [tématu Použití objektu CObject](../../mfc/using-cobject.md) a [serializace](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a>CObject::AssertValid

Ověří integritu tohoto objektu.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

`AssertValid`provede kontrolu platnosti tohoto objektu kontrolou jeho vnitřního stavu. V ladicí verzi knihovny může uplatnit a tedy ukončit program se zprávou, která uvádí číslo řádku a název souboru, `AssertValid` kde se kontrolní výraz nezdařil.

Při psaní vlastní třídy, měli `AssertValid` byste přepsat funkci poskytovat diagnostické služby pro sebe a ostatní uživatele vaší třídy. Přepsána `AssertValid` obvykle `AssertValid` volá funkci jeho základní třídy před kontrolou datových členů jedinečných pro odvozené třídy.

Protože `AssertValid` je **const** funkce, není povoleno změnit stav objektu během testu. Vlastní funkce odvozené třídy `AssertValid` by neměly vyvolávat výjimky, ale spíše by měly uplatnit, zda detekují neplatná data objektu.

Definice "platnost" závisí na třídy objektu. Funkce by měla zpravidla provést "mělkou kontrolu". To znamená, že pokud objekt obsahuje ukazatele na jiné objekty, by měl zkontrolovat, zda ukazatele nejsou null, ale neměl by provádět testování platnosti na objekty, na které odkazuje ukazatele.

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy `CObject` používané ve všech příkladech.

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Další příklad naleznete [v tématu AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).

## <a name="cobjectcobject"></a><a name="cobject"></a>CObject::CObject

Tyto funkce jsou `CObject` standardní konstruktory.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parametry

*objektSrc*<br/>
Odkaz na jiný`CObject`

### <a name="remarks"></a>Poznámky

Výchozí verze je automaticky volána konstruktorem odvozené třídy.

Pokud vaše třída je serializovatelný (zahrnuje makro IMPLEMENT_SERIAL), pak musíte mít výchozí konstruktor (konstruktor bez argumentů) v deklaraci třídy. Pokud nepotřebujete výchozí konstruktor, deklarujte soukromý nebo chráněný "prázdný" konstruktor. Další informace naleznete [v tématu Using CObject](../../mfc/using-cobject.md).

Standardní c++ výchozí konstruktor třídy provádí kopii člen po člen. Přítomnost konstruktoru `CObject` soukromé kopie zaručuje chybovou zprávu kompilátoru, pokud je konstruktor kopie vaší třídy potřebný, ale není k dispozici. Proto je nutné zadat konstruktor kopie, pokud vaše třída vyžaduje tuto schopnost.

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy `CObject` použité v příkladech.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a>CObject::Dump

Vypíše obsah objektu [cdumpcontext](../../mfc/reference/cdumpcontext-class.md) objektu.

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
Kontext diagnostického výpisu `afxDump`pro dumping, obvykle .

### <a name="remarks"></a>Poznámky

Při psaní vlastní třídy, měli `Dump` byste přepsat funkci poskytovat diagnostické služby pro sebe a ostatní uživatele vaší třídy. Přepsána `Dump` obvykle `Dump` volá funkci jeho základní třídy před tiskem datových členů jedinečných pro odvozené třídy. `CObject::Dump`vytiskne název třídy, `IMPLEMENT_DYNAMIC` pokud vaše třída používá makro nebo IMPLEMENT_SERIAL.

> [!NOTE]
> Funkce `Dump` by neměla tisknout znak nového řádku na konci výstupu.

`Dump`Volání smysl pouze v ladicí verzi Knihovny tříd Microsoft Foundation. Měli byste bracket volání, deklarace funkce a implementace funkcí s **#ifdef _DEBUG** /  `#endif` příkazy pro podmíněné kompilace.

Vzhledem k tomu, `Dump` že je **const** funkce, není povoleno změnit stav objektu během výpisu stavu.

[CDumpContext operátor vložení (<<)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) `Dump` volá `CObject` při vložení ukazatele.

`Dump`umožňuje pouze "acyklické" vyhazování předmětů. Můžete například vypsat seznam objektů, ale pokud je jedním z objektů samotný seznam, nakonec přetečení zásobníku.

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy `CObject` používané ve všech příkladech.

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a>CObject::GetRuntimeClass

Vrátí `CRuntimeClass` strukturu odpovídající třídě tohoto objektu.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) odpovídající třídě tohoto objektu; nikdy **NULL**.

### <a name="remarks"></a>Poznámky

Pro každou `CRuntimeClass` `CObject`odvozenou třídu existuje jedna struktura. Členové struktury jsou následující:

- **m_lpszClassName LPCSTR** Řetězec s nulovým ukončeným hodnotou obsahující název třídy ASCII.

- **int m_nObjectSize** Velikost objektu v bajtů. Pokud objekt má datové členy, které odkazují na přidělené paměti, velikost této paměti není zahrnuta.

- **UINT m_wSchema** Číslo schématu ( - 1 pro neserializovatelné třídy). Popis čísla schématu naleznete v [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makru.

- **CObject\* (\* PASCAL m_pfnCreateObject )** Ukazatel funkce na výchozí konstruktor, který vytvoří objekt vaší třídy (platí pouze v případě, že třída podporuje dynamické vytváření; jinak vrátí **hodnotu NULL).**

- **CRuntimeClass\* (\* PASCAL m_pfn_GetBaseClass )( )** Pokud je aplikace dynamicky propojena s verzí knihovny MFC AFXDLL, ukazatel na funkci, která vrací `CRuntimeClass` strukturu základní třídy.

- **CRuntimeClass\* m_pBaseClass** Pokud je aplikace staticky propojena s `CRuntimeClass` knihovnou MFC, ukazatel na strukturu základní třídy.

Tato funkce vyžaduje použití [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)nebo [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makro v implementaci třídy. V opačném případě získáte nesprávné výsledky.

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy `CObject` používané ve všech příkladech.

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a>CObjekt::IskindOf

Testuje vztah tohoto objektu k dané třídě.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) přidruženou k vaší `CObject`odvozené třídě.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud objekt odpovídá třídě; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce testuje *pClass,* aby zjistila, zda (1) je objektem zadané třídy nebo (2) je objektem třídy odvozené ze zadané třídy. Tato funkce funguje pouze pro třídy deklarované s [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)nebo [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) makro.

Nepoužívejte tuto funkci značně, protože porazí funkci polymorfismu C++. Místo toho použijte virtuální funkce.

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy `CObject` používané ve všech příkladech.

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a>CObject::Lze serializovat

Testuje, zda je tento objekt způsobilý pro serializaci.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud lze tento objekt serializovat; jinak 0.

### <a name="remarks"></a>Poznámky

Aby byla třída serializovatelná, musí její deklarace obsahovat [makro DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) a implementace musí obsahovat [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makro.

> [!NOTE]
> Tuto funkci nepřepisuj.

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy `CObject` používané ve všech příkladech.

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a>CObject::odstranění operátoru

Pro verzi verze knihovny, operátor **delete** uvolní paměť přidělenou operátorem **new**.

```cpp
void PASCAL operator delete(void* p);

void PASCAL operator delete(
    void* p,
    void* pPlace);

void PASCAL operator delete(
    void* p,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Poznámky

Ve verzi ladění operátor **delete** se účastní schéma monitorování přidělení určené k detekci nevracení paměti.

Pokud použijete řádek kódu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

před některou z vašich implementací v . CPP, pak bude použita třetí verze **odstranění,** ukládání názvu souboru a čísla řádku v přiděleném bloku pro pozdější vykazování. Nemusíte se starat o poskytování dalších parametrů; makro se o to postará za vás.

I v případě, že nechcete používat DEBUG_NEW v režimu ladění, stále získáte detekci úniku, ale bez sestavy čísla řádku zdrojového souboru popsané výše.

Pokud přepíšete operátory **new** a **odstranit**, ztratíte tuto diagnostickou schopnost.

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy `CObject` použité v příkladech.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a>CObject::operátor new

Pro verzi vydání knihovny operátor **new** provádí optimální přidělení paměti `malloc`způsobem podobným .

```cpp
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Poznámky

Ve verzi ladění operátor **new** se účastní schéma monitorování přidělení určené k detekci nevracení paměti.

Pokud použijete řádek kódu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

před některou z vašich implementací v . CPP, pak bude použita druhá verze **nového,** ukládání názvu souboru a čísla řádku v přiděleném bloku pro pozdější vykazování. Nemusíte se starat o poskytování dalších parametrů; makro se o to postará za vás.

I v případě, že nechcete používat DEBUG_NEW v režimu ladění, stále získáte detekci úniku, ale bez sestavy čísla řádku zdrojového souboru popsané výše.

> [!NOTE]
> Pokud tento operátor přepíšete, musíte také přepsat **odstranit**. Nepoužívejte standardní funkci `_new_handler` knihovny.

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy `CObject` použité v příkladech.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a>CObject::Serializovat

Přečte nebo zapíše tento objekt z nebo do archivu.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Objekt `CArchive` serializovat do nebo z.

### <a name="remarks"></a>Poznámky

Je nutné `Serialize` přepsat pro každou třídu, kterou chcete serializovat. Přepsaný `Serialize` musí nejprve `Serialize` volat funkci jeho základní třídy.

Makro [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) musíte použít také v deklaraci třídy a makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) v implementaci.

Pomocí [carchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) nebo [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) k určení, zda je archiv načítání nebo ukládání.

`Serialize`je volána [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) a [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Tyto funkce jsou `CArchive` spojeny s ** < **operátorem vložení **>>**( ) a operátorem extrakce ( ).

Příklady serializace naleznete v článku [Serializace: Serializace objektu](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy `CObject` používané ve všech příkladech.

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)
